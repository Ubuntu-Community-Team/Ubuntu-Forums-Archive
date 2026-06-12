---
title: "problem with RPM"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by ribidi on 2012-02-29
Hi, 
i'm using ubuntu 9.10 and i've trying to install an rpm package from this site 

[http://docs.tinyos.net/tinywiki/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages](http://docs.tinyos.net/tinywiki/index.php/Installing_TinyOS_2.1.1#Two-step_install_on_your_host_OS_with_Debian_packages)

but when i tape sudo apt-get install rpm this is the result "E: Aucun paquet ne correspond au paquet rpm"

so after some googling, i found a site   [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)
but the same thing when i tape sudo -apt-get install alien this is the result 
" Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet alien"
 

i  really need your help.
thank you

---

### Post by oldos2er on 2012-02-29
9.10 is no longer supported, so its repositories have moved to old-releases. 

[http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)

---

### Post by ribidi on 2012-03-01
> **oldos2er said:**
> 9.10 is no longer supported, so its repositories have moved to old-releases. 

[http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/](http://www.warpconduit.net/2011/07/31/apt-repository-for-old-ubuntu-releases/)


thanks a lot. it works

---

