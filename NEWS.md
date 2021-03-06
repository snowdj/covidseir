# covidseir

# covidseir 0.0.0.9002

* `forecast_seir()` has been renamed to `project_seir()`.

* `plot_projection()` and `tidy_sier()` have been added. See examples
  in `project_seir()`.

# covidseir 0.0.0.9001

* `fit_seir()` now allows for multiple estimated blocks (segments) of fractions
  of normal contacts (f) through time. The f values are indexed by `s` for
  segment. I.e., `f_s`. They currently all share the same prior.

* `fit_seir()` now allows for estimated blocks (segments) of sampling fractions
  for the first data type. The intent is that this is used for the reported
  cases in which the sampling fraction is unknown and can be estimated if
  another type of case data (e.g., hospitalizations) is included with a much
  better-known fraction of positive cases represented.

* Forecasting is now done with the same Stan model as the fitting via
  `forecast_seir()`. This eliminates approximately half of the code base (the
  R reimplementation), means that all of the model fitting options also work
  with the forecasting, makes it much easier to add functionality and harder to
  make mistakes, and generates much faster forecasts. The f values are
  represented as a vector and so can represent any desired pattern.

* `fit_seir()` now allows for NA values in the case data. These are omitted
  from the likelihood. If no NA values are present then a vectorized likelihood
  is used, which is slightly faster.

* The output from `forecast_seir()` includes helpful metadata such as which
  time steps are forecasted and which time steps use a fixed (vs. estimated)
  f value.

* `fit_seir()` now uses a time step of 0.2 by default, which seems to give
  similar results with faster fits.

* Fixed f values can be set to start on an arbitrary date in the future.

* `project_fit()` has been renamed to `forecast_seir()`.

* Arguments to the functions and within the Stan model have been standardized
  and cleaned up.

* Added continuous integration testing via Travis
  <https://travis-ci.org/github/seananderson/covidseir/builds>.

* Added many examples to `fit_seir()` and `forecast_seir()`. Removed the
  vignette for now as it was out of date and is currently replaced by those
  examples.

* The previous plotting function has been removed for now. It was bloated and
  included many dependencies and wasn't working with all options. A simpler
  version will likely be added back later.

* Documentation has been cleaned up throughout.


