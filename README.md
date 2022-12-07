# DS241-Portfolio

Portfolio for Clarkson Fall 2022 DS 241

The following is a general description of each of the files in this portfolio along with what data they rely on and what skills they address.
All data files relied on are found in the _data\_raw_ directory.

## Exploratory Analysis Using Airline Data

Each of the files in this section only include exploratory data analysis and data cleaning/preparation; no modeling is done and no evidence is generated beyond simple visualizations to support any conclusions. However, at several moments general observations are made from the resulting visualizations.

1. __NYC Flights:__
This was the first analysis we did in this class. It shows basics such as:
    * loading R packages
    * manipulating data with `dplyr::filter`
    * making bar plots with `ggplot`, including `facet_wrap`
    * constructing lists and using the `%in%` operator
2. __BOT:__ _(Relies on BOT.zip)_
This file builds on the NYC Flights analysis by taking data from the U.S. Bureau of Transportation. In addition to the skills from #1, it shows the following:
    * reading data from a .csv file, with help from the here and janitor packages
    * use of the `weight` field in `ggplot2::geom_bar` to count from a data column rather than number of rows
    * use of additional `dplyr` functions such as `mutate`, `select`, `group_by`, and `summarise`
    * plotting `geom_histogram` and `geom_line` with `ggplot2`
3. __Flights Over Year:__ _(Relies on all files in airline\_data)_
This file builds on the Bureau of Transportation analysis, specifically examining the departures from La Guardia Airport. In addition to the skills from #2, it shows the following:
    * making more visually appealing plots with `ggplot2` by adding titles and axis labels
    * use of the `rbind` function to combine rows from different dataframes (in this case, needed to combine data across years)

For the rest of the portfolio, the main five `dplyr` functions - `filter`, `mutate`, `select`, `group_by`, and `summarise` - are used fluently when needed.

## Modeling Using Student Enrollment Data

4. __MA 132 Enrollment:__ _(Relies on clarkson\_math\_enrollment.csv)_
This file uses enrollment data from the Clarkson University mathematics department to build a model to predict enrollment in MA 132 (Calculus II) in the Spring 2022 semester. It demonstrates the following skills:
    * Basic R Skills
        * use of `dplyr::distinct` function
        * use of `startsWith`, `substr`, `strtoi`, and `nchar` to work with strings
        * use of `cbind` to join dataframes
        * plotting `geom_point` with `ggplot2` and using `geom_smooth(method = lm)` to draw a regression line over it
        * use of `lm` for linear and multiple regression
    * Data Science Process
        * Generating a model based on understanding of enrollment patterns (e.g., many Calculus I students in the fall will enroll in Calculus II in the spring).
        * Revising this model to include additional real-world influences and determine a better fit for the data.

## Beginnings of Spatial Data Analysis

The following files demonstrate some spatial analysis - I say "beginnings" because we didn't necessarily work with spatial data in an authentic way (see the next section), but we still made spatial considerations.

5. __Denny's / La Quinta Lab 4:__ _(Relies on states.csv)_
This file demonstrates many of the same skills as in the first section (data cleaning, exploratory analysis).
    * One important skill to note is the use of the `case_when` function combined with `dplyr::mutate`.
6. __Denny's / La Quinta Lab 5:__ _(Relies on FastFoodRestaurants.csv)_
This file pursues further analysis on the spatial questions regarding the proximity of Denny's and La Quinta, and demonstrates the following skills:
    * use of `mean` and `median` to compute basic summary statistics
    * use of `full_join` to join two dataframes
    * definition and use of the Haversine distance function to compute the distance between two points on the Earth given latitude and longitude coordinates

## Summing up skills...Bikeshare Project

Analysis of the Washington D.C. Capital Bikeshare data provides a good summary of all of the skills described previously. The final part of this analysis is not included in the portfolio as it is the final project for the course...see the repository [here](https://github.com/Stephen-Miner/DS241-Class-Project). The data file used for these represents all rides from September 2022 Capital Bikeshare.

All files rely on _202209-capitalbikeshare-tripdata.zip_.

7. __Bikeshare General:__ 
In addition to using many of the skills described in the above section to explore the bikeshare dataset, this file also shows the following:
    * Basic R Skills
        * use of `ggplot2::geom_violin`/`ggplot2::geom_density` to illustrate/compare two distributions
        * use of `ggplot2::geom_step` to create a stairstep plot, focusing exactly on when changes occurs
        * use of additional `dplyr` functions such as `pivot_longer`, `slice_sample`, `arrange`, and `rename`
        * significant work with time data, including use of functions such as:
            * `as.POSIXct`
            * `%within%`
            * `interval`
            * `ggplot2::scale_x_datetime`
    * Data Science Process
        * Developing an algorithm to count the number of bikes out over time, given that each row in the dataset represents one ride and has a start and end time.
            * Starting to develop this algorithm on a small sample of the dataset for working efficiency, then once it's good, extending to the whole dataset.
        * Visualizing the result of the algorithm...verifying that it makes logical sense and making some observations based on the result.
8. __Bikeshare w/ Census Data:__
This file builds on the general bikeshare analysis by loading geographic data on the U.S. census tracts in Washington D.C. and creating spatial visualizations based on those:
    * Basic R Skills
        * use of `get_acs` from the `tidycensus` package to load census data
        * use of functions in `sf` package to manipulate spatial data such as `st_as_sf`, `st_intersects`, `st_crs`, `st_transform`
        * use of functions in `tmap` package to visualize spatial data such as `tmap_mode`, `tm_shape`, `tm_polygons`
    * Data Science Process
        * Identifying outliers in a dataset based on a visualization, recognizing that they hurt the effectiveness of the visualization, and removing them accordingly. (In this case, the outlier was the "mall" region of D.C.)
9. __Bikeshare w/ LODES Data:__
This file builds on the census tract-level bikeshare spatial analysis by incorporating data from the Longitudinal Employer-Household Dynamics (LODES) segment of the U.S. census data.
    * use of `lehdr::grab_lodes` function to get LODES data
    * use of `ggplot2::pivot_wider` and `left_join` to restructure data frames
10. __Bikeshare w/ Weather Data:__
This file uses a slightly different bikeshare dataset - one from 2011/2012 that is baked into the `dsbox` (Data Science in a Box) package - to model the effect of weather patterns on bikeshare usage.
    * Basic R Skills
        * use of `fct_relevel` function to manually reorder factor levels
        * use of `ifelse` function to evaluate conditions when cleaning data
        * use of regression functions: `linear_reg`, `set_engine("lm")`, `fit` (different from the functions used in the MA 132 Enrollment Analysis, but produce the same results)
    * Data Science Process
        * Clean data to get desired variables before modeling.
        * Visualize data before modeling to get a general sense of the situation.
        * Develop a series of models by adding and removing certain variables.
        * Interpret the meaning of the slope/intercept parameters and the `R^2` values of a model, and make observations about the data based on these interpretations.
        * Examine `R^2` values to compare the effectiveness of different models.