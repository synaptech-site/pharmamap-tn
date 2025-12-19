# PharmaMap TN (100% gratuit)

Ce projet est une web-app simple (FR) pour la Tunisie :
- Carte OpenStreetMap + Leaflet
- Pharmacies proches de vous (géolocalisation)
- Filtre "Ouvert maintenant"
- Filtre "De garde aujourd’hui"
- Bouton itinéraire (Option A) : ouvre Google Maps / Apple Plans
- Interface "Espace pharmacie" pour modifier horaires / garde / exceptions

## 1) Créer la Google Sheet
Crée un Google Sheet (ex: `PharmaMap_TN`) avec un onglet `pharmacies` et ces colonnes (ligne 1) :

id | nom | adresse | ville | lat | lng | telephone | horaires_json | garde_json | maj_speciale_json | auth_code | updated_at

Exemples JSON :
- horaires_json : {"lun":[{"de":"08:00","a":"18:00"}],"dim":[]}
- garde_json : [{"date":"2025-12-20","de":"18:00","a":"08:00"}]
- maj_speciale_json : [{"date":"2025-01-01","ferme":true}]

## 2) Créer l'API Google Apps Script
Dans la sheet : Extensions → Apps Script
- Colle le contenu de `apps_script/Code.gs`
- Déployer → Nouveau déploiement → Application Web
  - Exécuter en tant que : Moi
  - Accès : Tout le monde
Copie l'URL fournie (ex: https://script.google.com/macros/s/XXXXX/exec)

## 3) Configurer le front
Dans `index.html` et `pharmacy.html`, remplace :
REPLACE_WITH_YOUR_APPS_SCRIPT_URL
par l'URL Apps Script.

## 4) Déployer sur GitHub Pages
- Push le dossier sur GitHub
- Settings → Pages → Deploy from branch (main / root)
- Ton site sera : https://TON-USER.github.io/NOM-REPO/

## 5) Ajouter des pharmacies
Remplis des lignes dans la sheet (lat/lng obligatoires).

## Notes
- 100% gratuit (OSM + GitHub Pages + Google Sheets/Apps Script)
- Pour rester gratuit : n’ajoute pas de géocodage automatique (adresse→coordonnées) au début.
