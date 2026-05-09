
# HelloToast — Laboratoire Android




https://github.com/user-attachments/assets/9ae1261c-f93e-429f-b69a-bc8ed713c54f



## Description du projet

**HelloToast** est une petite application Android développée avec **Java** et **XML** dans **Android Studio**.

L’application contient deux boutons principaux :

- Un bouton **TOAST** qui affiche un message temporaire à l’écran.
- Un bouton **COUNT** qui incrémente un compteur affiché au centre de l’interface.

Ce laboratoire permet de comprendre les bases du développement Android, surtout la relation entre l’interface graphique en XML et la logique programmée en Java.

---

## Objectif du laboratoire

L’objectif de ce laboratoire est de créer une application Android simple capable de :

- Afficher un message Toast lorsque l’utilisateur clique sur un bouton.
- Afficher un compteur à l’écran.
- Incrémenter ce compteur à chaque clic sur un bouton.
- Relier les composants XML avec le code Java.
- Comprendre le fonctionnement de `TextView`, `Button`, `Toast` et `setOnClickListener()`.

---

## Technologies et outils utilisés

| Outil / Technologie | Rôle |
|---|---|
| Android Studio | Environnement de développement utilisé pour créer le projet |
| Java | Langage utilisé pour programmer la logique de l’application |
| XML | Langage utilisé pour créer l’interface graphique |
| Android Emulator | Émulateur utilisé pour tester l’application |
| API minimum | API 24 — Android 7.0 |

---

## Étape 1 — Création du projet Android

Pour commencer, j’ai créé un nouveau projet dans Android Studio.

Les étapes suivies sont les suivantes :

1. Ouvrir **Android Studio**.
2. Cliquer sur **New Project**.
3. Choisir le modèle **Empty Activity**.
4. Donner le nom suivant au projet :


---

## Étape 2 — Structure du projet

Après la création du projet, Android Studio génère plusieurs dossiers et fichiers.

Dans ce laboratoire, les deux fichiers les plus importants sont :

```text
app/src/main/res/layout/activity_main.xml
app/src/main/java/com/example/hellotoast/MainActivity.java
```

Le fichier `activity_main.xml` permet de créer l’interface graphique de l’application.

Le fichier `MainActivity.java` permet de programmer les actions de l’application.

---

---

## Code XML complet

Ouvrir le fichier suivant :

```text
app/src/main/res/layout/activity_main.xml
```

Puis remplacer son contenu par le code suivant :

<img width="1058" height="1310" alt="image" src="https://github.com/user-attachments/assets/4bb51680-b991-42e8-ae83-48f5018791d6" />




---

## Explication du code XML

Le composant principal utilisé est `LinearLayout`.

```xml
<LinearLayout
    android:orientation="vertical">
```

Il permet d’organiser les éléments verticalement, c’est-à-dire les uns en dessous des autres.

---

### Couleur de fond

```xml
android:background="#FFFF00"
```

Cette ligne permet de changer la couleur de fond de l’écran en jaune.

---

### Bouton TOAST

```xml
<Button
    android:id="@+id/button_toast"
    android:text="TOAST" />
```

Ce bouton sert à afficher un message Toast.

L’identifiant `button_toast` permet de retrouver ce bouton dans le code Java.

---

### TextView du compteur

```xml
<TextView
    android:id="@+id/text_count"
    android:text="0" />
```

Ce `TextView` affiche la valeur du compteur.

Au démarrage de l’application, la valeur affichée est `0`.

---

### Bouton COUNT

```xml
<Button
    android:id="@+id/button_count"
    android:text="COUNT" />
```

Ce bouton sert à incrémenter le compteur.

À chaque clic, la valeur affichée au centre de l’écran augmente de 1.

---

## Aperçu de l’interface

Après avoir écrit le code XML, il est possible de visualiser l’interface dans Android Studio.

L’interface attendue contient :

- Un bouton bleu en haut.
- Un grand chiffre bleu au centre.
- Un bouton bleu en bas.
- Un fond jaune.

### Capture d’écran

Insérer ici une capture d’écran de l’aperçu XML.

```md
![Aperçu de l’interface](screenshots/apercu_interface.png)
```

---

## Étape 4 — Programmation de la logique Java

La logique de l’application est écrite dans le fichier :

```text
MainActivity.java
```

Ce fichier permet de contrôler les actions de l’utilisateur.

Dans ce laboratoire, le code Java doit permettre de :

1. Récupérer les composants de l’interface.
2. Détecter le clic sur le bouton **TOAST**.
3. Afficher un message temporaire.
4. Détecter le clic sur le bouton **COUNT**.
5. Incrémenter le compteur.

---

## Code Java complet

Ouvrir le fichier suivant :

```text
app/src/main/java/com/example/hellotoast/MainActivity.java
```

Puis remplacer son contenu par le code suivant :
-<img width="1122" height="1222" alt="image" src="https://github.com/user-attachments/assets/5e457540-2a98-4b8f-97c8-b09d3218d132" />

---

## Remarque importante sur le nom du package

La première ligne du fichier Java est :

```java
package com.example.hellotoast;
```

Cette ligne doit correspondre au nom du package généré dans ton projet Android Studio.

Si ton projet utilise un autre package, il faut remplacer cette ligne.

Exemple :

```java
package com.monprojet.hellotoast;
```

Donc, il faut toujours vérifier le package réel affiché dans Android Studio.

---

## Explication du code Java

### Déclaration du compteur

```java
private int count = 0;
```

Cette variable permet de stocker la valeur du compteur.

Au début, la valeur du compteur est `0`.

---

### Déclaration du TextView

```java
private TextView textCount;
```

Cette variable représente le texte affiché au centre de l’écran.

Elle permet de modifier la valeur affichée lorsque l’utilisateur clique sur le bouton **COUNT**.

---

### Méthode onCreate

```java
protected void onCreate(Bundle savedInstanceState)
```

La méthode `onCreate()` est exécutée automatiquement au lancement de l’activité.

C’est dans cette méthode que l’on initialise l’interface et les actions des boutons.

---

### Liaison entre Java et XML

```java
setContentView(R.layout.activity_main);
```

Cette ligne relie le fichier Java avec le fichier XML.

Elle indique que l’activité doit utiliser l’interface définie dans `activity_main.xml`.

---

### Récupération des composants XML

```java
textCount = findViewById(R.id.text_count);
Button buttonToast = findViewById(R.id.button_toast);
Button buttonCount = findViewById(R.id.button_count);
```

La méthode `findViewById()` permet de récupérer les composants créés dans le fichier XML grâce à leurs identifiants.

Les identifiants utilisés dans Java doivent être les mêmes que ceux définis dans XML.

---

### Action du bouton TOAST

```java
buttonToast.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        Toast.makeText(
                MainActivity.this,
                "Hello Toast!",
                Toast.LENGTH_SHORT
        ).show();
    }
});
```

Ce bloc de code détecte le clic sur le bouton **TOAST**.

Lorsque l’utilisateur clique sur ce bouton, un message temporaire s’affiche à l’écran.

Le message affiché est :

```text
Hello Toast!
```

---

### Action du bouton COUNT

```java
buttonCount.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {
        count++;
        textCount.setText(String.valueOf(count));
    }
});
```

Ce bloc de code détecte le clic sur le bouton **COUNT**.

À chaque clic :

1. La variable `count` augmente de 1.
2. La nouvelle valeur est convertie en texte.
3. Le `TextView` est mis à jour avec la nouvelle valeur.

---

## Étape 5 — Exécution de l’application

Après avoir terminé le code XML et le code Java, l’application peut être lancée avec l’émulateur Android.

### Étapes d’exécution

<img width="490" height="789" alt="image" src="https://github.com/user-attachments/assets/9f53ce63-29d3-4774-a66d-1ae0b23bf51e" />




---

## Résumé personnel

Dans ce laboratoire, j’ai développé une petite application Android appelée **HelloToast**.

Cette application contient deux boutons. Le premier bouton affiche un message Toast, tandis que le deuxième bouton incrémente un compteur affiché au centre de l’écran.

Ce travail m’a permis de mieux comprendre la structure d’une application Android et le rôle de chaque fichier principal.

Le fichier XML permet de créer l’interface graphique, tandis que le fichier Java permet de gérer les actions de l’utilisateur.

---

## Conclusion

Le laboratoire **HelloToast** a été réalisé avec succès.

Même si l’application est simple, elle permet de comprendre plusieurs notions importantes du développement Android.

Grâce à ce projet, j’ai appris comment créer une interface, comment récupérer les composants XML dans Java, comment gérer les clics sur les boutons, comment afficher un Toast et comment mettre à jour un compteur dynamiquement.

Ce laboratoire représente une bonne introduction au développement d’applications Android avec Java et XML.

---

