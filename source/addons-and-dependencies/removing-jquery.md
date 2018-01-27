Ember has been relying on jQuery in the past, and it still ships it by default.
However since Ember 3.x it is an optional dependency, that you can opt out from.

To do so, add the [`@ember/optional-features`](https://github.com/emberjs/ember-optional-features) addon,
if you have not done so already, and disable the `jquery-integration` flag:

```shell
ember install @ember/optional-features
ember feature:disable jquery-integration
```

This will remove jQuery from your `vendor.js` bundle and disable any use of jQuery in Ember itself.

## Caveats

With jQuery not being available anymore, this will break any code that still relies on it, especially any usage of

* [`this.$()`](https://www.emberjs.com/api/ember/release/classes/Component/methods/$?anchor=%24) in components
* `jQuery` or `$` directly as a global, through `Ember.$()` or by importing it (`import jQuery from jquery;`) 
* global acceptance test helpers like `find()` or `click()`
* `this.$()` in component tests

Note that this also applies to all addons that your app uses, so make sure these support to be used without jQuery!