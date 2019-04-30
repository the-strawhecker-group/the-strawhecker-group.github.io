# AIM API

## Welcome to the AIM api by the Strawhecker Group!

### Introduction
    The AIM API reports on payment processing stats

### Api Token Access
    TODO

# Aggregation

Abstract aggregation operation.
    

<details><summary>Items</summary>

## None



## 3 Month Moving Average

Periods = 3, Frequency = Month
    

</details>

# Attributes

Attribute base class.
Metrics are columns of interest (Ex. Volume, Net Revenue, Processing Cost) that are co-tabulated with
attribute columns (Ex. Date, Card, Region) that are used to filter or group the metric.

<details><summary>Items</summary>

## Card

**Card** is an attribute of central importance in the AIM system.

There are 5 basic card types:
- credit
- signature_debit aka *sig_debit*
- pin_debit
- opt_blue

And 2 non-basic card types:
- bank_cards (credit + sig_debit)
- other_cards

The metrics coming from raw processor data which are reported on individual
card types may be filtered and grouped by card types and are referred to as
"card metrics" as opposed to "non-card metrics".

## Average Ticket Tier

A merchant's ticket tier is based on its **average** number of transactions (or "tickets")
over a rolling 12 month period.

## Annual Volume Tier

A merchant's volume tier is based on its **total** volume over a rolling 12 month period.
    

## Transaction Tier

A merchant's transaction tier is based on its **total** number of transactions (or "tickets")
over a rolling 12 month period.

## Region

Geographic region of the transaction.
Canada is a region.

## State

U.S. State of the transaction

## ZIP

Zip code of the transaction

## MSA

City of the transaction

## Sales Model

Sales model code

## Industry Classification Type

Industry Classification Type. Currently this is either MCC or SIC.
    

## Industry Group

Hierarchical grouping of Industries
    

## Industry

Industry the merchant belongs to.
    

## Portfolio

A grouping of merchants within an organization.
    

## Data Month

Date is one of the AIM required attributes.
Traditionally date has been by month due to month being the frequency of the aim
application, though other aggregation levels are possible and may show up in the
future. The term era is used to denote a chunk of time. Ex. The month of June, as
opposed to June 1.

## Standalone Merchants

Binary on if the merchant is part of a chain or not.

## Vintage

Year merchant entered the market

</details>

# Metrics

Base metric class.
    

<details><summary>Items</summary>

## COS Total Processing Fees

Processing Cost
Contains card components only

## Total Cost of Sales

Total Cost
:= Total Cost Card + Total Cost Noncard

## Gross Revenue

Gross Revenue
:= Gross Revenue Card + Gross Revenue Noncard
Contains card and noncard components

## Gross Processing Revenue

Gross Processing Revenue
Contains card components only

## Net Revenue

Net Revenue
:= Net Revenue Card + Net Revenue Noncard
Contains card and noncard components

## Net Processing Revenue

Net Processing Revenue
Contains card components only

## COS Association Fees, Assessments, and SWITCH Fees

Association And Switch Fees Cost
No card components

## COS Association Fees & Assessments

Association Fees Cost

## COS SWITCH Fees

Switch Fees Cost

## COS Interchange Fees

Interchange Fees Cost
No card components

## COS Other Processing Fees

Other Fees Cost
No card components

## Other COS

Other Cost
No card components

## Residuals Paid

Residuals Cost
No card components

## Legacy Account Annual Fees Revenue

Legacy Account Annual Fees Revenue
No card components

## Monthly Legacy Account Fees

Legacy Account Monthly Fees Revenue
No card components

## Discount Revenue

Discount  Revenue
Contains card components only

## Equipment & Other Income

Equipment and Other Revenue
Contains card components only

## Gross Profit

Gross Profit Revenue
Contains card components only

## Legacy Account Annual and Monthly Fees Revenue

Legacy Account Annual and Monthly Fees Revenue
Contains card components only

## Other Fee Revenue

Other Fees Revenue
No card components

## PCI Annual And Monthly Fees Revenue

PCI Annual And Monthly Fees Revenue
No card components

## Transaction Fee Revenue

Transaction Fees Revenue
No card components

## Transactions

Transaction
Contains card components only

## Volume

Volume
Contains card components only

</details>

# Normalization

Abstract Metric Normalizer.
AIM normalizations are of the form: **sum(metric)/sum(normalizing_metric)** .
There are three columns used in AIM normalization (with corresponding units):

- Volume ($)
- Transactions (-)
- Active Merchants (-)

Where "-" is a null unit.

Unit Matrix:

===================  ======  ============  ================
Metric / Normalizer  Volume  Transactions  Active Merchants
===================  ======  ============  ================
Transactions           -          -               -
Volume                 -          $               $
All Other Metrics      -          $               $
===================  ======  ============  ================

<details><summary>Items</summary>

## Per Merchant

Active Merchants
In order to be considered active a merchant has to have non-zero Volume and
Net Revenue > 0.
Unitless due to being a count.

## Per Transaction

Transactions - Unitless due to being a count.
    

## Per Volume

Volume - Units in dollars.

</details>

