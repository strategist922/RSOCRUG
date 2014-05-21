---
title       : RSelenium - Introduction
subtitle    : Orange County R User Group
author      : John Harrison (johndharrison0@gmail.com)
email       : johndharrison0@gmail.com
job         : 
logo: big-logo.png
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}

--- .class1 #id1a bg:#E0F0FF

## John Harrison

<img style="float: right" src="https://dl.dropboxusercontent.com/u/38391057/2014-05-15%2010.23.30.jpg" />

--- .class1 #id1 bg:#E0F0FF

## What is Selenium?



1. Selenium automates browsers. (http://docs.seleniumhq.org/)
2. Selenium is a set of tools for cross-platform automated testing of web applications.
3. Selenium supports
  * Chrome, Firefox, Safari, Internet Explorer, PhantomJS and others
  * Windows, OS X, Linux, Android, iOS and other OS's
  * Bindings in a number of languages (http://docs.seleniumhq.org/download/)


--- .class #id2 bg:#E0F0FF 

## Why a set of tools?

    
Selenium is actually composed of a number of projects (http://docs.seleniumhq.org/projects/).

  * ![alt text](http://docs.seleniumhq.org/images/selenium-ide-logo.png "Sel ide") Selenium IDE 
  * ![alt text](http://docs.seleniumhq.org/images/selenium-rc-logo.png "sel rc") Selenium Remote Control
  * ![alt text](http://docs.seleniumhq.org/images/selenium-logo.png "sel WD") Selenium WebDriver
  * ![alt text](http://docs.seleniumhq.org/images/selenium-grid-logo.png "sel grid") Selenium Grid

Selenium WebDriver and Selenium Grid compose Selenium 2.0.

--- .class #id3 bg:#E0F0FF 

## Selenium 2.0

<div id="container">
  <table id="mytable">
  <tr>
   <td>RSelenium interacts with the WebDriver</td>
   <td></td>
  </tr>
  <tr>
   <td>The WebDriver "drives" the browsers.</td>
       <td></td>
  </tr>
  <tr>
   <td>The browsers have various bindings</td>
       <td></td>
  </tr>
  <tr>
   <td>Each browser may have bespoke methods</td>
       <td></td>
  </tr>
  </table>
  <div id="myimages">
    <img src = 'https://dl.dropboxusercontent.com/u/38391057/RRSOCRUG/sel_diag1.png'  height="280"/>
  </div>
</div>



  * Firefox - The driver comes in the form of an xpi (firefox extension)
  * Chrome - executable downloaded from the Chromium project </br>
  which acts as a bridge between "chrome" and the "driver".
  * IE - similar to chrome
  * The SafariDriver is implemented as a Safari browser extension.


--- .class #id4 bg:#E0F0FF 

## RSelenium

  * Implements the JsonWireProtocol http://code.google.com/p/selenium/wiki/JsonWireProtocol  
  * Project page: https://github.com/johndharrison/RSelenium
  * Issues: https://github.com/johndharrison/RSelenium/issues?state=open
  * CRAN: http://cran.r-project.org/web/packages/RSelenium/index.html

--- .class #id5 bg:#E0F0FF 

## Basic operation

  * Browser initiation
  * Navigation
  * DOM interaction
  * Frames and Windows

--- .class #id6 bg:#E0F0FF 

## Browser initiation





```r
# RSelenium::startServer()
library(RSelenium)
remDr <- remoteDriver(browserName = "someBrowser", remoteServerAddr = ip, port = port)
remDr$open(silent = TRUE)
remDr$navigate("http://somecoolsite")
```


<table class="_GAbc _GASwb"><tbody><tr><th class="_GADO"></th><th class="_GAnH ">Browser</th><th class="_GALF">Sessions</th><th class="_GAoJ">% Sessions</th></tr><tr class="ID-row-0-0-0 ACTION-select TARGET-row-0 _GAipb"><td class="_GActb">1.</td><td class="_GApT"><div class="_GANu _GALpb">Chrome</div></td><td class="_GALF">135</td><td class="_GAoJ _GANGb"><div style="width:29.74576271186441%;" class="_GAyzb"></div>45.76%</td></tr><tr class="ID-row-1-0-0 ACTION-select TARGET-row-1 "><td class="_GActb">2.</td><td class="_GApT"><div class="_GANu _GALpb">Firefox</div></td><td class="_GALF">111</td><td class="_GAoJ _GANGb"><div style="width:24.45762711864407%;" class="_GAyzb"></div>37.63%</td></tr><tr class="ID-row-2-0-0 ACTION-select TARGET-row-2 _GAipb"><td class="_GActb">3.</td><td class="_GApT"><div class="_GANu _GALpb">Safari</div></td><td class="_GALF">29</td><td class="_GAoJ _GANGb"><div style="width:6.389830508474576%;" class="_GAyzb"></div>9.83%</td></tr><tr class="ID-row-3-0-0 ACTION-select TARGET-row-3 "><td class="_GActb">4.</td><td class="_GApT"><div class="_GANu _GALpb">Internet Explorer</div></td><td class="_GALF">12</td><td class="_GAoJ _GANGb"><div style="width:2.644067796610169%;" class="_GAyzb"></div>4.07%</td></tr><tr class="ID-row-4-0-0 ACTION-select TARGET-row-4 _GAipb"><td class="_GActb">5.</td><td class="_GApT"><div class="_GANu _GALpb">Opera</div></td><td class="_GALF">3</td><td class="_GAoJ _GANGb"><div style="width:0.6610169491525423%;" class="_GAyzb"></div>1.02%</td></tr><tr class="ID-row-5-0-0 ACTION-select TARGET-row-5 "><td class="_GActb">6.</td><td class="_GApT"><div class="_GANu _GALpb">Safari (in-app)</div></td><td class="_GALF">3</td><td class="_GAoJ _GANGb"><div style="width:0.6610169491525423%;" class="_GAyzb"></div>1.02%</td></tr><tr class="ID-row-6-0-0 ACTION-select TARGET-row-6 _GAipb"><td class="_GActb">7.</td><td class="_GApT"><div class="_GANu _GALpb">Android Browser</div></td><td class="_GALF">2</td><td class="_GAoJ _GANGb"><div style="width:0.4406779661016949%;" class="_GAyzb"></div>0.68%</td></tr></tbody></table>

--- .class #id7 bg:#E0F0FF 


## Navigation


```r
remDr$Navigate("http://somewhere.com")
remDr$goBack()
remDr$goForward()
remDr$refresh()
remDr$getTitle()
remDr$getCurrentUrl()
remDr$getStatus()
remDr$getAllCookies()
remDr$deleteCookieNamed("PREF")
```


--- .class #id8 bg:#E0F0FF 

## DOM interaction

RSelenium has a number of methods of finding elements in the document object model with two methods to search anchor elements (An anchor is a piece of text which marks the beginning and/or the end of a hypertext link.)

  * By id
  * By class
  * By css selector
  * By name
  * By tag name
  * By link text (anchor elements)
  * By partial link text (anchor elements)

--- .class #id9 bg:#E0F0FF 

## Frames and Windows


```r
remDr$switchToFrame("string|number|null|WebElement")
remDr$getWindowHandles()
remDr$getCurrentWindowHandle()
remDr$switchToWindow("windowId")
```



--- .class #id10 bg:#E0F0FF 

## Advanced operation

  * Javascript
  * Interacting with shiny apps
  * Remote driving
  * External providers
  

--- .class #id11 bg:#E0F0FF 

## Javascript

  * d3Network Example
  https://github.com/christophergandrud/d3ShinyExample . Neat package for
  creating interactive network graphs from R. All the power of d3.js without the pain.

<img src="https://dl.dropboxusercontent.com/u/38391057/Screenshot%202014-05-15%2022.20.09.png", width = 900, height = 400 />



--- .class #id12 bg:#E0F0FF 

## Interacting with shiny apps

  * Dialect Map
  http://spark.rstudio.com/jkatz/SurveyMaps/
  If I remember rightly this one went [viral](http://www.businessinsider.com/22-maps-that-show-the-deepest-linguistic-conflicts-in-america-2013-6?op=1) was viewed 7 million times and crashed rstudios server.
  
  * RSelenium test app
  Viewable at http://spark.rstudio.com/johnharrison/shinytestapp/ or can be ran from the Rselenium package locally.

<img src="https://dl.dropboxusercontent.com/u/38391057/RRSOCRUG/Screenshot%202014-05-16%2004.56.53.png", width = 900, height = 400 />

--- .class #id13 bg:#E0F0FF 

## Remote driving 
(http://johndharrison.blogspot.co.uk/2014/03/rstudioshiny-server-on-digital-ocean.html)
<img src="https://dl.dropboxusercontent.com/u/38391057/RRSOCRUG/Screenshot%202014-05-16%2006.08.20.png" , width = 900, height = 300 />

```
remDr <- remoteDriver(remoteServerAddr = "128.199.255.233", browserName = 'phantomjs')
remDr$open()
remDr$navigate("http://whatismyipaddress.com/")
remDr$screenshot(display = TRUE)
remDr$close(); remDr$closeServer()
```

--- .class #id14 bg:#E0F0FF 

## External providers

  * Sauce Labs - http://saucelabs.com/
  ```
  user <- "rselenium0"
  pass <- "*******************************"
  port <- 80
  ip <- paste0(user, ':', pass, "@ondemand.saucelabs.com")
  browser <- "firefox"
  version <- "25"
  platform <- "OS X 10.9"
  extraCapabilities <- list(name = "Test RSelenium", username = user, accessKey = pass)

  remDr <- remoteDriver$new(remoteServerAddr = ip, port = port, browserName = browser
                          , version = version, platform = platform
                          , extraCapabilities = extraCapabilities)
  ```

--- .class #id14b bg:#E0F0FF 

## External providers

  * Browser Stack - http://www.browserstack.com/
  
  ```
  require(RSelenium)
  user <- "johnharrison" 
  pass <- "******************"
  port <- 80
  ip <- paste0(user, ':', pass, "@hub.browserstack.com")
  extraCapabilities <- list("browser" = "IE",
                          "browser_version" = "7.0",
                          "os" = "Windows",
                          "os_version" = "XP",
                          "browserstack.debug" = "true")
  remDr <- remoteDriver$new(remoteServerAddr = ip, port = port
                          , extraCapabilities = extraCapabilities)
  ```

--- .class #id15 bg:#E0F0FF 

## External example

```
testAppScript <- function(remDr){
  remDr$open(); remDr$setImplicitWaitTimeout(2000)
  remDr$navigate("http://spark.rstudio.com/johnharrison/shinytestapp/")
  Sys.sleep(2)
  webElems <- remDr$findElements("css selector", "#ctrlSelect span")
  lapply(webElems, function(x){x$highlightElement()})
  Sys.sleep(2)
  appIds <- c("summary", "distPlot", "ggPlot", "dttable")
  lapply(seq_along(webElems), function(x){
    if(!webElems[[x]]$isElementSelected()[[1]]){
      webElems[[x]]$clickElement()
      # test for its output
      out <- remDr$findElement("id", appIds[x])
      out$highlightElement()
    }})
  remDr$close()
}
testAppScript(remDr)
```
