# 🐼 Séance 3 — Pandas : charger, inspecter, nettoyer

_Master IA‑GI · Python pour les sciences de données · FPK / USMS_

Ce dépôt contient **mon TP de la séance 3**. Deux notebooks, à faire **dans l'ordre** :

| | Notebook | Durée | Ouvrir dans Colab |
|---|---|---|---|
| **1** | **Partie 1 · Pratiquer** : 26 exercices en 5 parties, de votre première Series jusqu'au nettoyage | environ 2 h | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yelallioui/python-for-ds-s03/blob/main/tp-seance-03.ipynb) |
| **2** | **Partie 2 · Mini‑projet Titanic** : charger, auditer, nettoyer en décidant, puis écrire un tableau propre et son journal | environ 45 min | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yelallioui/python-for-ds-s03/blob/main/mini-projet-03/mini-projet-03.ipynb) |

---

## 🚀 Pour commencer : 3 étapes

### Étape 1 · Ouvrir le notebook
Cliquez sur **Open in Colab** (tableau ci‑dessus). Connectez‑vous avec votre **compte Google** si Colab le demande. Le notebook s'ouvre dans **votre** session Colab.

### Étape 2 · Faire votre copie (à ne pas oublier ⚠️)
Colab **ne sauvegarde pas** un notebook ouvert depuis GitHub : si vous fermez l'onglet, **tout est perdu**. Dès l'ouverture :

1. Menu **Fichier ▸ Enregistrer une copie dans Drive**.
2. Une **copie** s'ouvre dans un nouvel onglet : **travaillez dans cette copie**, et fermez l'original.

### Étape 3 · Travailler
- **Remplissez d'abord la cellule 🪪 « Qui êtes‑vous ? »** : votre **nom** et votre **prénom**, entre guillemets. Le contrôle reste ❌ tant qu'elle n'est pas remplie.
- Exécutez les cellules **dans l'ordre** (`Maj + Entrée`).
- Faites chaque exercice en remplaçant les `...` par votre code. Un **✅** ou un **❌** s'affiche sous chaque exercice ; en cas de ❌, ouvrez l'**indice 1**, puis 2, puis 3.
- **Partie 1** : rien d'autre à faire, elle est indépendante.
- **Mini‑projet** : exécutez d'abord la cellule **📁 Étape 0** : elle récupère le dossier du TP, qui contient `titanic.csv` et `s2_titanic.csv` (voir la section suivante).

---

## 📁 Où sont les fichiers dans Colab ?

**Colab n'ouvre que le notebook.** Les autres fichiers du dépôt, comme `titanic.csv`, **restent sur GitHub** : ils ne sont pas dans votre session Colab tant que vous ne les y avez pas amenés.

**`titanic.csv` et `s2_titanic.csv` (mini‑projet)**
1. Exécutez la cellule **Étape 0** (en haut du notebook). Elle télécharge le dossier du TP dans Colab et s'y place.
2. Les deux fichiers sont alors ici : `python-for-ds-s03/mini-projet-03/data/titanic.csv` (le fichier brut) et `python-for-ds-s03/mini-projet-03/data/s2_titanic.csv` (celui que votre mini‑projet de la séance 2 a produit : je vous donne **ma version de référence**, pour que tout le monde parte du même point). Pour les voir, ouvrez le panneau **📁 Fichiers** (icône dossier, à gauche), puis cliquez sur le bouton **↻** pour l'actualiser.
3. Dans votre code, vous les ouvrez avec les chemins **`"data/titanic.csv"`** et **`"data/s2_titanic.csv"`**.

**Si la cellule Étape 0 échoue** (pas de connexion, par exemple), faites‑le à la main :
1. Sur cette page, ouvrez `mini-projet-03/data/`, puis, pour **chacun des deux fichiers**, cliquez sur **Download raw file** (icône de téléchargement).
2. Dans Colab, panneau **📁 Fichiers** : clic droit ▸ **Nouveau dossier**, nommez‑le **`data`**.
3. Glissez‑déposez les deux fichiers dans ce dossier `data`.
4. Dans votre code, ouvrez toujours **`"data/titanic.csv"`** et **`"data/s2_titanic.csv"`**.

**Les fichiers que vous créez** (`fichiers_tp/` en partie 1, `result/` dans le mini‑projet, avec `s3_titanic_propre.csv` et `s3_journal.csv`) apparaissent aussi dans le panneau **📁** (bouton **↻**). Ils sont **temporaires** : ils **disparaissent quand la session Colab se ferme**. Pour garder un fichier : clic droit dessus ▸ **Télécharger**.

**Sur votre ordinateur**, rien de tout cela n'est nécessaire : ouvrez le notebook depuis son dossier (voir plus bas).

---

## 📂 Créer votre dépôt GitHub (pour me rendre votre travail)

![Visibilité : PUBLIC](https://img.shields.io/badge/Visibilit%C3%A9-PUBLIC-brightgreen?style=for-the-badge)

> [!IMPORTANT]
> **Choisissez « Public ».** Colab doit retrouver votre dépôt pour y enregistrer vos notebooks : avec un dépôt privé, il ne le retrouve pas.

> [!WARNING]
> Un dépôt public est **lisible par tout le monde**. N'y écrivez **aucune donnée personnelle** : pas de CNE, pas de mot de passe, pas de numéro de téléphone.

1. Créez un compte sur [github.com](https://github.com) si vous n'en avez pas (gratuit).
2. En haut de **cette page**, cliquez sur le bouton vert **Use this template**, puis **Create a new repository**.
3. **Nom du dépôt** : **`nom-prenom-s03`**, en **minuscules**, **sans accent**, **sans espace** (remplacez‑les par des tirets). Exemple : `benali-sara-s03`.
4. **Visibilité : `Public`**, puis **Create repository**.
5. Dans Colab : **Fichier ▸ Ouvrir le notebook ▸ onglet GitHub**. Saisissez votre identifiant GitHub, puis choisissez votre dépôt et le notebook.
6. Pour sauvegarder : **Fichier ▸ Enregistrer une copie dans GitHub**.

> ⚠️ Les boutons **Open in Colab** de cette page et des notebooks ouvrent toujours **ma version d'origine**. Pour rouvrir **votre** copie, passez par l'onglet **GitHub** de Colab (point 5).

---

## 📤 Me rendre votre travail

Votre dépôt est **public** : je peux le lire sans invitation. **Envoyez‑moi simplement son adresse**, par le moyen indiqué en cours. Elle ressemble à `https://github.com/votre-identifiant/nom-prenom-s03`.

> 💡 Je ne vois que ce qui est **dans votre dépôt**. Quand vous avez terminé une séance de travail, faites **Fichier ▸ Enregistrer une copie dans GitHub** (point 6 de la section précédente) : le notebook est enregistré **avec ses résultats**, les ✅ et les ❌ y restent visibles.

---

## 💻 Sur votre ordinateur (sans Colab)

1. Installez **Python 3** avec Jupyter (le plus simple : [Anaconda](https://www.anaconda.com/download)), ou VS Code avec l'extension Jupyter. Pandas doit être installé : `pip install pandas` (déjà présent avec Anaconda).
2. Téléchargez le dépôt (**Code ▸ Download ZIP**) ou clonez‑le, puis **décompressez‑le** si besoin.
3. Ouvrez chaque notebook **depuis son dossier**, sans le déplacer : la partie 1 depuis le dossier du dépôt, le mini‑projet depuis `mini-projet-03/`.

---

## ❓ En cas de problème

| Message ou symptôme | Cause et remède |
|---|---|
| `FileNotFoundError` sur `data/titanic.csv` ou `data/s2_titanic.csv` | Dans Colab : la cellule **📁 Étape 0** n'a pas été exécutée, ou elle a échoué : relancez‑la, ou suivez « Si la cellule Étape 0 échoue » plus haut. Sur votre ordinateur : le notebook n'est pas ouvert depuis son dossier `mini-projet-03/`. |
| Je ne trouve pas `titanic.csv` ni mes fichiers | Ouvrez le panneau **📁 Fichiers** à gauche et cliquez sur **↻**. Dans Colab, ils sont dans la session, pas dans votre Drive. |
| Mes fichiers ont disparu | Les fichiers d'une session Colab sont temporaires. Téléchargez ceux que vous voulez garder (clic droit ▸ **Télécharger**) avant de fermer. |
| Tout mon notebook a disparu | La copie n'avait pas été faite (étape 2). Recommencez et faites **Fichier ▸ Enregistrer une copie dans Drive** dès l'ouverture. |
| Colab ne trouve pas mon dépôt | Vérifiez que votre dépôt est **Public** (sa page doit s'ouvrir sans être connecté), que vous avez saisi le bon identifiant GitHub, et autorisez Colab à accéder à GitHub si on vous le demande. |
| Je ne vois pas mon travail sur GitHub | Le notebook n'a pas été enregistré **dans votre dépôt** : **Fichier ▸ Enregistrer une copie dans GitHub**. |
| J'ai écrit mon CNE ou une autre donnée personnelle dans le notebook | Supprimez‑la du notebook, puis **supprimez votre dépôt** (**Settings ▸ General ▸ Danger Zone ▸ Delete this repository**) et recréez‑le depuis le modèle : GitHub garde l'historique des anciennes versions. |
| Une cellule affiche `NameError` | Une cellule précédente n'a pas été exécutée : exécutez les cellules **dans l'ordre**, depuis le début. |
| Un ❌ qui ne part pas | Lisez les indices 1, 2, 3 de l'exercice, puis affichez vos variables avec `print`. |

---

## 🗂️ Contenu du dépôt

```
tp-seance-03.ipynb              Partie 1 : 26 exercices en 5 parties
mini-projet-03/
  mini-projet-03.ipynb          Partie 2 : mini-projet Titanic
  data/titanic.csv              le fichier brut
  data/s2_titanic.csv           le résultat de la séance 2 (version de référence)
```

Le dossier `result/` est créé par le notebook quand il écrit vos fichiers `s3_titanic_propre.csv` et `s3_journal.csv`.
