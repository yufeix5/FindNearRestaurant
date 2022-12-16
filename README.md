# Buffer map of restaurants near UW
by Yufei Xia, Aaron Thai, Amun Ibrahim Ahmed, Justen Ho

## Project description 
For our project, we made a buffer map that shows the restaurants in an area in Seattle. In the map we included the feature that allows the user to choose the center of a 1 km buffer. Then we can check and see what restaurants fall within the range. We set up the base map first. Then we used the Turf.js to write the createbuffer() function and when the user selects the location on map, it triggers the click event and the createbuffer() function should be called and the buffer is going to be displayed. We also added the points (icons) to lie within the buffer and display their info when clicked. 

##  Project goal
The message we want to deliver through this project is that we want to make it for the public looking for restaurants in Seattle, specifically the UW area. We provided users with an information panel that can display information about the restaurants within the map. Information included provides the address, names, and descriptions of the restaurants. 

##  The application URL (not the repository url) 
https://yufeix5.github.io/FindNearRestaurant/ 

## Screenshots 

![image](/images/example1.png "ss1")
*Default view of the map, centered on the University of Washington Seattle campus.*

![image](/images/example2.png "ss2")
*Example of the hover and popup function.*

![image](/images/example3.png "ss3")
*Example of the click and buffer function, marking the center and restaurants within the buffer.*

## Main functions 
There are 6 main functions that are involved in our project. The first function is the ability to zoom in and out of the map, this allows the user to see a desired area at a closer, more detailed view of the streets and the buildings/restaurants that are nearby. The zoom out function allows the user to see a larger area with less detail. For example, if the user wanted to look at specific restaurants in University Village, they can zoom in and see all the different restaurants and the name of the streets that are nearby, additionally if instead the user wanted to see restaurants in a bigger area, they can zoom out and see all of the restaurants in University District, but would lose the detailed street or building information. Our map also has the ability to drag/move around king county, this function enables the user to see different parts of the county. 

Another function that our map has is the hovering function. This function allows the user to hover their mouse over a restaurant and information will be portrayed to the user. The information displayed shows the restaurant name, the amount of seating, risk category, address, and the restaurant's phone number. Additionally, another function in our map is the clicking function. Whenever the user clicks on the map, it shows a buffer around where the user clicked, showing all the restaurants in that buffer (1km range). Lastly, we included a search bar function, in which the user is able to search any restaurant or address and the map will zoom in on the desired address, even if there is no restaurant at the searched address. 

##  Data sources 
The original data source is food establishment inspection records from [King County Open Data]https://data.kingcounty.gov/Health-Wellness/Food-Establishment-Inspection-Data/f29f-zza5). Data was provided by the Health Department at Seattle and King County. This data contains inspection records for more or less all of the food establishments in King County from 2006 to the present. Notably, we could not seem to find records for some food establishments inside the UW campus like Starbucks or Pagliacci Pizza at the HUB. This left some obvious gaps in the map, but the dataset also contained surprising locations like fraternities which probably needed inspections of their kitchens.

We downloaded the data from King County Open Data as a csv. Then we used R to clean the data. We cleaned the data by taking out rows with a duplicate address. This may have removed some establishments that happened to be located at the same address, but it was an efficient solution to remove inspection records for the same establishment across different years. We kept rows that were in Seattle (so either “SEATTLE” or “Seattle”). We removed half of the rows that were specific to individual inspections like Inspection Date. 

We only wanted information about the restaurants in general, like the seating, the address, and the phone number. This was needed to reduce the file size and loading speed for a web map. Lastly, we converted the csv to geojson in QGIS. This was necessary because turf.js uses geojson data to make buffers.

### Explanation of column names

**NAME:** Names of the restaurants and food establishments.

**DESCRIPTION:** Number of seating and risk category. According to [King County’s website](https://kingcounty.gov/depts/health/environmental-health/food-safety/inspection-system/search.aspx#/), “Risk categories are determined by the complexity of the businesses' food processing and handling.” From our observations, Risk I seems to apply to convenience stores like Circle K. Risk II seems to apply to school lunch programs like elementary schools. Risk III seems to apply to sit down restaurants like UW’s Saint Bread and Agua Verde.

**ADDRESS:** Address of the restaurants.  
**CITY:** Seattle  
**ZIP.CODE:** Zip Code of the region where restaurants are located.  

**PHONE:** Contact information of the restaurant. This is probably not the same one used to make delivery orders, but is more likely the owner’s contact number since multiple establishments can share a number. For example, the (206) 722-6400 number is shared by a Tutta Bella restaurant and a Tutta Bella mobile food unit. The (972) 828-6928 number is shared by five different 7-Elevens.

**LONGITUDE:** Geographical coordinates of the restaurants.  
**LATITUDE:** Geographical coordinates of the restaurants.  
**BUSINESS_ID:** Unique identification for each restaurant.  
**GRADE:** Food establishment grade.  

## Applied libraries (e.g., mapbox gl js) and Web Services (e.g., github, basemap) in use 

Mapbox GL JS 
https://docs.mapbox.com/mapbox-gl-js/api/ 

Turf.js Plugin 
https://turfjs.org/ 

Mapbox Geocoding API 
https://docs.mapbox.com/api/search/geocoding/ 

Mapbox Studio for making custom base map 
https://studio.mapbox.com/ 
Basemap url: mapbox://styles/lexixia/clblf6oja000d15pa9alqxxy9   

Github Pages for hosting the project 
https://pages.github.com/ 

## Acknowledgment

Create a hovering effect https://docs.mapbox.com/mapbox-gl-js/example/hover-styles/ 

Analyzing data with Turf.js and Mapbox GL JS https://docs.mapbox.com/help/tutorials/analysis-with-turf/ 

Add a geocoder https://docs.mapbox.com/mapbox-gl-js/example/mapbox-gl-geocoder/ 

Pre-built Mapbox gl styles 
https://github.com/mapbox/mapbox-gl-styles 

Load data from external geojson
https://docs.mapbox.com/mapbox-gl-js/example/external-geojson/ 

## Other things that are necessary to inform the audience
Thanks to our professor Bo Zhao and TA Steven Bao for teaching our class, [Geog 495](https://github.com/jakobzhao/geog495).

