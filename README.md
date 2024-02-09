# The Artbox project

## Étape 1 : Préparez votre travail

Avant de commencer le développement, il est important de commencer par comprendre le fonctionnement du site actuel, disponible sur ce repository envoyé par votre cliente.

### Recommandations

- Commencez par installer votre environnement de développement comme vu dans le cours, avec VSCode et MAMP, ou XAMP.
- Puis téléchargez le site envoyé par la cliente, ouvrez-le dans votre navigateur et dans votre IDE. Prenez bien le temps de regarder les différents fichiers. Vous verrez que du code est dupliqué entre les fichiers (le contenu et la structure) ainsi qu’au sein du fichier de la page d’accueil.

## Étape 2 : Factorisez le header et le footer

Maintenant que vous avez pris le temps de découvrir le code actuel, il est temps de l’améliorer ! Vous avez probablement remarqué que le code du header et du footer étaient présents sur chacune des pages.

Imaginez que vous souhaitiez modifier le contenu de ces éléments… Il faudrait alors effectuer cette modification pour chaque page, soit 16 fois !

### Recommandations

Vous savez maintenant utiliser la fonction include ? Utilisez-la sur le projet ! Deux étapes pour cela :

1. Créez les fichiers header.php et footer.php en y mettant respectivement le code HTML du header et du footer.
2. Remplacez le code du header et du footer par deux include, vers les fichiers fraîchement créés. Pensez à remplacer l’extension de tous les fichiers HTML par “.php” afin qu’ils soient lus par PHP.

Une fois ces changements effectués, vous serez capable de modifier le header ou le footer en une seule fois, et vos changements apparaîtront sur toutes les pages.

Vous y êtes arrivé ? Bravo ! Améliorons maintenant la gestion des œuvres !

#### changements effectués uniquement sur oeuvre-1.php : la suite du projet nous amenera à réduire le nombre de fichier oeuvre à un seul.

## Étape 3 : Créez le tableau des œuvres

Le site a maintenant un header et un footer “factorisés”. Il est temps de passer au code des œuvres.

Vous avez probablement remarqué que chaque œuvre était décrite deux fois dans le code : une fois dans la page d’accueil, une fois dans la page de détail de l’œuvre. Changer une œuvre implique donc de faire la modification deux fois. L’objectif va donc être de centraliser les œuvres dans un tableau PHP, qui sera beaucoup plus simple à maintenir.

### Recommandations

Une fois la notion de tableau bien comprise, vous pouvez mettre en place le tableau des œuvres. Pour cela :

- créez un fichier oeuvres.php ;
- dans ce fichier, créez un tableau PHP qui contiendra les 15 œuvres de la galerie. Vous vous servirez de ce tableau dans les étapes suivantes.

Pour vous aider :

- identifiez bien les informations de chaque œuvre sur le site ;
- vous aurez également besoin d’un identifiant d’œuvre (numéro de 1 à 15) pour pouvoir générer le lien vers les différentes œuvres par la suite ;
- l’idée est de regrouper toutes les œuvres dans un tableau. Chaque œuvre sera elle-même représentée par un tableau associatif qui regroupera les informations importantes de l'œuvre (titre, description, image...). Vous aurez donc une variable du type tableau contenant des tableaux.

Une fois cette étape terminée, vous devriez avoir un tableau avec toutes les œuvres pleinement utilisable pour les prochaines étapes !

## Étape 4 : Factorisez la page d’accueil

Maintenant que votre tableau est prêt, vous allez pouvoir l’utiliser sur la page d’accueil. En effet, vous avez peut-être remarqué que le code de la vignette représentant une œuvre est écrit 15 fois. Seuls l’image et le texte varient d’une vignette à une autre.

Ceci est problématique : si vous devez faire une modification sur le format de la vignette, vous devrez faire ce changement 15 fois !

### Recommandations

Comme vous l’avez peut-être compris, pour factoriser l’affichage des vignettes, vous allez devoir mettre en place une boucle dans votre page d’accueil afin de :

- parcourir votre tableau d’œuvres créé à l’étape précédente ;
- répéter automatiquement le code d’une vignette pour chacune de ces œuvres.

Pour vous aider dans votre tâche :

1. Identifiez bien le code répété pour chaque vignette.
2. Insérez, dans votre boucle, le code HTML répété.
3. Remplacez le contenu qui doit changer d’une œuvre à l’autre par les variables correspondantes, que vous afficherez en utilisant la fonction “echo”.

Votre boucle est mise en place ? Félicitations, votre page d’accueil est maintenant complètement factorisée et terminée ! Si vous avez besoin de modifier le format des vignettes, vous n’aurez à faire le changement qu’une seule fois au lieu de 15. Félicitations !

## Étape 5 : Factorisez les pages de détail des œuvres

Que de chemin parcouru ! Vous avez factorisé le header et le footer, ainsi que la page d’accueil. Un dernier problème subsiste. La page de détail d’une œuvre est dupliquée 15 fois, ce qui n’est pas une bonne chose. Si vous souhaitez changer l’affichage d’une œuvre, il faudra le faire sur chacune des œuvres. Remédions à cela.

### Recommandations

L’objectif est ici d’avoir un seul fichier oeuvre.php plutôt que 15 fichiers HTML. Commencez par créer ce fichier, et reprenez le contenu d’un des fichiers œuvres. Votre fichier sera appelé avec l’identifiant d’œuvre dans l’URL, par exemple :

- oeuvre.php?id=1 pour la première œuvre (id correspondant à l’identifiant de l’œuvre) ;
- oeuvre.php?id=2 pour la deuxième œuvre ;

et ainsi de suite.

Plusieurs modifications sont alors à apporter dans le fichier oeuvre.php :

1. Récupérez l’identifiant présent dans l’URL.
2. Recherchez, dans le tableau créé à l’étape 3, l’œuvre correspondant à l’identifiant (pour savoir comment rechercher un élément dans un tableau, retournez à la section "Recherchez dans un tableau").
3. Affichez le contenu de cette œuvre plutôt que le texte en brut actuellement dans le code.

N’oubliez pas de changer les liens des vignettes de la page d’accueil pour atterrir sur votre fichier oeuvre.php avec le bon identifiant dans l’URL.

Une fois ces changements apportés, vous devriez pouvoir supprimer les 15 fichiers d’œuvres. Parfait ! Vous avez ainsi :

- factorisé la structure des œuvres : si vous souhaitez modifier la structure de la page de détail d’une œuvre, vous n’avez à le faire qu’une seule fois ;
- factorisé le contenu des œuvres : si vous souhaitez modifier une œuvre, il vous suffit de la modifier dans le tableau. Elle sera automatiquement modifiée dans la liste des œuvres et dans la page de détail de l’œuvre.

Ça y est, votre code est factorisé, et vous avez maintenant un site dont les pages sont générées dynamiquement grâce à PHP. Il est temps de le présenter à Fatima.
