# ISPH Leadership Survey Data Analysis

This repository contains a Jupyter Notebook (`isph_leadership_survey.ipynb`) that performs a comprehensive analysis of the ISPH Leadership Survey data, along with the anonymized survey data (`obfusicated_data.csv`).

## Files

### 1. `isph_leadership_survey.ipynb`

This Jupyter Notebook contains the Python code used to analyze the survey data. It includes the following sections:

**1. Import Libraries:** Imports necessary Python libraries (pandas, numpy, matplotlib, seaborn, os, re, openpyxl).

**2. Load and Inspect Data:** Loads the survey data from `obfusicated_data.csv` and performs initial data inspection (shape, head). The file `survey_data.csv` is expected to be in the same directory.

- Loads data using `pandas.read_csv('survey_data.csv')`.
- Prints the shape of the DataFrame.
- Displays the first few rows using `data.head()`.

**3. Year Group Analysis:** Analyzes the distribution of students across different year groups.

- Counts the number of students in each year group.
- Creates a bar plot visualization.
- Prints the year group counts.

**4. Response Analysis by Year Group:** Calculates and exports the percentage of responses for each question, grouped by year group. The results are stored in the `csv_year` directory.

- Iterates through each question and year group.
- Calculates the percentage of each response (Strongly Disagree, Disagree, Agree, Strongly Agree).
- Exports the results to individual CSV files (e.g., `csv_year/Q1_percentage.csv`).

**5. Response Analysis by Nationality:** Calculates and exports the percentage of responses for each question, grouped by nationality. The results are stored in the `csv_nationality` directory.

- Iterates through each question and nationality.
- Calculates the percentage of each response.
- Exports the results to individual CSV files (e.g., `csv_nationality/Q1_percentage.csv`).

**6. Response Analysis by Gender:** Calculates and exports the percentage of responses for each question, grouped by gender. The results are stored in the `csv_gender` directory.

- Iterates through each question and gender.
- Calculates the percentage of each response.
- Exports the results to individual CSV files (e.g., `csv_gender/Q1_percentage.csv`).

**7. Overall Response Analysis:** Calculates the overall percentage of responses for each question, combining data from all year groups, nationalities, and genders. The results are exported to `percentage_all.xlsx`.

- Calculates the overall percentage of each response.
- Exports the results to an Excel file (`percentage_all.xlsx`).

**8. Data Aggregation:** Aggregates the year group, nationality, and gender data into a single file for each question. A total statistics row is also added. Results are stored in `all_data_csv` (CSV files) and `all_data_xls` (Excel files).

- Reads data from the individual CSV files generated in previous steps.
- Concatenates the dataframes for gender, nationality, and year group.
- Adds a "Total Stats" row with the overall response percentages.
- Exports the combined data to both CSV and Excel formats.

**9. Excel Formatting and Merging:** Formats the individual Excel files by adding the question text as the first row and merging the first few columns. It then merges all individual Excel files into a single comprehensive Excel file, with each question's data on a separate sheet (`merged_questions.xlsx`).

- Adds the question text as the first row in each Excel file.
- Merges the first few columns for better readability.
- Merges all individual Excel files into a single Excel file, with each question on a separate sheet.

### 2. `obfusicated_data.csv`

This file contains the anonymized survey data in CSV format. It includes the following columns:

- `Timestamp`: Date and time of the survey submission.
- `Please select your Year Group`: The year group of the student (e.g., Year 7, Year 8).
- `Please choose your Nationality`: The nationality of the student.
- `Please select your gender`: The gender of the student.
- `1-56`: Responses to the 56 survey questions, with values 1-4 representing Strongly Disagree, Disagree, Agree, and Strongly Agree, respectively.

## Usage

To run the analysis:

1.  **Clone the repository:**

    ```bash
    git clone <repository_url>
    cd quangngonz-isph_survey_data_analysis
    ```

2.  **Install the required Python libraries:**

    ```bash
    pip install pandas numpy matplotlib seaborn openpyxl
    ```

3.  **Rename the data file:**

    ```bash
    mv obfusicated_data.csv survey_data.csv
    ```

4.  **Run the Jupyter Notebook:**

    ```bash
    jupyter notebook isph_leadership_survey.ipynb
    ```

    or

    ```bash
    python isph_leadership_survey.ipynb
    ```

5.  **Execute the cells in the notebook sequentially.** The notebook will generate various CSV and Excel files in the created directories (`csv_year`, `csv_nationality`, `csv_gender`, `all_data_csv`, `all_data_xls`), as well as `percentage_all.xlsx` and `merged_questions.xlsx`.

## Output

The analysis generates the following output files:

- **CSV Files (Year Group, Nationality, Gender):** `csv_year/Q{i+1}_percentage.csv`, `csv_nationality/Q{i+1}_percentage.csv`, `csv_gender/Q{i+1}_percentage.csv` contain the percentage of responses for each question, grouped by year group, nationality and gender respectively.

- **Excel File (Overall):** `percentage_all.xlsx` contains the overall percentage of responses for each question.

- **Aggregated CSV and Excel Files:** `all_data_csv/Q{i+1}_percentage.csv` and `all_data_xls/Q{i+1}_percentage.xlsx` contain the aggregated year group, nationality, and gender data for each question, including total statistics.

- **Merged Excel File:** `merged_questions.xlsx` is a single Excel file containing all questions and their corresponding data on separate sheets. This file is formatted for easy readability.

## Notes

- The provided CSV file (`obfusicated_data.csv`) is assumed to be in the same directory as the Jupyter Notebook. The notebook attempts to load this file as `survey_data.csv`, so you may need to rename it.
- The code creates several directories (`csv_year`, `csv_nationality`, `csv_gender`, `all_data_csv`, `all_data_xls`) to store the output files.
- The code includes a hardcoded fix for the 'Year 8' count. This indicates a potential issue with the original data that should be addressed before analysis.
- The analysis relies on specific column names in the CSV file (e.g., "Year Group", "Nationality", "Gender"). Ensure that these column names are consistent in your data.
- The code assumes that the response values in the CSV file are integers from 1 to 4, representing the response options "Strongly Disagree", "Disagree", "Agree", and "Strongly Agree".
