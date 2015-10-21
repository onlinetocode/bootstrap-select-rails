# Bootstrap::Select::Rails

bootstrap-select-rails provides the [bootstrap-select](https://github.com/silviomoreto/bootstrap-select) JS and CSS as a Rails engine for use with the Rails asset pipeline.

See [bootstrap-select Documentation](https://silviomoreto.github.io/bootstrap-select) for more details and expanded usage.

## Installation

Add this line to your Gemfile:

```ruby
gem 'bootstrap-select-rails'
```

And then run `bundle install`.

Or install it yourself as:

`$ gem install bootstrap-select-rails`
    
## Usage

In your `application.js` file include the base js file:

```js
//= require bootstrap-select
```

and in your `application.css` file include the css:

```css
/*
= require bootstrap-select    
*/
```

Add any needed locale files to your `application.js` like:
```js
//= require bootstrap-select
//= require bootstrap-select/i18n/defaults-de_DE
```

Restart your webserver if it was previously running.

### SCSS/SASS Support
If you use [SCSS](http://sass-lang.com/documentation/file.SASS_REFERENCE.html), add this to your `application.scss` file:
```scss
@import "bootstrap-select";
```
    
or if you use [SASS indented style](http://sass-lang.com/docs/yardoc/file.INDENTED_SYNTAX.html), add this to your `application.sass` file:
    
```SASS
@import bootstrap-select
```

## Views/Helpers

Add the `selectpicker` class to your `<select>` element like:
```ruby
= select :post, :category, Post::CATEGORIES, class: 'selectpicker'
```

### Options/Configuration

Additional `bootstrap-select` options are supplied through HTML attributes:
```ruby
= select :post, :category, Post::CATEGORIES, class: 'selectpicker', title: 'Please choose a category&hellip;'.html_safe, data: { live_search: true }
```
Checkout the [documentation](https://silviomoreto.github.io/bootstrap-select) for more configuration.

## Notes/Troubleshooting

### Required Bootstrap Components
You must require at least the *alert* and *dropdown* bootstrap components.
For example, if using
[bootstrap-sass gem](https://github.com/twbs/bootstrap-sass):

```js
//= require bootstrap/alert
//= require bootstrap/dropdown
```

### Turbolinks trouble
Using turbolinks, the bootstrap-select component will not be initialized after page load and must be injected into the `turbolinks` `page:load` callback like:

`application.js`
```js
var ready;

ready = function() {
  $('.selectpicker').selectpicker 'render'
};

$(document).on('page:load', ready);
```

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

# Copyright and license

Copyright (C) 2013 bootstrap-select-rails

Licensed under the MIT license.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
