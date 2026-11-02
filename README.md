# Uber_trip_analysis
EDA & ML of NYC Uber Trips

# Uber NYC Pickup Hotspots — K-Means vs DBSCAN

**Python · Pandas · Scikit-learn · Plotly · Exploratory Data Analysis · Geospatial Clustering**

> Historical case study using New York City Uber pickups (April–September 2014). This is an analysis of completed pickups, not a real-time forecasting or dispatch system.

## English

### Business problem
Where are the strongest historical concentrations of Uber pickups in NYC, and how do they vary over time? Could clustering provide understandable zones for drivers to explore before peak pickup periods?

### Data
- Six monthly 2014 Uber pickup CSVs (April–September).
- **4,534,327** records loaded; **4,507,763** retained after geographic filtering (0.59% excluded).
- Features analyzed: latitude, longitude, month, weekday, hour.
- Original public dataset: [FiveThirtyEight / NYC TLC FOIL response](https://github.com/fivethirtyeight/uber-tlc-foil-response).

### Approach
1. Parse and consolidate six monthly data extracts.
2. Inspect data quality and explore monthly, daily and hourly patterns.
3. Visualize historical pickups on maps and day–hour heatmaps.
4. Compare K-Means cluster counts using inertia and silhouette scores.
5. Retain **8 K-Means clusters** as an interpretable operational breakdown; examine day-specific zones.
6. Compare K-Means with DBSCAN on the Friday 6 p.m. subset.

### Selected findings
| Metric | Recorded result |
|---|---:|
| Friday 6 p.m. pickups in the six-month dataset | **54,485** |
| K-Means clusters retained | **8** |
| DBSCAN clusters found | **7** |
| DBSCAN points classified as noise | **4.8%** |
| K-Means silhouette in final comparison | **0.430** |
| DBSCAN silhouette in final comparison | **0.156** |

**Interpretation:** K-Means provides a fixed number of simple regions for presentation. DBSCAN reveals dense groupings and atypical points. The notebook retains K-Means for interpretability. The silhouette comparison is not strictly like-for-like: DBSCAN's score excludes noise points.

### Reproduce the analysis
1. Clone the repository and install packages:
   ```bash
   python -m pip install -r requirements.txt
   ```
2. Obtain the six 2014 Uber pickup CSVs (`uber-raw-data-apr14.csv` through `uber-raw-data-sep14.csv`) from the source above.
3. Compress the six CSVs into an archive named **`uber-trip-data.zip`** (the archive may contain a parent folder) and place it in **`data/raw/`**.
4. Open [the notebook](notebook/Uber_hotzones_clustering_Schuyler_Gilmer_Goncalves.ipynb) and select an appropriate Python environment.
5. Run all cells. The notebook reads the six 2014 CSV files directly from the local ZIP.

The raw dataset and ZIP are **intentionally excluded** from version control due to size. Map visualizations may require network access to load map tiles.

### Limitations
- The data are from 2014 and describe **completed pickups**, not unfulfilled demand or real-time conditions.
- Clustering depends on sampling, geographic representation and algorithm parameters.
- There is no assessment of traffic, driver availability, cancellations, weather or economic benefit.
- This project is an analytical prototype, not an operational driver recommendation tool.

---

## Français

### Problématique métier
Où se concentrent historiquement les prises en charge Uber à New York et comment ces concentrations varient-elles selon les jours et les heures ? Le clustering peut-il fournir des zones faciles à interpréter pour les chauffeurs ?

### Données
- Six fichiers mensuels de prises en charge Uber, d'avril à septembre 2014.
- **4 534 327** trajets chargés et **4 507 763** conservés après filtrage géographique (0,59 % exclus).
- Variables : latitude, longitude, mois, jour de semaine, heure.
- Source : [FiveThirtyEight / NYC TLC](https://github.com/fivethirtyeight/uber-tlc-foil-response).

### Méthodologie
1. Chargement et consolidation des six CSV.
2. Contrôle qualité et analyse exploratoire temporelle.
3. Cartes de prises en charge et matrice jour–heure.
4. Évaluation de plusieurs valeurs de K avec inertie et score de silhouette.
5. Choix de **8 clusters K-Means** pour un découpage plus fin et lisible.
6. Comparaison avec DBSCAN sur le créneau du vendredi à 18 h.

### Résultats clés
- **54 485** prises en charge le vendredi à 18 h sur la période étudiée.
- **8 zones K-Means** retenues ; **7 clusters DBSCAN** détectés.
- **4,8 %** de bruit avec DBSCAN.
- Scores de silhouette comparatifs : **0,430** pour K-Means et **0,156** pour DBSCAN. Le score de DBSCAN exclut les points de bruit : la comparaison comporte donc une limite méthodologique.

### Exécution
1. Installer les bibliothèques listées dans `requirements.txt`.
2. Télécharger les six CSV Uber de 2014 depuis la source indiquée.
3. Les regrouper dans une archive `uber-trip-data.zip` et placer celle-ci dans `data/raw/`.
4. Ouvrir le [notebook](notebook/Uber_hotzones_clustering_Schuyler_Gilmer_Goncalves.ipynb), sélectionner l'environnement Python puis exécuter toutes les cellules.

Le jeu de données brut est volontairement exclu de Git afin de garder un dépôt léger.

### Limites
Il s'agit de données historiques de courses réalisées, non d'une mesure directe de demandes non satisfaites. Le projet n'évalue ni la disponibilité des chauffeurs, ni le trafic, ni la rentabilité des recommandations. Les zones identifiées sont exploratoires et ne constituent pas des instructions de conduite en temps réel.
