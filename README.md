# Initialize
add Rtools path & phantomJS to test the shiny app
```r
Sys.setenv(PATH = paste(
  Sys.getenv("PATH"), 
  "C:/rtools40/usr/bin", sep = ";"), 
  "C:/PhantomJS"
)
```

# Create skeleton of R pkg
```r
usethis::create_package("R.pkg")
```
add a licence file if needed
```r
usethis::use_gpl3_license()
```
use renv to manage dependencies
```r
renv::init(bare = TRUE)
```
sometimes renv doesn't want to install pkg, this should fix the problem:
```
Sys.setenv(RENV_DOWNLOAD_FILE_METHOD = "libcurl")
```
move into the R pkg directory & create the test directory
```r
setwd("R.pkg")
usethis::use_testthat()
```
if some C++ code will be used:
```r
Rcpp::use_rcpp()
```
