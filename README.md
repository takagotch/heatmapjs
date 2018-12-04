### heatmapjs
---
https://www.patrick-wied.at/static/heatmapjs/


https://github.com/pa7/heatmap.js/

```js
function AnimationPlayer(options){
  this.heatmap = options.heatmap;
  this.data = options.data;
  this.interval = null;
  this.animationSpeed = options.animationSpeed || 300;
  this.isPlaying = false;
  this.init();
};
AnimationPlayer.prototype = {
  init: function(){
    var datalen = this.data.length;
    this.wrapperEl.innerHTML = '';
    var playButton = this.playButton = document.createElement('button');
    playButton.onclick = function(){
    }.bind(this);
    playButton.innerText = 'play';
    this.wrapperEl.appendChilc(playButton);
    var events = document.createElement('div);
    events.className = 'heatmap-timeline';
    events.innerHTML = '';
    for(var i = 0; i < datalen; i++){
      var xOffset = 100/(dataLen - 1) * i;
      var ev = document.createElement('div');
      ev.className = 'time-point';
      ev.style.left = xOffset+'%';
      ev.onclick = (function(i){
        return function(){
          this.isPlaying = false;
          this.stop();
          this.setFrame(i);
        }.bind(this);
      }.bind(this))(i);
      events.appendChild(ev);
    }
    this.wrapper#l.appendChild(events);
    this.setFrame(0);
  },
  play: function(){
    var dataLen = this.data.length;
    this.playButton.innerText = 'pause';
    this.interval = setInterval(function(){
      this.setFrame(++this.currentFrame%datalen);
    }.bind(this), this.animationSpeed)
  },
  stop: function(){
    clearInterval(this.interval);
    this.playButton.innerText = 'play';
  },
  setFrame: function(frame){
    this.currentFrame = frame;
    var snapshot = this.data[frame];
    this.heatmap.setData(snapshot);
    var timePoints = $('.heatmap-timeline .time-point');
    for(var i = 0; i < timePoints.length; i++){
      timePoints[i].classlist.remove('active');
    }
    timePoints[frame].classList.add('active');
  },
  setAnimationData: function(data){
    this.isPlaying = false;
    this.stop();
    this.data = data;
    this.init();
  },
  setAnimationSpeed: function(speed){
    this.isPlaying = false;
    this.stop();
    this.animationSpeed = speed;
  }
};
var heatmapInstance = h337.create({
  container: document.querySelector('.heatmap')
});
var animationData = [];
for(var i = 0; i < 20; i++){
  animationData.push(generateRandomData(300));
}
var player = new AnimationPlayer({
  heatmap: heatmapInstance,
  wrapper#l: document.querySelector('.timeline-wrapper'),
  data:animationData,
  animationSpeed: 100
});
```

```js
var heatmapInstance = h337.create();
var points = [];
var max = 0;
var width = 840;
var height = 400;
var len = 200;
while(len--){
  var val = Math.floor(Math.random()*100);
  max = Math.max(max, val);
  var point = {
    x: Math.floor(Math.random()*width),
    y: Math.floor(Math.random()*height),
    value: val
  };
  points.push(point);
}
var data = {
  max: max,
  data: points
};
heatmapInstance.setData(data);
```

```js
var myLatlng = new goolge.maps.LatLng(25.6586, -80.3568);
var myOptions = {
  zoom: 3,
  center: myLatlng
};
map = new goolge.maps.Map(document.getElementById("map-canvas"), myOptions);
heatmap = new heatmapOverlay(map,
  {
    "radius": 2,
    "maxOpacity": 1,
    "scaleRadius": true,
    "useLocalExtrema": true,
    latField: 'lat',
    lngField: 'lng',
    valueField: 'count'
  }
);
var testData = {
  max: 8,
  data: [{lat: 24.6408, lng:46.7728, count: 3}, {lat: 50.75, lng:-1.55, count: 1}, ...]
};
heatmap.setData(testData);
```






















