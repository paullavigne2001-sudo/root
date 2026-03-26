# MultiPlanet PWA 🚀

Jeu éducatif de tables de multiplication — packagé en PWA publiable sur le Play Store.

---

## 📁 Structure du projet

```
multiplanet-pwa/
├── index.html        ← Le jeu (ton fichier original + balises PWA)
├── manifest.json     ← Identité de l'app (nom, icônes, couleurs)
├── sw.js             ← Service Worker (mode hors-ligne)
├── .nojekyll         ← Nécessaire pour GitHub Pages
├── icons/
│   ├── icon-72.png   ← Icônes app (à remplacer par tes vraies icônes)
│   ├── icon-96.png
│   ├── icon-128.png
│   ├── icon-144.png
│   ├── icon-152.png
│   ├── icon-192.png  ← Utilisé comme apple-touch-icon
│   ├── icon-384.png
│   ├── icon-512.png  ← Icône principale Play Store
│   ├── screenshot-wide.png   ← Capture d'écran paysage (à remplacer)
│   └── screenshot-narrow.png ← Capture d'écran portrait (à remplacer)
└── README.md
```

---

## 🚀 Étape 1 — Déployer sur GitHub Pages

### 1. Créer le repo GitHub
1. Va sur [github.com](https://github.com) → **New repository**
2. Nom : `multiplanet` (ou ce que tu veux)
3. Visibilité : **Public** ← obligatoire pour GitHub Pages gratuit
4. Ne pas initialiser avec README (on a déjà les fichiers)

### 2. Pousser les fichiers
```bash
cd multiplanet-pwa
git init
git add .
git commit -m "Initial PWA"
git remote add origin https://github.com/TON_USERNAME/multiplanet.git
git push -u origin main
```

### 3. Activer GitHub Pages
1. Dans ton repo → **Settings** → **Pages**
2. Source : **Deploy from a branch**
3. Branch : `main` / `/ (root)`
4. Clic **Save**

✅ Ton app sera disponible sur : `https://TON_USERNAME.github.io/multiplanet/`

### ⚠️ Important : mettre à jour le manifest.json
Si ton repo s'appelle `multiplanet`, change le `start_url` dans `manifest.json` :
```json
"start_url": "/multiplanet/",
"scope": "/multiplanet/"
```
Et dans `sw.js`, adapte les chemins si besoin.

---

## 📱 Étape 2 — Générer l'APK avec PWABuilder

1. Va sur **[pwabuilder.com](https://www.pwabuilder.com)**
2. Colle ton URL GitHub Pages : `https://TON_USERNAME.github.io/multiplanet/`
3. Clique **Start** → attends l'analyse
4. Onglet **Android** → **Generate Package**
5. Remplis :
   - Package ID : `com.tetra_chroma.multiplanet`
   - App version : `1`
   - Version name : `1.0.0`
6. Télécharge le `.zip` contenant l'APK

### Installer l'APK sur ton téléphone
1. Active **"Sources inconnues"** sur Android :
   - Paramètres → Sécurité → Installer des apps inconnues
2. Transfère le fichier `.apk` sur ton téléphone (USB ou email)
3. Ouvre-le et installe

---

## 🏪 Étape 3 — Publier sur le Play Store

### Prérequis
- Compte Google Play Console ([play.google.com/console](https://play.google.com/console)) — frais uniques de 25 $
- Vraies icônes PNG (voir section ci-dessous)
- Captures d'écran réelles du jeu

### Avec PWABuilder → Play Store
1. Depuis PWABuilder, onglet **Android** → **Publish to Play Store**
   - Ou utilise le package **Android (TWA)** généré
2. Dans Play Console → **Créer une app**
3. Upload le `.aab` (Android App Bundle) généré par PWABuilder
4. Remplis les métadonnées, captures d'écran, politique de confidentialité
5. Soumets pour review (délai : 1–7 jours)

---

## 🎨 Remplacer les icônes placeholder

Les icônes actuelles sont générées automatiquement. Pour les remplacer :

### Option A — Site en ligne (recommandé)
1. Va sur [realfavicongenerator.net](https://realfavicongenerator.net)
2. Upload ton image source (au moins 512×512 px)
3. Télécharge le pack → remplace les fichiers dans `/icons/`

### Option B — PWABuilder
PWABuilder peut aussi générer des icônes depuis une image source.

### Tailles requises
| Fichier | Utilisation |
|---------|-------------|
| icon-192.png | Android homescreen, apple-touch-icon |
| icon-512.png | Play Store, splash screen |
| icon-144.png | Chrome / Edge |
| Autres | Compatibilité étendue |

---

## 🔒 Politique de confidentialité (obligatoire Play Store)

Le Play Store exige une URL de politique de confidentialité.
Crée une page simple `privacy.html` dans ton repo avec :
- Ce que l'app collecte (ici : rien, tout est en localStorage)
- Conformité COPPA (app pour enfants)

---

## ✅ Checklist avant publication Play Store

- [ ] Vraies icônes (512×512 minimum)
- [ ] Captures d'écran réelles (min. 2)
- [ ] URL de politique de confidentialité
- [ ] Testé sur vrai appareil Android
- [ ] `start_url` et `scope` corrects dans manifest.json
- [ ] Service Worker fonctionne (test dans Chrome DevTools → Application)
