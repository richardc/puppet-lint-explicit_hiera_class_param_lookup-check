# puppet-lint explicit Hiera class parameter lookup check

Extends puppet-lint to ensure there are no explicit calls to hiera()
in the class parameters.

In our code base we would rather have a class lookup values for its
parameters using Puppets automatic data binding functionality rather than
scatter a number of direct, unpredictably name spaced, hiera calls
throughout our manifests. This puppet-lint plugin helps us with that goal by
finding any explicit `hiera` calls in a classes parameter section.

    class no_explicit_lookups (
      $my_content = hiera('my::nested::key', 'baz')
    ) {
      file { '/tmp/foo':
        content => $my_content,
      }
    }

## Installation

To use this plugin add the following line to your Gemfile

    gem 'puppet-lint-explicit_hiera_class_param_lookup-check'

and then run `bundle install`.

## Usage

This plugin provides a new check to `puppet-lint`.

    explicit hiera() lookup of my::sample::key

#### Author

[Dean Wilson](http://www.unixdaemon.net)

### License

 * MIT
