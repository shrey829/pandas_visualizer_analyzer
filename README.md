==============================================================================
                          SALES DATA ANALYZER
==============================================================================

Author  : Shrey
File    : sales_data_analyzer.py
Type    : Menu-driven command-line program (Python)


------------------------------------------------------------------------------
TABLE OF CONTENTS
------------------------------------------------------------------------------

  1.  Overview
  2.  Features at a Glance
  3.  Requirements
  4.  Installation
  5.  How to Run
  6.  Preparing Your CSV File
  7.  Detailed Guide to Every Menu Option
        Option 1 - Load Data
        Option 2 - Explore Data
        Option 3 - Perform DataFrame Operations
        Option 4 - Handle Missing Values
        Option 5 - Generate Descriptive Info
        Option 6 - Data Visualization
        Option 7 - Save Visualization
        Option 8 - Exit
  8.  Example Session
  9.  Error Handling
 10.  Known Limitations
 11.  Troubleshooting
 12.  Project Structure
 13.  Author


==============================================================================
1. OVERVIEW
==============================================================================

Sales Data Analyzer is a console program that lets you work with sales data
stored in a CSV file without writing any code. You choose actions from a
numbered menu, type the answers to the prompts, and the program shows the
results on screen.

With it you can:

  - load a CSV file into memory
  - look at the data (first rows, last rows, columns, data types, statistics)
  - clean the data (find, fill, drop or replace missing values)
  - slice, search, sort, filter, split, combine and aggregate the data
  - calculate sum, mean, median, mode, standard deviation and variance
  - draw charts with Matplotlib and Seaborn
  - save those charts as image files

The program is built with a single class, SalesDataAnalyzer, and uses the
pandas, NumPy, Matplotlib and Seaborn libraries.


==============================================================================
2. FEATURES AT A GLANCE
==============================================================================

  Menu   Feature
  ----   ---------------------------------------------------------------
   1     Load data from a CSV file
   2     Explore data (head, tail, columns, data types, info, statistics)
   3     DataFrame operations (convert, index, slice, math, combine,
         split, search, sort, filter, aggregate)
   4     Handle missing values (show, fill with mean, drop, replace)
   5     Descriptive statistics (mean, median, mode, std, var, quartiles)
   6     Data visualization (Matplotlib and Seaborn)
   7     Save a visualization to an image file
   8     Exit


==============================================================================
3. REQUIREMENTS
==============================================================================

  - Python 3.10 or newer
      The main menu uses the "match" statement, which was introduced in
      Python 3.10. Older versions will stop with a SyntaxError.

  - These Python libraries:
      pandas
      numpy
      matplotlib
      seaborn

  - A CSV file containing your sales data.


==============================================================================
4. INSTALLATION
==============================================================================

Step 1. Install Python 3.10 or newer from https://www.python.org
        (tick "Add Python to PATH" during installation on Windows).

Step 2. Check your Python version:

            python --version

        (On some systems the command is "python3 --version".)

Step 3. Install the required libraries:

            pip install pandas numpy matplotlib seaborn

Step 4. Put sales_data_analyzer.py and your CSV file in a folder you can
        easily find.


==============================================================================
5. HOW TO RUN
==============================================================================

Open a terminal or command prompt, go to the folder that contains the
program, and run:

            python sales_data_analyzer.py

(Use "python3" instead of "python" if that is what your system requires.)

The program prints the main menu once at the start:

            enter your choices
            1.load data
            2.explore data
            3.perform dataframe operations
            4.handling missing values
            5.generate descriptive info
            6.data visualization
            7.save visualization
            8.exit
            please choose your choice

and then keeps asking "enter the choice" until you type 8.

IMPORTANT: Always start with option 1 and load a CSV file. Most other
options will not work until data has been loaded.


==============================================================================
6. PREPARING YOUR CSV FILE
==============================================================================

The program works with any CSV file that has a header row. A typical sales
file looks like this:

            id,region,product,sales
            1,North,A,100
            2,South,B,150
            3,East,A,120
            4,West,B,170
            5,North,B,90

Tips:

  - The first row must contain the column names.
  - Column names are case-sensitive. "Sales" and "sales" are different.
  - If you plan to use Combine, Join or Merge (option 3), both files need a
    column named exactly "id".
  - For the Pie chart and Stack plot, the y column must be numeric.
  - You can give the file path in full (for example C:\data\sales.csv or
    /home/user/sales.csv) or just the file name if the CSV is in the same
    folder from which you run the program.


==============================================================================
7. DETAILED GUIDE TO EVERY MENU OPTION
==============================================================================

Each time you pick an option, the program performs ONE action and then
returns to the main menu. Choose the option again for another action.


------------------------------------------------------------------------------
OPTION 1 - LOAD DATA
------------------------------------------------------------------------------

What it does:
    Reads a CSV file into memory so the other options can use it.

What you enter:
    The path of the CSV file.

Example:
    enter the choice1
    Give me the CSV file path
    sales.csv
    Data loaded successfully

Notes:
    - If the file is not found or cannot be read, the program shows
      "Error is: ..." and returns to the menu.
    - Loading a new file replaces the data that was loaded before.


------------------------------------------------------------------------------
OPTION 2 - EXPLORE DATA
------------------------------------------------------------------------------

What it does:
    Lets you look at the loaded data in different ways.

Sub-menu:
    1. Display first 5 rows
    2. Display last 5 rows
    3. Display column names
    4. Display data types
    5. Display basic info and statistics
    6. Exit

What each choice shows:
    1  The first five rows of the data.
    2  The last five rows of the data.
    3  The list of column names.
    4  The data type of every column (for example int64, float64, object).
    5  Row/column counts, non-null counts and memory use, followed by
       count, mean, std, min, quartiles and max for numeric columns.
    6  Closes the whole program.

Notes:
    - Shows "Your DataFrame is empty" if no data has been loaded.


------------------------------------------------------------------------------
OPTION 3 - PERFORM DATAFRAME OPERATIONS
------------------------------------------------------------------------------

This option has a first-level menu with three groups:

    1.convert_index_slicing
    2.mathematical_combine_split
    3.search_sort_filter

Choose a group, then choose the operation inside it.


GROUP 1 - CONVERT / INDEX / SLICE
.................................

    1. Convert
         Asks for a column name and converts that column into a NumPy
         array, then prints the array.

    2. Index
         Asks for a column name, converts it to an array, prints it, then
         asks for an index number and prints the element at that position.
         (The first element is index 0.)

    3. Slice
         Asks for a column name first, then shows three slicing choices:

           1. Slicing whole dataframe
                Enter row start, row end, column start and column end.
                The program prints that block of the table (positions,
                not names; the end position is not included).

           2. Slicing specific column
                Enter a start and an end position. The program prints that
                part of the column you selected.

           3. Slicing specific row
                Enter a row index. The program prints that row, then asks
                for a start and end position and prints that part of the
                row.

    Example (Slice > column):
         column name : sales
         start       : 0
         end         : 3
         result      : the first three sales values


GROUP 2 - MATHEMATICAL / COMBINE / SPLIT
........................................

    1. Mathematical operation
         Asks for a column name first, then shows:
           1. sum
           2. mean
           3. median
           4. mode
           5. exit (listed in the menu; it only returns to the main menu
              with an "INVALID CHOICE" message)
         The result is printed for the column you chose.
         Sum and mean need a numeric column.

    2. Combine operations
         Asks for the path of a SECOND CSV file, then shows:
           1. concatination of dataframes
                Stacks the second file's rows below the loaded data.
           2. join of dataframes
                Joins the two tables on the "id" column (inner join).
           3. merge of dataframes
                Merges the two tables on the "id" column (inner merge).
         The combined table is printed on screen. The loaded data itself
         is not changed.
         For join and merge, both files must contain an "id" column. Join
         also fails if the two files share any other column name; use
         merge in that case.

    3. Split operations
         Shows:
           1. split dataframe based on regions
           2. split dataframe based on products
           4. split dataframe based on your choice of criteria
         (There is no choice 3.)
         After choosing, enter the name of the column to split by. The
         program prints one separate table for every unique value in that
         column (for example one table per region).


GROUP 3 - SEARCH / SORT / FILTER / AGGREGATE
............................................

    1. Search
         1. search by column value
              Enter a column name and a value; rows that match exactly
              are printed.
         2. search by row index
              Enter a row index; that row is printed.

    2. Sort
         1. sort by column value
              Enter a column name; the table is printed sorted by that
              column in ascending order.
         2. sort by row index
              Prints the table sorted by its index.

    3. Filter
         1. filter by column value
              Enter a column name and a value; only matching rows are
              printed.
         2. filter by row index
              Enter a row index; that row is printed.

    4. Aggregate
         Enter the column to group by (for example region), then choose:
           1. sum
           2. mean
           3. median
           4. mode
           5. exit (closes the whole program)
         The result is shown for every group. Sum, mean and median use
         numeric columns only.

    Notes for search and filter:
         The value you type is compared as text, so it works for both text
         columns (North) and number columns (100).


------------------------------------------------------------------------------
OPTION 4 - HANDLE MISSING VALUES
------------------------------------------------------------------------------

Sub-menu:
    1. Display rows with missing values
    2. Fill missing values with mean
    3. Drop rows with missing values
    4. Replace missing values with a specific value
    5. Exit

What each choice does:
    1  Prints only the rows that contain at least one empty cell.
    2  Replaces empty cells in numeric columns with that column's mean.
    3  Removes every row that contains an empty cell.
    4  Asks for a value and replaces empty cells with it.
         - Numeric columns are filled only if the value you type is a
           number (for example 0).
         - Text columns are filled with whatever you type.
    5  Closes the whole program.

Notes:
    - Changes are made to the data in memory, so every later option uses
      the cleaned data.
    - The CSV file on disk is NOT changed, and the program has no option
      to export the cleaned data.


------------------------------------------------------------------------------
OPTION 5 - GENERATE DESCRIPTIVE INFO
------------------------------------------------------------------------------

What it does:
    Prints a statistics summary for one column, grouped by another column.

What you enter:
    1. The column to group by (for example region).
    2. The numeric column to analyse (for example sales).

What it prints:
    - mean, median, mode, standard deviation and variance of the numeric
      column for each group
    - the 25th and 75th percentiles (quartiles) of the numeric column
    - the full describe() table of the data
    - the info() summary of the data


------------------------------------------------------------------------------
OPTION 6 - DATA VISUALIZATION
------------------------------------------------------------------------------

The program shows:

    using matplotlib options are:-[bar plot,line plot,histogram,
                                   scatter plot,stack plot,pie chart]
    using seaborn options are:-[heatmap,boxplot,countplot]
    1.matplotlib,2.Seaborn

Type 1 for Matplotlib or 2 for Seaborn.

MATPLOTLIB CHARTS
.................

    1. line plot       Enter x column and y column.
    2. bar plot        Enter x column and y column.
    3. scatter plot    Enter x column and y column.
    4. histogram       Enter one column (10 bins).
    6. pie chart       Enter label column (x) and numeric value column (y).
    7. stack plots     Enter x column and numeric y column.
    8. subplots        Enter x and y columns for plot 1, then x and y
                       columns for plot 2. Two line plots are drawn, one
                       above the other.
    (There is no choice 5.)

SEABORN CHARTS
..............

    1. heatmap         Enter two columns. The program counts how often the
                       two columns occur together and shows the
                       correlation of that count table as a heatmap.
    2. boxplot         Enter x column (category) and y column (numeric).
    3. countplot       Enter one column; shows how many times each value
                       appears.

Notes:
    - A chart window opens on screen. Close the window to return to the
      menu.
    - If you type a column name that does not exist, the program prints
      the error and returns to the menu.


------------------------------------------------------------------------------
OPTION 7 - SAVE VISUALIZATION
------------------------------------------------------------------------------

What it does:
    Draws a chart exactly like option 6 and also saves it as an image file.

Steps:
    1. Enter the file path to save to, for example:
           sales_chart.png
           charts/sales_chart.png
           C:\Users\Shrey\Desktop\sales_chart.png
       - Quotes around the path (as added by Windows "Copy as path") are
         accepted.
       - If the folder does not exist, it is created automatically.
       - The file name should end with .png (other formats supported by
         Matplotlib, such as .jpg, .pdf and .svg, also work).
    2. Choose 1 (Matplotlib) or 2 (Seaborn).
    3. Choose the chart and enter the column names, as in option 6.

The chart is saved first and then displayed. The message
"Plot saved successfully!" confirms that the file was written.


------------------------------------------------------------------------------
OPTION 8 - EXIT
------------------------------------------------------------------------------

Prints "exiting the program" and closes the program.


==============================================================================
8. EXAMPLE SESSION
==============================================================================

Using the sample sales.csv from section 6:

    enter the choice1
    Give me the CSV file path
    sales.csv
    Data loaded successfully

    enter the choice2
    ... (explore menu) ...
    Enter your choice: 1
       id region product  sales
    0   1  North       A    100
    1   2  South       B    150
    2   3   East       A    120
    3   4   West       B    170
    4   5  North       B     90

    enter the choice3
    1.convert_index_slicing
    2.mathematical_combine_split
    3.search_sort_filter
    3
    1.search
    2.sort
    3.filter
    4.aggregate
    enter the choice4
    give us the columns name for the aggregation columns in your dataframe
    region
    ... (choose 1 for sum) ...
            id  sales
    region
    East     3    120
    North    6    190
    South    2    150
    West     4    170

    enter the choice7
    enter the file path
    charts/sales_by_region.png
    1.matplotlib visuals
    2.seaborn visuals
    2
    it should end with .png
    1.heatmap
    2.boxplot
    3.countplot
    3
    countplot
    give me the columns name for the x axis in your dataframe
    region
    Plot saved successfully!

    enter the choice8
    exiting the program

(The exact table layout on your screen depends on your data.)


==============================================================================
9. ERROR HANDLING
==============================================================================

The main loop catches common mistakes so the program does not close
unexpectedly. When one of these happens, the program prints a message such
as:

    Error is: <description>

and returns to the main menu. Typical causes:

  - "Your DataFrame is empty"
        No data was loaded. Use option 1 first.

  - KeyError (for example 'Sales')
        The column name does not exist or is typed with different
        capital letters. Check the spelling with Explore > Display column
        names.

  - ValueError (invalid literal for int())
        You typed text where a number was expected (for example in a menu
        choice or an index).

  - IndexError (index out of bounds)
        The index or row number is bigger than the data.

  - FileNotFoundError
        The file path is wrong.

  - TypeError
        The column is not suitable for the chosen operation (for example
        sum of a text column).

If you type a menu number that does not exist, the program prints
"invalid choice" and asks again.


==============================================================================
10. KNOWN LIMITATIONS
==============================================================================

  - Results of Combine, Join, Merge and Split are only printed. They do not
    replace the loaded data.
  - Cleaned data (option 4) is not written back to a file.
  - Menu choices 6 (Explore), 5 (Missing values) and 5 (Aggregate), each
    labelled "Exit", close the whole program, not just that sub-menu.
  - The Mathematical operations menu lists "5.exit", but choosing it only
    prints "INVALID CHOICE" and returns to the main menu.
  - Matplotlib menu has no choice 5, and the Split menu has no choice 3.
  - Search and filter by row index give the same result.
  - The main menu is printed only once, at program start. Use the list in
    section 5 as a reminder.
  - Python 3.10 or newer is required.


==============================================================================
11. TROUBLESHOOTING
==============================================================================

Problem : ModuleNotFoundError: No module named 'pandas' (or numpy,
          matplotlib, seaborn)
Fix     : Install the libraries:
              pip install pandas numpy matplotlib seaborn

Problem : SyntaxError pointing at "match choice:"
Fix     : Your Python is older than 3.10. Install a newer Python.

Problem : "python" is not recognized as a command
Fix     : Reinstall Python and tick "Add Python to PATH", or try "python3"
          or "py" instead.

Problem : Error is: [Errno 2] No such file or directory (when loading)
Fix     : Check the CSV file path. Use the full path, or run the program
          from the folder where the CSV is stored.

Problem : Chart window does not appear (for example on a server or in a
          remote terminal)
Fix     : The computer has no display. Use option 7 to save the chart to
          an image file and open that file instead.

Problem : Join fails with "columns overlap but no suffix specified"
Fix     : The two files have columns with the same name besides "id". Use
          Merge instead of Join.

Problem : Pie chart or stack plot fails
Fix     : Make sure the y column contains numbers only.

Problem : Search or filter returns nothing
Fix     : The value must match exactly, including capital letters
          (North is not the same as north).


==============================================================================
12. PROJECT STRUCTURE
==============================================================================

    sales_data_analyzer/
    |-- sales_data_analyzer.py    main program
    |-- README.txt                this file
    |-- sales.csv                 your data file (example name)


==============================================================================
13. AUTHOR
==============================================================================

    Shrey

==============================================================================
                                END OF FILE
==============================================================================
