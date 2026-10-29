# Global agreement masks regional divergence in soil respiration

Code and data products for the analysis of global soil respiration (Rs) estimates
from data-driven models (DDMs) and process-based models (PBMs).

**Manuscript.** Ren, X., Jian, J., Li, P., Gu, Y., Zhang, L., Yan, Z., Yang, R.-M.,
He, H., Niu, Z., Ge, R., Wu, Y., Yu, G.-R., Liu, C.-Q., Sitch, S., Vargas, R. &
Bond-Lamberty, B. *Global agreement masks regional divergence in soil respiration.*
(in preparation)

## Repository contents

| Path | Contents |
| --- | --- |
| `RsBias.Rmd` | the complete analysis: all 12 figures and all data products |
| `data/` | inputs; provenance and SHA-256 in `data/input_manifest.csv` |
| `result/*.png` | 12 figures (Figs. 1-4 and extended data) |
| `result/zenodo/` | Zenodo deposit: 3 NetCDF files, 3 metadata CSV tables, the Hashimoto source table and the supplementary material |

## Data availability

The code is on GitHub; the data are on Zenodo
([10.5281/zenodo.23333448](https://doi.org/10.5281/zenodo.23333448)), which holds both
the products in `result/zenodo/` and the input data in `data/`. Please cite the
Zenodo DOI for the data.

## Requirements

R 4.4.2 with `terra`, `sf`, `dplyr`, `tidyr`, `ggplot2`, `patchwork`, `ggrepel`,
`readxl`, `ggpubr`, `gghalves`, `ggh4x`, `ggtext`, `glmnet`, `ncdf4`, `scales`,
`showtext`, `rmarkdown`, `knitr`. The first chunk lists any missing packages.

## Run

```r
rmarkdown::render("RsBias.Rmd", output_dir = "result",
                  envir = new.env(parent = globalenv()), encoding = "UTF-8")
```

Figures are written to `result/`, the NetCDF products to `result/zenodo/`. The
workflow takes about 10-15 minutes and ~8 GB of RAM (the `stell` and `Warner`
rasters are resampled to the common 0.5-degree grid). The Rmd caps the GDAL
block cache before `terra` is loaded, so that step cannot exhaust memory.

## Citation

```bibtex
@article{ren_global_soil_respiration,
  title   = {Global agreement masks regional divergence in soil respiration},
  author  = {Ren, Xiaohua and Jian, Jinshi and Li, Pan and Gu, Yuning and
             Zhang, Li and Yan, Zhifeng and Yang, Ren-Min and He, Honglin and
             Niu, Zhongen and Ge, Rong and Wu, Yu and Yu, Gui-Rui and
             Liu, Cong-Qiang and Sitch, Stephen and Vargas, Rodrigo and
             Bond-Lamberty, Ben},
  journal = {Manuscript in preparation},
  year    = {2026}
}
```

Code is released under the MIT License (see `LICENSE`). The input data and the
products in `result/zenodo/` remain subject to the terms of their original sources
(SRDB-V5, TRENDY v13, CRU TS, MODIS, FLUXCOM, ERA5, ISRIC SoilGrids, UNEP aridity
database, and the individual DDM publications).