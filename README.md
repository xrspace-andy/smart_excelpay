# Cycling Data Processor

## Description
This script reads a text file containing cycling data, processes it, and outputs a structured CSV file. It organizes the data with dates as row indices and participant IDs as columns. A final row is added to calculate the total values for each participant.

## Requirements
- Python 3.x
- pandas library
- flask library

## Installation
1. Ensure you have Python installed.
2. Install the required library if not already installed:
   ```sh
   pip install pandas flask
   ```

## Usage
1. Prepare a text file for the round (`cycling_data_round<N>.txt`, e.g. `cycling_data_round9.txt`) with data in the following format:
   ```
   YYYY_MM_DD,Name1/Name2/Name3,Value
   ```
   Example:
   ```
   2025_01_21,Arthur/Bossun/JJ/Rex/Chaihung,245
   ```
2. Run the script with the round number to process:
   ```sh
   python to_csv.py <round>
   ```
   Example, for round 9:
   ```sh
   python to_csv.py 9
   ```
3. The processed data will be saved in `cycling_data_round<N>.csv` (e.g. `cycling_data_round9.csv`). The CSV files are generated output and are not committed.
4. Run the script for service with the round number to serve (this also regenerates the CSV of that round):
   ```sh
   python service.py <round>
   ```
   Example, for round 9:
   ```sh
   python service.py 9
   ```

Both scripts need the round number; run them with `-h` to see the usage, and an unknown round (no matching `cycling_data_round<N>.txt`) exits with an error.
5. copy URL to query personal data:
   #### Example:
   - enter URL
   ```
   http://192.168.10.59:9487/query?ID=JJ
   ```
   - output on webpage:
   ```
   {"2025_01_21":245,"total":245}
   ```

## Output
- The CSV file will contain:
  - Dates as row indices
  - Participants as column headers
  - A final row labeled `Total` summing up the values for each participant

## Example Output CSV:
```
Date,Arthur,Bossun,JJ,Rex,Chaihung
2025_01_21,245,245,245,245,245
Total,245,245,245,245,245
```

## Notes
- Ensure the text file follows the specified format.
- Modify the script to handle different data structures if needed.

