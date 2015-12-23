# Python-Tutorial 

## Les fonctions lambda et sorted

````
  f = lambda x: x * x
  
  >>> sorted(etudiants, key=lambda colonnes: colonnes[2])
  [
      ('Thomas', 11, 12), 
      ('Charles', 12, 15), 
      ('Damien', 12, 15), 
      ('Clément', 14, 16),
      ('Oriane', 14, 18)
  ]
  >>>
  
  >>> sorted(etudiants, key=lambda etudiant: etudiant.age, reverse=True)
  [
      <Étudiant Clément (âge=14, moyenne=16)>,
      <Étudiant Oriane (âge=14, moyenne=18)>,
      <Étudiant Charles (âge=12, moyenne=15)>,
      <Étudiant Damien (âge=12, moyenne=15)>,
      <Étudiant Thomas (âge=11, moyenne=12)>
  ]
  >>>
  
  // Pour les listes volumineuses
  from operator import itemgetter
  sorted(etudiants, key=itemgetter(2))
  
  from operator import attrgetter
  sorted(etudiants, key=attrgetter("moyenne"))
````

Le tri en Python se fait grâce à la méthode de liste sort, qui modifie la liste d'origine, et la fonction sorted, qui ne modifie pas la liste (ou la séquence) passée en paramètre ;
On peut spécifier des fonctions clés grâce à l'argument key. Ces fonctions sont appelées pour chaque élément de la séquence à trier, et retournent le critère du tri ;
Le module operator propose les fonctions itemgetter et attrgetter qui peuvent être très utiles en tant que fonction clés, si on veut trier une liste de tuples ou une liste d'objets selon un attribut ;
Le tri en Python est « stable », c'est-à-dire que l'ordre de deux éléments dans la liste n'est pas modifié s'ils sont égaux. Cette propriété permet le chaînage de tri.
## Les modules et les namespaces

````
  import math as mathematiques
  help('mathematiques')
  from math import fabs
  
  # Savoir si le fichier est importé ou s'il est le main
  if __name__ == "__main__":
````
* On peut écrire les programmes Python dans des fichiers portant l'extension **````.py````**.
* On peut créer des fichiers contenant des modules pour séparer le code.
* On peut créer des répertoires contenant des packages pour hiérarchiser un programme.

## Les fonctions

````
  def name(arg = arg1, arg2 = arg2, arg3 = arg3):
    """ Doc source de la fonction """
    return 
    
  name(arg2 = 2, arg1 = 1)
  
  def fonction_inconnue(nom, prenom, *commentaires): # * pour un nombre d'arguments variable
````

## Les exeptions et assertions

````
  try:
      # Bloc de test
  except type_de_l_exception as exception_retournee:
      print("Voici l'erreur :", exception_retournee)
      
  annee = input("Saisissez une année supérieure à 0 :")
    try:
        annee = int(annee) # Conversion de l'année
        assert annee > 0
    except ValueError:
        print("Vous n'avez pas saisi un nombre.")
    except AssertionError:
        print("L'année saisie est inférieure ou égale à 0.")
````
* On peut intercepter les erreurs (ou exceptions) levées par notre code grâce aux blocs tryexcept.
* La syntaxe d'une assertion est ````assert test````.
* Les assertions lèvent une exception ````AssertionError```` si le test échoue.
* On peut lever une exception grâce au mot-clé ````raise```` suivi du type de l'exception.

## Les Objets

* Les variables utilisées jusqu'ici sont en réalité des objets.
* Les types de données utilisés jusqu'ici sont en fait des classes. Chaque objet est modelé sur une classe.
* Chaque classe définit certaines fonctions, appelées méthodes, qui seront accessibles depuis l'objet grâce à ````objet.methode(arguments)````.
* On peut directement accéder à un caractère d'une chaîne grâce au code suivant : ````chaine[position_dans_la_chaine]````.
* Il est tout à fait possible de sélectionner une partie de la chaîne grâce au code suivant : ````chaine[indice_debut:indice_fin]````.

* Les méthodes spéciales permettent d'influencer la manière dont Python accède aux attributs d'une instance et réagit à certains opérateurs ou conversions.
* Les méthodes spéciales sont toutes entourées de deux signes « souligné » (_).
* Les méthodes **\__getattr\__**, **\__setattr\__** et **\__delattr\__** contrôlent l'accès aux attributs de l'instance.
* Les méthodes **\__getitem\__**, **\__setitem\__** et **\__delitem\__** surchargent l'indexation ([]).
* Les méthodes **\__add\__**, **\__sub\__**, **\__mul\__**… surchargent les opérateurs mathématiques.
* Les méthodes **\__eq\__**, **\__ne\__**, **\__gt\__**… surchargent les opérateurs de comparaison.

### Class String

<p align="center">   
<img src='https://developers.google.com/edu/python/images/hello.png' alt='String Class' />
</p>

````
  chaine = str()
  chaine = "Hello"
  chaine[1:4] #is 'ell' -- chars starting at index 1 and extending up to but not including index 4
  text = ("%d little pigs come out or I'll %s and %s and %s" % (3, 'huff', 'puff', 'blow down'))
````
* __String Methode()__
  * s.__lower()__ / s.__upper()__         
  *-- returns the lowercase or uppercase version of the string*
  * s.__strip()__       
  *-- returns a string with whitespace removed from the start and end**
  * s.__isalpha()__ / s.__isdigit()__ / s.__isspace()__ ...            
  *-- tests if all the string chars are in the various character classes*
  * s.__startswith(__ *'other'* __)__, s.__endswith(__ *'other'* __)__           
  *-- tests if the string starts or ends with the given other string*
  * s.__find(__ *'other'* __)__        
  *-- searches for the given other string (not a regular expression) within s, and returns the first index where it begins or -1 if not found*
  * s.__replace(__ *'old', 'new'* __)__         
  *-- returns a string where all occurrences of 'old' have been replaced by 'new'*
  * s.__split(__ *'delim'* __)__            
  *-- returns a list of substrings separated by the given delimiter. The delimiter is not a regular expression, it's just text.* 'aaa,bbb,ccc'.split(',') -> ['aaa', 'bbb', 'ccc']. As a convenient special case s.split() (with no arguments) splits on all whitespace chars.
  * s.__join(__ *list* __)__       
  *-- opposite of split(), joins the elements in the given list together using the string as the delimiter. e.g. '---'.join(['aaa', 'bbb', 'ccc']) -> aaa---bbb---ccc*
  
### Class Liste

<p align="center">   
<img src='https://developers.google.com/edu/python/images/list1.png' alt='List Class' />
</p>

````
  ma_liste = [1, 2, 3, 4, 5] # Une liste avec cinq objets
  tuple = (1,2,3,4,5)
  
  squares = [1, 4, 9, 16]
  sum = 0
  for num in squares:
    sum += num
  print sum  ## 30
  
  list = ['larry', 'curly', 'moe']
  if 'curly' in list:
    print 'yay'
    
  >>> qtt_a_retirer = 7 # On retire chaque semaine 7 fruits de chaque sorte
  >>> fruits_stockes = [15, 3, 18, 21] # Par exemple 15 pommes, 3 melons...
  >>> [nb_fruits-qtt_a_retirer for nb_fruits in fruits_stockes if nb_fruits>qtt_a_retirer]
  [8, 11, 14]
  
  >>> inventaire = [
  ...     ("pommes", 22),
  ...     ("melons", 4),
  ...     ("poires", 18),
  ...     ("fraises", 76),
  ...     ("prunes", 51),
  ... ]
  >>>
  # On change le sens de l'inventaire, la quantité avant le nom
  inventaire_inverse = [(qtt, nom_fruit) for nom_fruit,qtt in inventaire]
  # On n'a plus qu'à trier dans l'ordre décroissant l'inventaire inversé
  # On reconstitue l'inventaire trié
  inventaire = [(nom_fruit, qtt) for qtt,nom_fruit in sorted(inventaire_inverse, \reverse=True)]
````

* __List Methode()__
  * list.__append(__ *elem* __)__         
  *-- adds a single element to the end of the list. Common error: does not return the new list, just modifies the original.*
  * list.__insert(__ *index, elem* __)__         
  *-- inserts the element at the given index, shifting elements to the right.*
  * list.__extend(__ *list2* __)__      
  *adds the elements in list2 to the end of the list. Using + or += on a list is similar to using extend().*
  * list.__index(__ *elem* __)__      
  *-- searches for the given element from the start of the list and returns its index. Throws a ValueError if the element does not appear (use "in" to check without a ValueError).*
  * list.__remove(__ *elem* __)__       
  *-- searches for the first instance of the given element and removes it (throws ValueError if not present)*
  * list.__sort()__       
  *-- sorts the list in place (does not return it). (The sorted() function shown below is preferred.)*
  * list.__reverse()__       
  *-- reverses the list in place (does not return it)*
  * list.__pop(__ index __)__       
  *-- removes and returns the element at the given index. Returns the rightmost element if index is omitted (roughly the opposite of append()).*
  * list.__remove(__ index __)__        
  *-- removes and at the given index.*

* Contrairement à la classe str, la classe list vous permet de remplacer un élément par un autre. Les listes sont en effet des types dits mutables.
* Une liste est une séquence mutable pouvant contenir plusieurs autres objets.
* Une liste se construit ainsi : liste = [element1, element2, elementN].
* On peut insérer des éléments dans une liste à l'aide des méthodes append, insert et extend.
* On peut supprimer des éléments d'une liste grâce au mot-clé del ou à la méthode remove.
* Un tuple est une séquence pouvant contenir des objets. À la différence de la liste, le tuple ne peut être modifié une fois créé.

### Class Disctionnaire

<p align="center">   
<img src='https://developers.google.com/edu/python/images/dict.png' alt='Dictionnaire Class' />
</p>


````
  dictionnaire = {} or new Dict()
  set = {1,"test",[],{}} #Pour créer des SETs
  
  for cle in fruits:
  for cle in fruits.keys():
  for valeur in fruits.values():
  for cle, valeur in fruits.items():
````

* Un dictionnaire est un objet conteneur associant des clés à des valeurs.
* Pour créer un dictionnaire, on utilise la syntaxe dictionnaire = {cle1:valeur1, cle2:valeur2, cleN:valeurN}.
* On peut ajouter ou remplacer un élément dans un dictionnaire : dictionnaire[cle] = valeur.
* On peut supprimer une clé (et sa valeur correspondante) d'un dictionnaire en utilisant, au choix, le mot-clé del ou la méthode pop.
* On peut parcourir un dictionnaire grâce aux méthodes keys (parcourt les clés), values (parcourt les valeurs) ou items (parcourt les couples clé-valeur).
* On peut capturer les paramètres nommés passés à une fonction en utilisant cette syntaxe : def fonction_inconnue(**parametres_nommes): (les paramètres nommés se retrouvent dans le dictionnaire parametres_nommes).
