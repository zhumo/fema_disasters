# FEMA Declared Disasters 1953 - Present

This is a geographical representation of all FEMA declared disasters beginning in 1953 for each state. Viewers can filter data by disaster type. Each circle represents *relative* size, not absolute size.

This chart was built with d3.js and uses data collected from data.gov(http://catalog.data.gov/dataset/fema-disaster-declarations-summary) and the geographical data was obtained from Natural Earth(http://www.naturalearthdata.com/downloads/10m-cultural-vectors/10m-admin-1-states-provinces/). Additionally, credit should be given to Mike Bostock for his topojson command line tool as well his many thorough tutorials.

# How to Run It
This project relies on the data in topo-usa.json and it acquires that data through the d3.json() function, which is in turn built on XML. This means that topo-usa.json must be served. This file will not work if you simply open fema_disaster.html in a broswer. To make this work, I ran the python simple server by calling `$ python -m SimpleHTTPServer 8888`. This will run serve the files from localhost:8888.

# Interesting Results
* Coastal Storm (SD and ND)
* Freezing (FL)
* Human Causes (I see you, Florida Man)
* Terrorist (MA, probably because this designation was used in a major way due to the Boston Marathon Bombing)
* Toxic Substances (RI, NY)
* Tsunami (AR)
* Volcano (WA)

# To Do
* ~~Fix Michigan~~
  * Fixed by using the data set that does NOT include lakes.
* ~~Fix border highlighting, which is inconsistent across states. Some borders seem thicker than others.~~
  * Fixed by setting `fill-opacity: 0;`.
* ~~State does not highlight when hovering over the circle.~~
  * Fixed by putting both circle and path objects into a g and doing g:hover `.state{stroke-width: 3px;}`.
* ~~Add numbers to each circle~~
  * ~~Currently technically doable, but it gets kind of ugly with small states. I need to figure out the design.~~
  * ~~Maybe separate out the small states to a panel on the right?~~
  * Solved by adding a tooltip
* ~~Create a rescaling legend which gives more context as the circles scale up and down~~
  * Decided to get rid of the legend and just use tooltips.
* ~~Allow for filtering by year in addition to type.~~
  * ~~Dates are provided in mm/dd/yy format. Need to parse this.~~
  * Done!
* ~~Need to make circles not leak over into another state. (See NJ)~~
* ~~Refactor. Lots of repetition could be eliminated.~~
* When you switch to another incident type then switch back to Total Incidents, the bubbles do not go in order.
* Need to properly position the sliders.
* UI Improvement: The bubbles do not scale in an intuitive manner. When filter options are changed, sometimes the bubbles barely seem to change. Need to reconfigure the logic for the radiusScale.
