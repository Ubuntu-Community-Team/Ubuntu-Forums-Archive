---
title: "Problem &quot;dependencies&quot; during update"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by isagarran on 2013-02-04
Hello,

Ubuntu 12.04 in a virtualbox 4.2.0 (Host is Ubuntu 12.04) 

I need some help as I encountered network problems during fix update. I restart the update processing and I got messages. Now when, I issued this command : 
```
sudo apt-get update && sudo apt-get upgrade
```

I got :
**********************************************************************
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer «*apt-get -f install*» pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites*:
 linux-generic-pae : Dépend: linux-image-generic-pae (= 3.2.0.37.44) mais 3.2.0.37.45 est installé
                     Dépend: linux-headers-generic-pae (= 3.2.0.37.44) mais 3.2.0.37.45 est installé
E: Dépendances manquantes. Essayez d'utiliser l'option -f.
**********************************************************************

I tried 
sudo apt-get -f update && sudo apt-get -f upgrade
sudo dpkg --configure -a

I can't get rid off te problem. Could you help me please ?
Best regards.
Isagarran

---

### Post by isagarran on 2013-02-13
Hello,
Could you help me and give me some advices or on the way to find any elements that could solve the problem.
best regards.
isagarran

---

### Post by schragge on 2013-02-13
Try *sudo apt-get -f install* like the error message says.

---

### Post by isagarran on 2013-02-19
Hello,
Thanks for you reply.
I run the command and in the terminal, I got (at the end of the terminal) :
> 
Paramétrage de linux-image-generic-pae (3.2.0.38.46) ...
Paramétrage de linux-headers-3.2.0-38 (3.2.0-38.60) ...
Paramétrage de linux-headers-3.2.0-38-generic-pae (3.2.0-38.60) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
Paramétrage de linux-headers-generic-pae (3.2.0.38.46) ...
dpkg*: des problèmes de dépendances empêchent la configuration de linux-generic-pae*:
 linux-generic-pae dépend de linux-image-generic-pae (= 3.2.0.37.44)*; cependant*:
  La version de linux-image-generic-pae sur le système est 3.2.0.38.46.
 linux-generic-pae dépend de linux-headers-generic-pae (= 3.2.0.37.44)*; cependant*:
  La version de linux-headers-generic-pae sur le système est 3.2.0.38.46.
dpkg*: erreur de traitement de linux-generic-pae (--configure)*:
 problèmes de dépendances - laissé non configuré
Aucun rapport «*apport*» n'a été créé car le message d'erreur indique une erreur consécutive à un échec précédent.
                                  Des erreurs ont été rencontrées pendant l'exécution*:
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)


Regards.
isagarran

---

