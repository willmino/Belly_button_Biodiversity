# Belly_button_Biodiversity
Javascript and Plotly for dynamic web display

link to the website! : https://willmino.github.io/Belly_button_Biodiversity/


## Overview

I used javascript and HTML code to create a webpage with dynamic charts. A JSON file "samples.json" was loaded into the javascript code using the
command `d3.json()` from the d3 library. A function called `then()` was chained to the `d3.json()` function. Inside the then() function, the iteration variable data was declared and it was used to capture each array of values from individuals who participated in a belly-button bacterial sampling study.

To make the webpage dynamic a listener was created to keep track of the changes to the dropdown menu on the website.
The below line of code is the dropdown menu. It was the `optionChanged()` function included as the property for the `onchange` attribute.
This javascript code in this HTML element takes the `this` object, which serves as the current object that javascript is iterating on, and chains 
the value function to it to get the value of `this`. In this case, `this` represents the new value from the dropdown menu that will be selected.


`<select id="selDataset" onchange="optionChanged(this.value)"></select>`


The visual landscape of the website was initialized using the init() function:


`function init() {`

    `var selector = d3.select("#selDataset");`
  
    `d3.json("samples.json").then((data) => {`
    
      `console.log(data);`
      
      `var sampleNames = data.names;`
      
      `sampleNames.forEach((sample) => {`
        `selector`
        
          `.append("option")`
          
          `.text(sample)`
          
          `.property("value", sample);`
          
      `});`

    `var firstSample = sampleNames[0];`
    
    `buildCharts(firstSample);`
    
    `buildMetadata(firstSample);`
    
  `});`
  
`}`

  `init();`
  
The function optionChanged() is created in the javascript file plots.js. It calls the function `buildMetaData()`, which creates a dynamic table representing the unique characteristics of each individual in the belly-button study. optionChanged() also calls `buildCharts`, which creates the wonderful charts showing the unique bacterial aspects of each individual in the study.
  
  `function optionChanged(newSample) {`
  
    `buildMetadata(newSample);`
    
    `buildCharts(newSample);`
    
  `}`


A dynamic data table was created for the website using the code below. 

`function buildMetadata(sample) {`

    `d3.json("samples.json").then((data) => {`
    
      `var metadata = data.metadata;`
      
      `var resultArray = metadata.filter(sampleObj => sampleObj.id == sample);`
      
      `var result = resultArray[0];
      
      `console.log(Object.keys(result));`
      
      `var PANEL = d3.select("#sample-metadata");`
  
      `PANEL.html("");`
      
      `index= Object.entries(result)`
      
      `//id_string = `
      
      `Object.entries(result).forEach(([key, value]) => {`
      
        `PANEL.append("h6").text(`${key.toUpperCase()}: ${value}`);`
        
      `});`
      
    `});`
    
  `}`
  
## Layout

In addition to the dynamic features, my website exhibits a crisp cool water color paltte. It matches the serene image at the top of the page.
The ocean is teeming with quadrillions of microflora which fuel the delicious oxygen in our atmospere. Us humans are utterly dependent upon our amazing oceanic microbials.
