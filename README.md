# Tidyverse Extended

An opinionated Docker image based on [`rocker/tidyverse`](https://rocker-project.org/) with an extended set of R packages for data analysis, visualization, and publishing.

## Overview

This project provides a reproducible, containerized R environment with a curated collection of packages commonly used in data science workflows. It extends the official Rocker tidyverse image with additional system dependencies, CLI tools, and R packages tailored for advanced analytics and interactive analysis.

## Features

- **Base Image**: [rocker/tidyverse:4.5.2](https://rocker-project.org/use/tidyverse/) - includes R, RStudio, and tidyverse packages
- **Extended Package Set**: 50+ additional R packages for statistics, forecasting, parallel computing, and more
- **System Dependencies**: Pre-installed system libraries for spatial data (GDAL), scientific computing (GSL), parallel processing (OpenMPI), and other specialized tools
- **CLI Tools**: 
  - [rclone](https://rclone.org/) - cloud storage integration
  - [air](https://github.com/posit-dev/air) - code reloading tool
- **Development Tools**: Git, SSH, zsh, vim, emacs, tmux, screen
- **Configured RStudio**: Pre-configured RStudio preferences for consistent development experience

## Package Categories

The extended environment includes packages for:

- **Data Manipulation**: collapse, data.table, dbplyr
- **Forecasting & Time Series**: forecast, BTYD, BTYDplus, clock
- **Parallel Computing**: future, furrr, doParallel, doMC
- **Database Connectivity**: DBI, duckdb, duckdbfs
- **Visualization**: ggplot2, cowplot, ggh4x, flextable
- **Statistical Modeling**: caret, lme4, mgcv, and others
- **Reproducibility**: renv, targets, packrat
- **And many more...**

See [DESCRIPTION](DESCRIPTION) for the complete list of packages.

## Quick Start

### Build the Docker Image

```bash
docker build -t tidyverse-extended .
```

### Run a Container

Interactive RStudio session:

```bash
docker run -d \
  -p 8787:8787 \
  -e PASSWORD=yourpassword \
  tidyverse-extended
```

Then navigate to `http://localhost:8787` with username `rstudio` and your chosen password.

Or, start an R console:

```bash
docker run -it tidyverse-extended R
```

### Mount Volumes

To work with local files:

```bash
docker run -it \
  -v /path/to/your/project:/home/rstudio/project \
  tidyverse-extended
```

## Files

- **[DESCRIPTION](DESCRIPTION)** - R package manifest specifying all dependencies
- **[Dockerfile](Dockerfile)** - Container build configuration
- **[apt-packages.txt](apt-packages.txt)** - System package dependencies
- **[rstudio-prefs.json](rstudio-prefs.json)** - RStudio IDE configuration

## Author

[Ramnath Vaidyanathan](https://github.com/ramnathv)

## License

MIT

## Notes

- This image is not intended for CRAN submission
- It is optimized for interactive analysis and development workflows
- The Dockerfile uses a multi-layer cache strategy to minimize rebuild times when R packages change
