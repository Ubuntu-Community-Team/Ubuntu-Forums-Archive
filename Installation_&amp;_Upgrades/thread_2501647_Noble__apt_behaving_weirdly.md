---
title: "Noble : apt behaving weirdly"
date: 2024-10-16
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2024-10-16
Hi Guys,
I'm running 24.04.1 LTs on my laptop. 
I'm French and live in France, so my language is set to French. 
But I'm studying Català so I recently installed catalan keyboard and language support.
Since that time, apt has mixed language in it's messages : 
```

apt upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances... Fait
Lecture des informations d'état... Fait      
Calcul de la mise à jour... Fait
S'han ajornat les actualitzacions següents degut a escalonament:
  gir1.2-gtk-3.0 gtk-update-icon-cache indicator-keyboard libgail-3-0t64 libgtk-3-0t64 libgtk-3-bin libgtk-3-common libgtk-3-doc snapd
0 mis à jour, 0 nouvellement installés, 0 à enlever et 9 non mis à jour.
```
In this example, everything is in French except this : ```
S'han ajornat les actualitzacions següents degut a escalonament:
``` which is Català.... 
Funny, isn't it ?

---

