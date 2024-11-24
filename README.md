# User Journey Analysis Project

## Overview
This project aims to analyze user journeys on a website to understand user behavior and improve user experience. The project includes preprocessing raw user journey data and performing various analyses to extract meaningful insights.

## Project Structure
```
.
├── **pycache**/
├── .gitignore
├── analyzing_data.ipynb
├── processed_user_journeys.csv
├── README.md
├── solution-files/
│   ├── User_journey_analysis.ipynb
│   ├── User_journey_preprocessing.ipynb
├── user_journey_raw.csv
├── videos/
│   ├── instruction.mp4
│   ├── solution.mp4
```

## Notebooks

### User_journey_preprocessing.ipynb
This notebook preprocesses the raw user journey data. It includes functions to group data, remove specific pages, and remove consecutive duplicate pages.

#### Functions

##### `group_by(data, group_column='user_id', target_column='user_journey', sessions='all', count_from='last')`
Groups the data by the specified column and concatenates user journey strings.
- **Parameters:**
  - `data`: DataFrame containing the data to be grouped
  - `group_column`: Column to group by (default: 'user_id')
  - `target_column`: Column to concatenate (default: 'user_journey')
  - `sessions`: Number of sessions to aggregate (default: 'all')
  - `count_from`: Whether to count from 'last' or 'first' (default: 'last')
- **Returns:** A new DataFrame with grouped data

##### `remove_pages(data, pages=[], target_column='user_journey')`
Removes specified pages from user journey strings.
- **Parameters:**
  - `data`: DataFrame containing the user journeys data
  - `pages`: List or set of pages to remove (default: [])
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
- **Returns:** A new DataFrame with specified pages removed

##### `remove_page_duplicates(data, target_column='user_journey')`
Removes consecutive duplicate pages from user journey strings.
- **Parameters:**
  - `data`: DataFrame containing the user journeys data
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
- **Returns:** A new DataFrame with consecutive duplicates removed

### User_journey_analysis.ipynb
This notebook analyzes the preprocessed user journey data. It includes functions to count page occurrences, find page presences, and identify page sequences.

#### Functions

##### `make_mask(data, match, target_column)`
Creates a boolean mask indicating where match is found in target_column.
- **Parameters:**
  - `data`: DataFrame to create the mask for
  - `match`: String to match in target_column
  - `target_column`: Column to search for the match
- **Returns:** A boolean list (mask)

##### `split_pages(data, target_column='user_journey')`
Splits user journey strings into separate pages.
- **Parameters:**
  - `data`: DataFrame containing user journeys data
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
- **Returns:** A numpy array of arrays of pages

##### `get_pages_set(data, target_column='user_journey')`
Obtains the set of all unique pages in the data.
- **Parameters:**
  - `data`: DataFrame containing user journeys data
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
- **Returns:** A set of unique pages

##### `page_count(data, target_column='user_journey', plan='All', mask=None, sort=True)`
Counts the number of times each page appears in user journey strings.
- **Parameters:**
  - `data`: DataFrame containing user journeys data
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
  - `plan`: Subscription plan to filter by (default: 'All')
  - `mask`: Boolean list to filter data (default: None)
  - `sort`: Whether to sort the results (default: True)
- **Returns:** A dictionary of page counts

##### `page_presence(data, target_column='user_journey', plan='All', mask=None, sort=True)`
Finds the number of journeys each page is present in.
- **Parameters:**
  - `data`: DataFrame containing user journeys data
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
  - `plan`: Subscription plan to filter by (default: 'All')
  - `mask`: Boolean list to filter data (default: None)
  - `sort`: Whether to sort the results (default: True)
- **Returns:** A dictionary of page presences

##### `page_destinations(data, target_column='user_journey', plan='All', mask=None, sort=True)`
Finds all follow-up pages for each page and their counts.
- **Parameters:**
  - `data`: DataFrame containing user journeys data
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
  - `plan`: Subscription plan to filter by (default: 'All')
  - `mask`: Boolean list to filter data (default: None)
  - `sort`: Whether to sort the results (default: True)
- **Returns:** A dictionary of follow-up pages and their counts

##### `page_sequences(data, number_of_pages=3, show_results=10, target_column='user_journey', plan='All', mask=None, sort=True)`
Finds the top consecutive page sequences and their counts.
- **Parameters:**
  - `data`: DataFrame containing user journeys data
  - `number_of_pages`: Number of consecutive pages to include in each sequence (default: 3)
  - `show_results`: Number of results to return (default: 10)
  - `target_column`: Column containing the user journey strings (default: 'user_journey')
  - `plan`: Subscription plan to filter by (default: 'All')
  - `mask`: Boolean list to filter data (default: None)
  - `sort`: Whether to sort the results (default: True)
- **Returns:** A dictionary of page sequences and their counts

## Data Files
- `user_journey_raw.csv`: Raw user journey data
- `processed_user_journeys.csv`: Preprocessed user journey data

## Videos
- **Instruction Video**: Available at `videos/instruction.mp4`
- **Solution Video**: Available at `videos/solution.mp4`

## How to Use
1. Preprocess the raw data using `User_journey_preprocessing.ipynb`
2. Analyze the preprocessed data using `User_journey_analysis.ipynb`
3. Refer to the provided functions for specific analyses and insights

## Requirements
- Python 3.9.7
- pandas
- numpy
- warnings