---
layout: research
title: Research - Blogs
---
 {% include alm/setup %}
<script language="javascript">
$($("#blog").children()[0]).css('color', '#EC6197');
</script>

<div class="row">
<div class="col-md-2">Sort by:</div>
<div class="btn-group" data-toggle="buttons">
  <label class="btn btn-default active">
    <input type="radio" id="q156" name="sortby" checked="checked" value="0" /> Timeline
  </label> 
  <label class="btn btn-default">
    <input type="radio" id="q160" name="sortby" value="1" /> Category 
  </label>
</div>
</div>



<!--by timeline-->
<div name="sortby" class="row typo" style="display:block;">
  <div class="col-md-9" >
    {% assign posts_list = site.posts %}  
    {% include alm/timeline %}
  </div>
  <div id="time-list-nav" class="col-md-3">
    <ul id="time-list-ul" class="nav nav-tabs nav-stacked nav-pills time-list affix">
      {% include alm/time_list %}
      {% assign posts_list = nil %}
    </ul>
  </div>
</div>


<!--by category-->
<div name="sortby" class="tabbable tabs-right row" style="display:none;">
  <ul class="nav nav-tabs" id="categories-nav">
    {% assign site_categories = site.categories %}
    {% include alm/anchor_of_categories %}
  </ul>

  <div class="tab-content">
    {% for category in site.categories %} 
    <div class="tab-pane" id="{{ category[0] }}-ref" style="display: block;">
      <ul class="posts-list">
        {% assign posts_list = category[1] %}  
        {% include alm/posts_of_category %}
      </ul>
    </div>
    {% endfor %}
  </div>
</div>

<script type="text/javascript">

var divs = $('div[name=sortby]');

$( "input[name='sortby']" ).change(function() {
  if($("input[name='sortby']:checked").val()=="0"){
    divs[0].style.display='block';
    divs[1].style.display='none';
  }else{
    divs[0].style.display='none';
    divs[1].style.display='block';
  }
});

</script>
