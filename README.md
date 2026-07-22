# Stratified standardized household consumption profiles from HCES 2022-23

## Dataset scope

This deposit contains household-level, within-stratum standardized consumption-expenditure profiles derived from Level 14, Sections A1, B1 and C1, of India's Household Consumption Expenditure Survey (HCES) 2022-23 (https://microdata.gov.in/NADA/index.php/catalog/224).

The dataset contains 261,746 households and 42 consumption categories. Each household is represented by a study-specific household identifier (`hhid`) and 42 z-score variables. Z-scores were calculated separately within each second-stage stratum.
The files are derived from the official HCES 2022-23 unit-level data. They are not a replacement for the official source microdata.

## Files

| File | Description | No. of Households |

| `SSS11_2023_level_14_hh_zscores_pspp.csv` | Rural SSS 1 z-score dataset | 5,730 |

| `SSS12_2023_level_14_hh_zscores_pspp.csv` | Rural SSS 2 z-score dataset | 17,074 |

| `SSS13_2023_level_14_hh_zscores_pspp.csv` | Rural SSS 3 z-score dataset | 132,210 |

| `SSS21_2023_level_14_hh_zscores_pspp.csv` | Urban SSS 1 z-score dataset | 4,260 |

| `SSS22_2023_level_14_hh_zscores_pspp.csv` | Urban SSS 2 z-score dataset | 10,420 |

| `SSS23_2023_level_14_hh_zscores_pspp.csv` | Urban SSS 3 z-score dataset | 92,052 |

| Corresponding `.sav` files | PSPP/SPSS versions of each CSV | Same as CSV |

| `b_a1b1c1_item_code.csv` | Codebook for the 42 consumption variables | — |

| `strata_definition.csv` | Definitions of rural and urban SSS groups | — |

| `SSS*_Queries.txt` | MySQL processing pipelines | — |

| `sss*_unpivot_stats_summary.csv` | Pre-standardization means and standard deviations | — |

| `sss*_comm_output.csv` | Principal-component communalities outputs | — |



## Variables and codebook

### Variables
Each data file has one `hhid` column and 42 variables named `z_<item code>`. The `z_` prefix denotes a within stratum z-score. The item code definitions are provided in `b_a1b1c1_item_code.csv`; for example, `z_129` is cereals and `z_169` is milk and milk products.
A z-score is calculated as: z = (household expenditure - stratum mean) / stratum standard deviation

## Strata
The first digit identifies sector: 1 = rural; 2 = urban.
The second digit identifies second-stage stratum: 1, 2, or 3.
Rural SSS 1: households above the State/UT-specific upper land-possession threshold.
Rural SSS 2: households between the State/UT-specific lower and upper land-possession thresholds.
Rural SSS 3: remaining rural households.
Urban SSS 1: households owning non-commercial four-wheeler vehicle(s) with combined purchase value above Rs. 10 lakh.
Urban SSS 2: households owning non-commercial four-wheeler vehicle(s) with combined purchase value at or below Rs. 10 lakh.
Urban SSS 3: remaining urban households.

## Software

The pipeline was executed using MySQL [Ver 8.4.7] on Windows [Version 10.0.26100.8457].
PSPP [2.1.1-g557d00] was used to create and inspect the SAV files.

## Reproduction procedure

1. Execute the procedure detailed in /codebook/setup_procedures_queries.txt

2. Execute /codebook/SSS11_Queries.txt, /codebook/SSS12_Queries.txt, /codebook/SSS13_Queries.txt, /codebook/SSS21_Queries.txt, /codebook/SSS22_Queries.txt, and /codebook/SSS23_Queries.txt.

3. Export the six resulting z-score tables as CSV.

4. Open or import each CSV into PSPP to create the matching SAV file.

## Technical validation

1. The six output files contain 261,746 households in total.
2. Every output has one unique `hhid` (household id) per row.
3. Each output contains 42 standardized consumption variables.
4. No z-score values are missing.
5. Within each stratum, each z-score variable has mean approximately 0 and population standard deviation approximately 1.
6. The pre-standardization means and standard deviations are supplied in `sss*_unpivot_stats_summary.csv`.
7. The exact MySQL check queries and their outputs are provided in the `/validation` folder.


