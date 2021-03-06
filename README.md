[![js-semistandard-style](https://img.shields.io/badge/code%20style-semistandard-brightgreen.svg?maxAge=3600&style=flat-square)](https://github.com/Flet/semistandard)
[![npm](https://img.shields.io/npm/v/animationframes.svg?maxAge=60&style=flat-square)](https://www.npmjs.com/package/animationframes)
[![Twitter Follow](https://img.shields.io/twitter/follow/pakastin.svg?style=social&maxAge=3600)](https://twitter.com/pakastin)

# animationframes
Minimalistic way to create JS animations (~1.5 KB). Use [prefix](https://github.com/pakastin/prefix) to auto-prefix CSS properties.

Battle-tested in my [HTML5 Deck of Cards](https://deck-of-cards.js.org), [source](https://github.com/pakastin/deck-of-cards/blob/master/lib/card.js#L65).

## install
    npm install animationframes

## usage

```js
import { frames, ease } from 'animationframes';

const translate = (x, y) => `translate(${x}%, ${y}%)`;

const el = document.createElement('h1');

const animation = frames(0, 1000)
  .start(() => {
    el.style.transform = translate(-100, 0);
  })
  .progress((t) => {
    const e = ease.quartInOut(t);
    const x = -100 * (1 - e);

    el.style.transform = translate(x, 0);
  })
  .end(() => {
    el.style.transform = '';
  });

el.textContent = 'Hello world!';

document.body.appendChild(el);
```
https://jsfiddle.net/o6vac675/4/

Another example: https://jsfiddle.net/pakastin/fjozqopm/

## easings
Available easings (you can use your own!): https://github.com/pakastin/animationframes/blob/master/src/ease.js

## oldskool
```html
<script src="https://pakastin.github.io/animationframes/animationframes.min.js"></script>
<script>
const { frames, ease } = animationframes;
...
</script>
```

## License
[MIT](https://github.com/pakastin/animationframes/blob/master/LICENSE)
