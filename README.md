# Data Visualization

As the sixth project of the Data Analyst Nanodegree program, I used html, css and javascript - d3.js and other js libraries to create an explanatory data visualization. The goal of this project is to effectively and clearly communicate a finding(s) to the audience. 

The interactive visualization can be viewed here: [Meteorite Strikes](http://bl.ocks.org/sharad-vm/af74ae5932de1bcf5a39b0f3f849d847)

### Summary

While working on some datasets in Kaggle, I came across [Meteorite Landings](https://www.kaggle.com/nasa/meteorite-landings#) dataset and immediately had an idea of telling a story on how different meteorites have struck our planet since the beginning of recorded meteorite times. I also wanted to integrate population density into my visualization to show any connection between the two. 

In doing this, I built a world map and used the co-ordinates of the meteorites to plot them on the map based on their mass and also animated their strike itself. I also used colors to differentiate observed vs found meteroites. The animation would run starting year 860 all the way till 2013 (as per the dataset). The result was a beautiful animation of the meteorites striking our planet with time. 
Due to the number of meteorites (data points), SVG takes a while to load all of them. As we do not have the time available always to wait for the animation to finish, I added a Skip Intro button to finish the animation for us so that all the meteorite information is available for us on the map. 

As mentioned earlier, I integrated population density on the map by changing the map's opacity based on the population density of the region. I used World Bank's population density dataset for the year 2016 to visualize this. Although, I could have used the meteorite's corresponding year for population density, I thought it was unnecessary for this particular project as no meteorite has hugely altered human population density and would also add additonal performance overhead.

### Design

The visulization is roughly divided into 3 parts - a header, a map or visualization and a story on the right

As the name suggests, the header contains the heading and 3 tween attributes - year and count of found and observed meteorites, that interpolate based on the animation that is progressing on the map. 
The animation in the visualization starts from the oldest year available t the most recent and the Year scroll keeps track of this and the counts of found and observed meteorites are cumulatively displayed in the Found and Observed scrolls as the animation progresses. 

The map contains the entire visualization - an interactive map, meteorites, animation etc.,
I used bootstrap to help organize different parts as a grid and jQuery and d3 for interactivity and animation.
The aniamtion starts from the oldest year and visualizes the meteors fall and strike the planet at its corresponding co-ordinates.
I also added an effect to the strike itself to visualize the contact made on the ground. This has also helped in cases of really small meteorites to identify where it ends up striking. 

The story carusel consists of buttons and information to toggle the visualization and also provide details on the visualization.
There are 4 buttons that either display information in understanding the visualization and its importance and also changes the visualization. Due to the time consuming nature of the animation, I've added a Skip Intro button that skips the animation and loads all the meteorites. The Info button is selected by default in order for users to get an introduction to the visualization. The population Density button alters the map's opacity based on the respective region's population density. The Data button displays information about the datasets used for this visualization. Note that choosing a different button from Population Density brings the map back to its original setting.

In order to get all of this working, I had to combine 3 different datasets - a geojson file, meteorites data and population density data.
I joined the geojson file and the population density file and added the population density (per sq. km) to the geojson file for each country. I then used the meteorites data to plot the meteorites on the map.

### Feedback

I received feeback from 3 people loosely based on the questions mentioned in Udacity's project submission page.

##### Feedback 1

[First Iteration](https://bl.ocks.org/sharad-vm/6821d9945d06e6c5e5b767fc37aed77b)

>The animation and the idea of a scroll on the right side look good. However, the information provided in the visual is minimal.
>This could be improved. Zoom on the map is not smooth. It does not work correctly sometimes.

##### Changes after Feedback 1

I made a lot of changes after the first feedback.
* Added a lot more information and buttons to navigate to different views to the scroll on the right
* Added year to the header scroll
* Added a 'strike' effect to the animation 
* Added a Skip Intro button to skip the animation

##### Feedback 2

[Second Iteration](http://bl.ocks.org/sharad-vm/dbe6ab9546c5acf2e0ab42b687da03ff)

>The message in the beginning looks odd. Any reason why you have this?
>The animation looks goodin the beginning but it speeds up later and is not really visible. 
>The numbers in the fallen and observed do not match the meteorites on screen.
>I like how you tried to integrate population density on the map. I don't understand it's relationship with meteorites.

##### Feedback 3 

>I don't understand the introduction message. Is this a placeholder as of now for some message?
>The animation is slow but but does the job. I like the idea of 'Skip Intro'. You should consider making the button clear. It is being >cut off right now.
>The counts don't seem to be in sync when Skip Intro feature is used and the animation sometimes looks like it is repeating a bunch of meteorites.

##### Changes after Feedback 2 & 3

* Removed the intro message
* Modified and improved the scroll on the right
* Improved language and font
* Modified and improved the header scrolls

##### Feedback 4

[Third Iteration](http://bl.ocks.org/sharad-vm/2e743dae80e09b8aaa3779bc886a584d)

From the same person who gave Feedback 3
>Looks much better now. The different meteorites in conjunction with population density is clear.
>Aesthetics could be improved further.

##### Changes after Feedback 4

* Modified and improved the background color and some aesthetics
* Fixed and improved the header scroll issue with counts to be in sync with the animation

[Final Version](http://bl.ocks.org/sharad-vm/af74ae5932de1bcf5a39b0f3f849d847)

### Conclusion

While I'm happy with the outcome of this visualization, I want to acknowledge the performance issue in SVG handling 
so many circles and animation itself. In this regard, I have tried using Canvas instead of SVG to make the visualization faster.
Keeping in mind a drawback of Canvas, that I cannot directly add a tooltip and will have to use a workaround to add a second hidden canvas to make the tooltip work and the time involved in making these changes, I will consider replacing SVG with Canvas in a future project. With SVG, the visualization works perfectly for everything else.

### Resources

* [Blocks](https://bl.ocks.org/)
* [Feltron](http://feltron.com/)
* [D3 - Animation & Interaction](http://synthesis.sbecker.net/articles/2012/07/10/learning-d3-part-3-animation-interaction)
* [Animated Data - Peter Cook](http://animateddata.co.uk/)
* [HTML5 - Canvas Tutorials](https://www.html5canvastutorials.com/tutorials/html5-canvas-circles/)
