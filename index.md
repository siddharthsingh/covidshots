---
layout: default
classes: wide
title: Covid Shots
---

<style title="inlineCSSTitle">
.filter{
  margin-top: 10px !important;
}

#vaccinesAvailableNumBlock img {
    margin-right: auto; 
    justify-self: flex-start;
    width: 32px;
    border-radius: 8px;
    cursor: pointer;
}
</style>

<link rel="stylesheet" type="text/css" href="index.css">
<link rel="stylesheet" type="text/css" href="semantic.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.24/css/jquery.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://unpkg.com/intro.js@3.4.0/minified/introjs.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/responsive/2.2.7/css/responsive.dataTables.min.css">
<link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/buttons/1.7.0/css/buttons.dataTables.min.css">

<script src="https://code.jquery.com/jquery-3.5.1.min.js" crossorigin="anonymous"></script>
<script src="semantic.min.js"></script>
<script src="components/state.min.js"></script>
<script src="js/tablesort.js"></script>
<script src="js/tata.js"></script>
<script src="https://cdn.datatables.net/1.10.24/js/jquery.dataTables.min.js"></script>
<script src="https://cdn.datatables.net/1.10.24/js/dataTables.semanticui.min.js"></script>
<script src="https://cdn.datatables.net/responsive/2.2.7/js/dataTables.responsive.js"></script>
<script src="https://cdn.datatables.net/buttons/1.7.0/js/dataTables.buttons.min.js"></script>

<script src="https://unpkg.com/dayjs@1.8.21/dayjs.min.js"></script>
<script src="https://unpkg.com/dayjs@1.8.21/plugin/customParseFormat.js"></script>
<script>dayjs.extend(window.dayjs_plugin_customParseFormat);</script>

<script src="https://unpkg.com/intro.js@3.4.0/minified/intro.min.js"></script>


<!--START https://codepen.io/desirecode/pen/MJPJqV-->
<a href="#" id="scrollToTop" style="display: none; z-index:9999"><span></span></a>
<!--END-->

 <div class="ui top sidebar" id="topBar" style="display:none">
    <p id="AutoRefreshRecordGif">&nbsp;⬤</p>
    <p>&nbsp;Refreshing in </p>
    <p id="AutoRefreshRecordTimeRemaing"></p>
    <p>&nbsp;seconds </p>
  </div>

<div class="ui blue inverted menu">
  <a href="https://covidshots.in/?" class="item" target="_self" rel="noopener noreferrer">Home</a>
  <!--<a class="item"></a>-->
  <div class="right menu">
    <a class="item" id="siteTour">Tour</a>
    <a href="https://github.com/lihas/covidshots/blob/gh-pages/Readme.md" class="item" target="_blank" rel="noopener noreferrer">Help</a>
<!---->
  <div class="ui dropdown item" id="navbarMoreBtn">
    More
    <i class="dropdown icon"></i>
    <div class="menu">
      <a class="item" href="https://github.com/lihas/covidshots/issues" target="_blank" rel="noopener noreferrer"><i class="bug icon"></i>Report bug</a>
      <a class="item" href="https://github.com/lihas/covidshots/issues" target="_blank" rel="noopener noreferrer"><i class="magic icon"></i>Request feature</a>
      <a class="item" target="_blank" rel="noopener noreferrer" id="SettingsDialogButton"><i class="cog icon"></i>Settings</a>
      <a class="item" target="_blank" rel="noopener noreferrer" id="AboutDialogButton"><i class="info circle icon"></i>About</a>
    </div>
  </div>
<!---->
  </div>
</div>

<div class="ui modal" id="SettingsDialogModal">
  <div class="header">Settings</div>
  <div class="scrolling content">

  <div class="ui toggle checkbox" id="SettingAutoScroll">
  <input type="checkbox" name="public" checked="checked" id="SettingAutoScrollInput">
  <label title="When ON auto scrolls to table when results are available">Auto Scroll</label>
  </div>

    <p></p>
  </div>
  <div class="actions">
    <!--<div class="ui approve button">Approve</div>
    <div class="ui button">Neutral</div>-->
    <div class="ui cancel button">Close</div>
  </div>
</div>


<div class="ui modal" id="AboutDialogModal">
  <div class="header">About</div>
  <div class="scrolling content">

  <a href="https://icons8.com/icon/f35ivmW8y15E/combo-chart">Combo Chart icon by Icons8</a>
  <a href="https://thenounproject.com/search/?q=vaccine&i=2196600">vaccine by mynamepong from the Noun Project</a>

    <p></p>
  </div>
  <div class="actions">
    <!--<div class="ui approve button">Approve</div>
    <div class="ui button">Neutral</div>-->
    <div class="ui cancel button">Close</div>
  </div>
</div>

<h3 class="ui header">Find free vaccination slots across districts, set alarms!</h3>

<h5 class="ui header">States</h5>
<select name="states" multiple="" class="ui fluid dropdown" id="states">
</select>


<h5 class="ui header">Districts</h5>
<select name="districts" multiple="" class="ui fluid dropdown disabled" id="districts">
    <option>Select districts</option>
</select>

<label for="dateInput">Date:</label>
<input type="date" id="dateInput" name="dateInput" />




<h5 class="ui header">Filters</h5>
<button class="ui toggle button filter grey basic" id="filter_age_18_45">18-45</button>
<button class="ui toggle button filter grey basic" id="filter_age_45_plus">45+</button>
<button class="ui toggle button filter grey basic" id="filter_vaccine_covishield">Covishield</button>
<button class="ui toggle button filter grey basic" id="filter_vaccine_covaxin">Covaxin</button>
<button class="ui toggle button filter grey basic" id="filter_vaccine_sputnikv">SPUTNIK V</button>
<br />
<button class="ui toggle button filter grey basic" id="filter_vaccine_dose_1">Dose 1</button>
<button class="ui toggle button filter grey basic" id="filter_vaccine_dose_2">Dose 2</button>
<br /><br />

<h5 class="ui header">Auto refresh</h5>

<div class="toggle ui animated button" tabindex="0" id="btn_auto_refresh" style="float:left">
      <div class="hidden content">Auto Refresh</div>
      <div class="visible content">
      <i class="big sync alternate icon"></i>
      </div>
</div>

<button class="circular ui icon button" id="alarm_vaccine">
  <i class="big bell slash icon" id="alarm_vaccine_icon"></i>
</button>

<br />

Refresh interval (minutes):
<div class="ui right labeled input disabled" id="input_auto_refresh_interval_parent">
<input type="number" placeholder="Enter time.." id="input_auto_refresh_interval" name="input_auto_refresh_interval" min="2" max="600" value="5">
<div class="ui basic label">
minutes
</div>
</div>

<br/>
<div style="display: flex; width: 100%;float: right;flex-direction: row; align-content: flex-end; align-items: flex-end;justify-items: flex-end;" id="vaccinesAvailableNumBlock">
<img src="images/icons8-combo-chart.gif" id="viewStatsImgBtn">
<h3 class="ui grey header" style="display:inline; margin:0;">Vaccines available &nbsp;</h3>
<h1 id="vaccinesAvailableNum" class="ui orange header" style="display:inline; margin:0;">0</h1>
</div>

<iframe id="viewStatsContent" framborder="0" scrolling="no" style="display:none">
</iframe>

<br />
<table id="centreList" class="display" width="100%"><thead></thead></table><!--https://stackoverflow.com/a/32484034/981766-->

<script src="index.js?v=1.1"></script>