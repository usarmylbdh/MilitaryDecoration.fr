# Registre US Military Police 1944 — mise en ligne (GitHub + Firebase)

Ce dossier contient l'application complète : effectifs et présences, promotions, décorations avec niveaux.
Les données sont stockées dans **Firebase** (gratuit) et la page est hébergée sur **GitHub Pages**.

- **Tout le monde peut consulter** le registre, sans compte.
- **Toi et ton état-major** modifiez après connexion avec un compte Google.
- L'application est **installable** sur téléphone et PC (icône MP, plein écran).

Durée : environ 15 minutes.

---

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | L'application |
| `firebase-config.js` | **À remplir** avec la configuration de ton projet Firebase (étape 3) |
| `firestore.rules` | Règles de sécurité **à coller dans Firebase** (étape 2), avec ton adresse Gmail |
| `donnees-initiales.json` | Tes 3 effectifs actuels + le catalogue des 13 décorations, importables en un clic |
| `manifest.webmanifest`, `sw.js`, `icons/` | Ce qui rend l'application installable |

---

## Étape 1 — Créer le projet Firebase

1. Va sur **https://console.firebase.google.com** et connecte-toi avec ton compte Google.
2. **Créer un projet** → nom : `registre-mp` (ou ce que tu veux).
3. Google Analytics : tu peux le **désactiver**, il ne sert à rien ici.
4. Attends la création, puis clique sur **Continuer**.

## Étape 2 — Créer la base de données (Firestore)

1. Dans le menu de gauche : **Créer (Build) → Firestore Database → Créer une base de données**.
2. Emplacement : choisis une région **Europe** (par exemple `eur3` ou `europe-west`).
3. Mode : **production**.
4. Ouvre l'onglet **Règles**, efface tout, puis colle le contenu du fichier `firestore.rules`.
5. Dans le texte collé, remplace `TON_ADRESSE@gmail.com` par **ton adresse Gmail, en minuscules**.
6. Clique sur **Publier**.

> C'est cette adresse qui fait de toi le chef : toi seul pourras ajouter ou retirer des membres de l'état-major.

## Étape 3 — Activer la connexion Google et récupérer la configuration

1. Menu de gauche : **Créer (Build) → Authentication → Commencer**.
2. Onglet **Mode de connexion (Sign-in method)** → **Google** → **Activer**, choisis ton e-mail d'assistance, puis **Enregistrer**.
3. Clique sur la **roue dentée** en haut à gauche → **Paramètres du projet**.
4. En bas, section **Vos applications** → icône **`</>`** (Web) → nom : `registre-mp` → **Enregistrer l'application** (ne coche pas « Firebase Hosting »).
5. Firebase affiche un bloc `const firebaseConfig = { ... }`. Copie **uniquement ce qu'il y a entre les accolades**.
6. Ouvre `firebase-config.js` et remplace le contenu entre les accolades par ce que tu as copié.

> Ces clés ne sont pas secrètes, c'est normal qu'elles soient visibles sur GitHub. Ce sont les règles de l'étape 2 qui protègent le registre.

## Étape 4 — Autoriser ton site à utiliser la connexion Google

1. **Authentication → Paramètres (Settings) → Domaines autorisés → Ajouter un domaine**.
2. Ajoute : `usarmylbdh.github.io`
3. Si ton site a un nom de domaine personnalisé (par ex. `militarydecoration.fr`), ajoute-le aussi.

Sans cette étape, le bouton « Connexion état-major » affiche « Domaine non autorisé ».

## Étape 5 — Mettre le dossier sur GitHub

1. Dans ton dépôt **MilitaryDecoration.fr**, crée un dossier `registre-mp`.
2. Envoie dedans **tout le contenu de ce dossier** (avec le sous-dossier `icons`) : sur github.com, ouvre le dossier puis **Add file → Upload files**, glisse les fichiers, puis **Commit changes**.
3. Attends 1 à 2 minutes que GitHub Pages se mette à jour.
4. Ton registre est en ligne à l'adresse :
   `https://usarmylbdh.github.io/MilitaryDecoration.fr/registre-mp/`
   (ou `https://ton-domaine/registre-mp/` si tu as un domaine personnalisé).

## Étape 6 — Premier lancement

1. Ouvre l'adresse du registre et clique sur **Connexion état-major** (en haut à droite). Connecte-toi avec **la même adresse Gmail** que dans les règles.
2. Le registre est vide : clique sur **Importer les données de départ**. Tes effectifs et les 13 décorations apparaissent.
3. Clique sur **État-major** pour ajouter les adresses Gmail de tes officiers. Ils pourront modifier dès leur prochaine connexion.
4. Partage le lien sur ton Discord : tout le monde peut consulter, sans compte.

---

## Installer l'application

- **Téléphone Android (Chrome)** : ouvre le lien → menu ⋮ → **Ajouter à l'écran d'accueil** / **Installer l'application**.
- **iPhone (Safari)** : bouton Partager → **Sur l'écran d'accueil**.
- **PC (Chrome ou Edge)** : icône **Installer** dans la barre d'adresse.

L'icône MP apparaît et le registre s'ouvre en plein écran. Les mises à jour arrivent toutes seules.

---

## À savoir

- **Gratuit** : le plan gratuit de Firebase (Spark) suffit très largement pour un registre de serveur RP. Pas besoin de carte bancaire.
- **Sauvegarde** : dans **État-major → Exporter une sauvegarde**, tu télécharges tout le registre en JSON. Tu peux le réimporter avec **Importer un fichier…**.
- **Pour modifier la liste de l'état-major**, il faut être connecté avec l'adresse du chef (celle des règles). Les autres membres de l'état-major voient la liste mais ne peuvent pas la changer.
- **Problème ?**
  - « Registre inaccessible » → `firebase-config.js` n'est pas rempli ou contient une erreur.
  - « Domaine non autorisé » → étape 4.
  - Connecté mais « consultation seule » → ton adresse n'est pas celle des règles, ou n'est pas dans la liste de l'état-major.
