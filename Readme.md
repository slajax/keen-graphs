
# keen.io-graphs

  An abstracted graphing library for Keen.io

## NOTICE

  This plugin requires you to implement [KeenJS v2](https://github.com/keenlabs/keen-js/tree/v2).
  This repo probably will not be updated to v3 so it's highly recommended you use Keen's v3 library directly.

## Installation

  Install with [component(1)](http://component.io):

    $ component install slajax/keen.io-graphs

## API

```javascript
  var keen = require('keen.io-graphs')(Keen); // inject configured keen.io obj

  keen.getSeries('pageViews', { groupBy: 'device' },
    function getMobileData(data, next) {
      var mobile = _.filter(data.result, function(d) {
        return d.value[0].type === 'mobile';
      });
      next(mobile);
    },
    function showMobileData(data) {
      // ... do some d3 magic ...
    }
  );

```

```javascript
  // Block Counts
  var graphs = keen.graphs;
  new graphs.number('#element-1', 'pageViews', '7 Day View Count');
  new graphs.number('#element-2', 'pageViews', '14 Day View Count', {
    timeframe: 'this_14_days'
  });
```
![Count Screen Shot](https://raw.github.com/slajax/keen.io-graphs/master/examples/imgs/count.png)

---

```javascript
  // Line Chart
  var graphs = keen.graphs;
  new graphs.line('#element-3', 'pageViews',
    { timeframe: 'this_7_days', interval: 'daily' },
    { title: '7 Day Page View Graph' },
  );
  new graphs.line('#element-4', 'pageViews',
    { timeframe: 'last_24_hours', interval: 'hourly' },
    { title: 'Past Day Page View Graph' },
  );
```
![Line Screen Shot](https://raw.github.com/slajax/keen.io-graphs/master/examples/imgs/line.png)

---


```javascript
  // Pie Chart
  var graphs = keen.graphs;
  new graphs.pie('#element-5', 'pageViews',
    { timeframe: 'this_7_days', interval: 'daily', group: 'source' },
    { title: '7 Day Page Views by Source' },
  );
```
![Line Screen Shot](https://raw.github.com/slajax/keen.io-graphs/master/examples/imgs/pie.png)

---

```javascript
  // Heatmap
  var graphs = keen.graphs;
  new keen.heatmap('#element-6', 'pageViews');
```
![Timeline Screen Shot](https://raw.github.com/slajax/keen.io-graphs/master/examples/imgs/timeline.png)

---

## Attribution

  Thanks to [Dustin Larimer](http://dustinlarimer.com) for his [original work](https://gist.github.com/dustinlarimer/7853815) on the Timeline Heatmap.

## License

(The MIT License)

Copyright (c) 2013 Kyle Campbell mail@slajax.com

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the 'Software'), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
