# Projet NLP Simplifié : Génération de Poèmes et Analyse de Sentiments

Un projet simple et efficace de traitement du langage naturel (NLP) implémentant deux fonctionnalités principales avec des modèles LSTM.

## 🎯 Fonctionnalités

### 1. Génération de Poèmes
- **Modèle LSTM** entraîné sur un corpus de poésie française
- **Génération créative** à partir d'un mot de départ
- **Contrôle de température** pour ajuster la créativité
- **Corpus riche** de poésie française classique

### 2. Analyse de Sentiments
- **Classification binaire** (positif/négatif) 
- **Modèle LSTM** avec dropout pour éviter le surapprentissage
- **Score de confiance** pour chaque prédiction
- **Données équilibrées** d'exemples français

## 📁 Structure du Projet

```
NLP-a5/
├── project.ipynb           # Notebook principal (TOUT EN UN)
├── data/
│   ├── poetry_corpus.txt   # Corpus de poésie française
│   └── sentiment_data.txt  # Données d'analyse de sentiment
└── README.md              # Ce fichier
```

## 🚀 Installation et Utilisation

### Prérequis
```bash
pip install torch torchvision
pip install numpy matplotlib scikit-learn
```

### Exécution
1. Ouvrez `project.ipynb` dans Jupyter Notebook/Lab
2. **IMPORTANT** : Exécutez les cellules dans l'ordre :
   - Cellule 1 : Titre et description
   - Cellule 2 : Imports
   - **Cellule 3 : SimpleEncoder** ⚠️ À exécuter OBLIGATOIREMENT avant les autres
   - Cellules suivantes : dans l'ordre séquentiel

## 🧠 Architecture Technique

### Encodage de Caractères
- **SimpleEncoder** : Encodage caractère par caractère
- Vocabulaire dynamique basé sur le corpus
- Mapping bidirectionnel char ↔ index

### Modèles LSTM

#### Génération de Poèmes (`PoetryLSTM`)
```python
- Embedding : 64 dimensions
- LSTM : 128 unités cachées
- Séquences : 15 caractères
- Température : 0.8 (ajustable)
```

#### Analyse de Sentiments (`SentimentLSTM`)
```python
- Embedding : 32 dimensions  
- LSTM : 64 unités cachées
- Classes : 2 (positif/négatif)
- Dropout : 0.2
- Longueur max : 30 caractères
```

## 📊 Données

### Corpus de Poésie
- **144 lignes** de poésie française classique
- Styles variés : Verlaine, romantique, symboliste
- **~8000 caractères** au total

### Données de Sentiment
- **30 exemples** équilibrés (15 positifs, 15 négatifs)
- Phrases en français naturel
- Format : `texte\tlabel` (0=négatif, 1=positif)

## 🎮 Exemples d'Utilisation

### Génération de Poèmes
```python
# Générer un poème commençant par "Les"
poem = generate_poetry(poetry_model, poetry_encoder, "Les", length=80)
print(poem)
```

### Analyse de Sentiments  
```python
# Analyser le sentiment d'une phrase
sentiment, confidence = predict_sentiment(
    sentiment_model, 
    sentiment_encoder, 
    "J'adore cette journée!"
)
print(f"{sentiment} ({confidence:.3f})")  # Positif (0.892)
```

## 📈 Performance

### Génération de Poèmes
- **Convergence** : ~80 époques
- **Perte finale** : ~1.2
- **Qualité** : Génère des vers cohérents avec rimes

### Analyse de Sentiments
- **Précision** : ~85-95% sur l'ensemble de test
- **Convergence** : ~100 époques  
- **Confiance moyenne** : ~0.8

## 🔧 Personnalisation

### Ajuster la Créativité des Poèmes
```python
# Plus créatif (température élevée)
poem = generate_poetry(model, encoder, "Les", temperature=1.2)

# Plus conservateur (température faible)  
poem = generate_poetry(model, encoder, "Les", temperature=0.5)
```

### Ajouter des Données
- **Poésie** : Ajoutez vos poèmes dans `data/poetry_corpus.txt`
- **Sentiment** : Ajoutez des lignes dans `data/sentiment_data.txt` au format `texte\tlabel`

## 🎯 Points Forts

✅ **Simple et compact** : Un seul fichier notebook  
✅ **Données incluses** : Corpus prêt à l'emploi  
✅ **Code minimal** : ~300 lignes total  
✅ **Résultats immédiats** : Génération et classification fonctionnelles  
✅ **Français natif** : Optimisé pour la langue française  

## 🚧 Limitations

- **Corpus limité** : Convient pour la démonstration
- **Caractères uniquement** : Pas de tokenisation par mots
- **Modèles simples** : LSTM basiques sans attention
- **CPU seulement** : Optimisé pour l'entraînement local

## 🔮 Améliorations Possibles

- Ajouter plus de données d'entraînement
- Implémenter des modèles Transformer
- Ajouter d'autres langues
- Interface web pour la démonstration
- Sauvegarde/chargement des modèles entraînés

## 📝 License

Ce projet est fourni à des fins éducatives et de démonstration.

---

*Projet réalisé dans le cadre d'un cours de NLP - Version simplifiée et fonctionnelle*