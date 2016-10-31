# include-media grid mixins
This is an addon for the great [include-media](http://include-media.com) that allows you to create a robust, responsive grid while maintaining clean, semantic markup. This prevents your compiled CSS from being littered with unused classes, and keeps excess presentation classes out of your markup.

## Installation

- bower: `bower install include-media-grid-mixins`
- npm: `npm install include-media-grid-mixins`

```
@import 'include-media';
@import 'include-media-grid-mixins';
```

## Configuration

By default, it will output a Bootstrap-style grid (floats, inline-block elements) with 12 columns and 30px gutters. But you can configure any of these properties with a `$grid` map.

*Defaults*
```
$grid: (
  columns: 12,
  gutters: 30px,
  layout: 'standard' // options: 'standard', 'flexbox'
);
```

## Mixins
- `@include grid-container` will create a centered container for your grid. Roughly equivalent to Bootstrap's `.container` - add your own width/max-width as needed.
- `@include grid-row` will create a row in your grid. Equivalent to Bootstrap's `.row`.
- `@include grid-item((breakpoint: # of columns, [...]))` accepts a map based on your include-media `$breakpoints` configuration. Set the number of columns for each breakpoint as needed.
- `@include grid-item-offset((breakpoint: # of columns, [...]))` accepts a map based on your include-media `$breakpoints` configuration. Use to offset a column at given breakpoints.


## Example Usage

*Markup*
```
<div class="some-block">
  <div class="some-block__wrapper">
    <div class="some-block__some-element"></div>
    <div class="some-block__other-element"></div>
    <div class="some-block__third-element"></div>
  </div>
</div>
```

*Styles*
```
@import 'include-media';
@import 'include-media-grid-mixins';

.some-block {
  &__wrapper {
    @include grid-row;
  }

  &__some-element {
    @include grid-item(('phone': 6, 'tablet': 4, 'desktop': 3));
  }

  &__other-element {
    @include grid-item(('phone': 6, 'tablet': 4, 'desktop': 6));
  }

  &__third-element {
    @include grid-item(('tablet': 4, 'desktop': 3));
  }
}
```

## Inspiration
- [include-media](http://include-media.com)
- [Bootstrap sass](https://github.com/twbs/bootstrap-sass)
- [Susy](http://susy.oddbird.net/)

## Author
[Charley Pugmire](http://charleypugmire.me)
