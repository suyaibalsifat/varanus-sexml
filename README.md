# VaranusSexML

Open workflow for uncertainty-aware machine-learning sexing of the Asian water monitor
(*Varanus salvator*) from morphometrics. It accompanies the manuscript
"An open workflow for uncertainty-aware machine-learning sexing of a harvested monitor lizard from morphometrics"
(Suyaib Al Sifat, Department of Computer Science and Engineering, Southeast University, Dhaka).

## Contents
| Path | Description |
|---|---|
| `varanus_sex_prediction.ipynb` | Single notebook that regenerates every table and figure of the paper |
| `data/Varanus_salvator_morphology_sex_prediction__19_Features_.csv` | Public dataset (see Data and attribution) |
| `results/figures`, `results/tables` | Figures (PNG/PDF) and tables (CSV) produced by the full run |
| `results/results_summary.json` | Headline numbers and software versions of the full run |
| `results/field_model_card.json` | Model card of the fitted two-measurement field model (BTC, thigh circumference); the notebook regenerates `field_model.joblib` |
| `requirements.txt` | Python dependencies (versions used for the paper are pinned where they matter) |

## How to run
1. `pip install -r requirements.txt`
2. Open `varanus_sex_prediction.ipynb` (Jupyter, Colab or Kaggle). Put the CSV next to the notebook or set the environment variable `VARANUS_CSV`.
3. `FAST = False` (default in this repository) runs the full analysis (10 x 5-fold nested cross-validation, 17 models). Set `FAST = True` for a quick smoke test (about ten minutes on one CPU core).
4. Outputs are written to `paper_assets/`; intermediate nested-CV results are cached in `paper_assets/cache`, so an interrupted run resumes.

Random seed: 42. No GPU required.

## Data and attribution
The dataset is Alymann, A. A. (2023), *Varanus salvator* morphology sex prediction (19 Features), Figshare,
https://doi.org/10.6084/m9.figshare.24558595 (CC BY 4.0), described in Alymann et al. (2024), Scientific Data 11, 337,
https://doi.org/10.1038/s41597-024-03172-9. A copy is included here under the CC BY 4.0 licence; please cite the original.

## Field model
The field model (model card in `results/field_model_card.json`, model file `field_model.joblib` written by the notebook) was fitted on animals of at most 5 kg from oil palm plantations in Perak, Malaysia, and has not been validated externally.
The model file is a pickled scikit-learn pipeline: load only files you trust.

## Licence
Code: MIT (see `LICENSE`). Data: CC BY 4.0 (original authors).

## Citation
See `CITATION.cff`.
