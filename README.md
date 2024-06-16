# During my internship at Cognizant, I worked on a significant project
# BillManagement Module

Overview
The BillManagement module provides features for both ride providers and ride seekers, including bill generation, viewing, and report generation. This module handles various operations related to billing within a ride-sharing application.

* Features
Bill Generation: Ride providers can request bill generation based on TripId.
Bill Viewing: Ride seekers can view bills based on RideId or BillId.
Report Generation: Provides data for generating reports for ride providers.
Database Schema
Tables

* FEES
feeId (int): Primary Key
carType (varchar)
carName (varchar)
fuelType (varchar)
averageInKm (int)
costOfFuel (int)
wearTearCost (int)
driverCharges (int)
carpoolCommission (int)

* BILLMASTER
billId (varchar): Primary Key
rideId (varchar)
NoOfKm (int)
totalBill (int)
NoOfOccupants (int)
FeeId (int): Foreign Key referencing FEES
CostPerOccupant (int)

* Relationships
FEES and BILLMASTER have a one-to-many relationship.

* Endpoints

  
Generate New Bill
URL: /api/bill/new
Method: POST
Role: RideSeeker
Inputs: BillRequestDTO
Outputs: Status code and BillId

Get Bill by ID
URL: /api/bill/{billId}
Method: GET
Role: RideSeeker
Inputs: billId
Outputs: BillResponseDTO

Get Monthly Billing Report
URL: /api/bill/{month}/{driverId}
Method: GET
Role: RideProvider
Inputs: month, driverId
Outputs: List of BillResponseDTO
