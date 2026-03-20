

## Lancemmentprojet
AliceHELIOUandVincentTHOUVENOT
Laboratoire Cyber de cortAIx Labs

## Content
## 1. Bilanmi-projet
## 2. Déroulementduprojet
## 3. Rappelsurlecasd’usage
## 4. Cequiestfourni
## 5. Cequiestattendu
Paris-Saclay University - Lancement projet2/13

## Bilanmi-projet
Paris-Saclay University - Lancement projet

## Bilanmi-projet
Dans l’ensemble vous avez bien compris l’analyse demandée.
Nous accordons de l’importance à la réflexion et aux explications.
## Rappels
## •
L’analyse univariée peut révéler des déséquilibres, l’analyse bivariée peut
révéler des biais.
## •
Les biais peuvent avoir une explication (voire le Paradoxe de Simpson), mais ils
restent factuels.
## •
Un modèle de machine learning (tout comme nous) a tendance à amplifier les
biais présents.
Paris-Saclay University - Lancement projet3/13

## Bilanmi-projet
Dans l’ensemble vous avez bien compris l’analyse demandée.
Nous accordons de l’importance à la réflexion et aux explications.
## Rappels
## •
L’analyse univariée peut révéler des déséquilibres, l’analyse bivariée peut
révéler des biais.
## •
Les biais peuvent avoir une explication (voire le Paradoxe de Simpson), mais ils
restent factuels.
## •
Un modèle de machine learning (tout comme nous) a tendance à amplifier les
biais présents.
Paris-Saclay University - Lancement projet3/13

## Déroulementduprojet
Paris-Saclay University - Lancement projet

## Déroulement
## •
projet en trinome
## •
Sessions dédiées: semaines du 09/03 et 23/03
## •
Rendu des notebooks finaux avant le cours de la semaine du 30/03
donc avant le pour le 01/04 groupe 1 et avant le 03/04 pour le groupe 2
## •
Soutenance: sur les créneaux de cours de la semaine du 7 avril
## •
note finale =
mi−parcours+notebookfinal+2xsoutenance
## 4
Paris-Saclay University - Lancement projet4/13

## Déroulement
## •
projet en trinome
## •
Sessions dédiées: semaines du 09/03 et 23/03
## •
Rendu des notebooks finaux avant le cours de la semaine du 30/03
donc avant le pour le 01/04 groupe 1 et avant le 03/04 pour le groupe 2
## •
Soutenance: sur les créneaux de cours de la semaine du 7 avril
## •
note finale =
mi−parcours+notebookfinal+2xsoutenance
## 4
Paris-Saclay University - Lancement projet4/13

## Rappelsurlecasd’usage
Paris-Saclay University - Lancement projet

## Casd’usage
Chest X ray NIH 14 Dataset
https://www.kaggle.com/datasets/nih-chest-xrays/data
Dataset d’image de rayons X, fourni avec de nombreuses informations sur les
personnes (notamment age, genre, maladies). Pour votre projet les images ont
toutes été compressées en 256x256.
Paris-Saclay University - Lancement projet5/13

## Cequiestfourni
Paris-Saclay University - Lancement projet

SurecampusdansledossierProjet
Les données
Un zip par personne dans le dossier données_par_eleve , chacun contient un
dossier avec cette structure: NOM_PRENOM
## •
train:
## •
malade : avec des images
## •
sain: avec des images
## •
valid:
## •
malade : avec des images
## •
sain: avec des images
## •
metadata.csv (fichier similaire à celui que vous avez eu pour le mi-projet)
Paris-Saclay University - Lancement projet6/13

## Infos
Code fournis
Vous trouverez un fichier train_classifieur.py et deux notebooks, un pour l’execution
locale l’autre pour l’utilisation de colab Le fichier train_classifieur.py n’a pas etre
modifié ni compris, vous pouvez l’utiliser tel quel. N’hésitez cependant pas à nous
poser des questions
Modèle de classification d’image: Resnet18
Le modèle utilisé est un ResNet18, il ne prend en entrée que l’image, pas les
métadonnées.
Celles-ci sont néanmoins nécessaires pour réduire les biais.
En effet le Resnet18 peut très bien retrouver les attributs tels que ’View Position’,
’Patient Gender’ et ’Patient Age’ à partir des images uniquement.
Paris-Saclay University - Lancement projet7/13

Infos-ResNet18
0:<40 ans / 1:40-60ans / 2:>60ans0: F / 1: M0: AP / 1: PA
Paris-Saclay University - Lancement projet8/13

## Utilisationdansunnotebook
from train_classifieur import train_classifier, pred_classifier
ckpt_path, ckpt_score = train_classifier( # prend entre 20 et 60min
logdir="./expe_log/",
datadir="NOM_PRENOM/",
weights_col="WEIGHTS",
csv="NOM_PRENOM/metadata.csv")
pred_classifier( # prend entre 5 et 10min
datadir="NOM_PRENOM/",
csv_in="NOM_PRENOM/metadata.csv"
csv_out="./expe_log/preds.csv",
ckpt_path = ckpt_path)
Paris-Saclay University - Lancement projet9/13

## Utilisationenlignedecommande
python train_classifieur.py
--logdir expe_log/
--datadir NOM_PRENOM/
--csv NOM_PRENOM/metadata.csv
--weights_col WEIGHTS
--csv_out expe_log/preds.csv
En ajoutant les arguments
## "--train False --ckpt /chemin_vers_votre_modele.ckpt"
vous pouvez ne faire que les prédictions.
Paris-Saclay University - Lancement projet10/13

## Cequiestattendu
Paris-Saclay University - Lancement projet

## Cequiseraévalué
## •
Analyse rapide des données: En plus court que le mi-projet, étudier le dataset
et montrer les déséquilibres et biais.
## •
Analyse de l’impact de la pondération sur les performances du modèles:
Prendre en compte la performance en ’balanced accuracy” mais aussi sur les
métriques de fairness. Essayer plusieurs méthodes de pondération
## •
Analyse de l’impact du post-processing: Idem prendre en compte plusieurs
critères pour la comparaison et tester plusieurs approches. Regarder les
combinaisons pre/post processing
## •
Soin: Comme toujours le rapport devra comporter une introduction, une
conclusion et un soin devra être apporter pour aider la compréhension/lecture
Paris-Saclay University - Lancement projet11/13

## Notation
## •
1/4: Rapport final:
## •
## Introduction (/1)
## •
Preparation et analyse des données (/3)
## •
Application des méthodes de pre processing et étude de métriques de fairness
## (/3)
## •
Application des méthodes de post processing et étude de métriques de fairness
## (/5)
## •
Analyse, compréhension (/3)
## •
## Soin (/4)
## •
## Conclusion (/1)
## •
1/2: Soutenance de 15 minutes, (10’ présentation, 5’ de questions)
## •
Présentation avec illustration du travail effectué
## •
Ainsi que de l’organisation choisie au sein du groupe
Paris-Saclay University - Lancement projet12/13

## Conseils
Code TD
Il est tout à fait autorisé (meme conseillé) de réutiliser les codes fait en TDs.
A l’inverse l’utilisation de LLM peut introduire des problèmes de cohérence. Si vous
utilisez ces outils, soyez critiques faites attention à réfléchir à vos résulats, apporter
de la cohérence.
git
Git (par exemple github) est un outil très pratique pour travailler en groupe. De plus
cela vous permettrait de pouvoir ensuite (par exemple à un entretien) de montrer
vos travaux de projet académiques. Cela ne sera pas évaluer, mais nous vous
incitons à utiliser Git.
Paris-Saclay University - Lancement projet13/13