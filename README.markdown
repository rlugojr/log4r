# log4r [![Travis-CI Build Status](https://travis-ci.org/johnmyleswhite/log4r.png?branch=master)](https://travis-ci.org/johnmyleswhite/log4r) [![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/github/johnmyleswhite/log4r?branch=master)](https://ci.appveyor.com/project/johnmyleswhite/log4r)

## Introduction
The log4r package is meant to provide a clean, lightweight object-oriented approach to logging in R based roughly on the widely emulated log4j API. The example code below shows how the logger is used in practice to print output to a simple plaintext log file.

## Installation
- Stable CRAN version:
    ```r
    install.packages("log4r")
    ```

- Development version on GitHub:

    ```r
    devtools::install_github("johnmyleswhite/log4r")
    ```

## Example Code
```r
# Import the log4r package.
library('log4r')

# Create a new logger object with create.logger().
logger <- create.logger()

# Set the logger's file output: currently only allows flat files.
logfile(logger) <- file.path('base.log')

# Set the current level of the logger.
level(logger) <- "INFO"

# Try logging messages at different priority levels.
debug(logger, 'A Debugging Message') # Won't print anything
info(logger, 'An Info Message')
warn(logger, 'A Warning Message')
error(logger, 'An Error Message')
fatal(logger, 'A Fatal Error Message')
```

## The log4r Priority Levels
`log4r` supports five priority levels. In order from lowest to highest
priority, they are:

* `"DEBUG"`
* `"INFO"`
* `"WARN"`
* `"ERROR"`
* `"FATAL"`

## Keep in Mind
* Calling `logfile(logger) <- file.path('logs', 'my.log')` will fail if the `logs` directory does not already exist. In general, no effort is made to create non-existent directories.
* Only messages at or above the current priority level are logged. Messages below this level are simply ignored.
* Using the internal priority level constants using the `:::` notation is
  deprecated, but no warning is given.  It is safer to simply use strings
  or numeric constants.

## Future Changes
* `create.logger()` will become a singleton method to insure log integrity.
* Future versions of log4r will respect the format attribute of logger objects.
