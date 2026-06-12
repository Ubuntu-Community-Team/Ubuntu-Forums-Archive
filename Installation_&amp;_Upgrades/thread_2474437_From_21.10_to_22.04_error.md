---
title: "From 21.10 to 22.04 error"
date: 2022-04-29
forum: Installation &amp; Upgrades
---

### Post by olufsen17 on 2022-04-29
Hi,
(I'm french)
I want to up-grade from 21.10 to 22.04 but this is the same problem each time I try:

Atteint :1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) impish InRelease
Ign :2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security InRelease
Atteint :3 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) impish-updates InRelease
Ign :4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) groovy-updates InRelease
Err :5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security Release
  404  Not Found [IP : 91.189.91.39 80]
Atteint :6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) impish-security InRelease
Atteint :7 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) impish-backports InRelease
Err :8 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) groovy-updates Release
  404  Not Found [IP : 51.158.154.169 80]
Lecture des listes de paquets... Fait
E: Le dépôt [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) groovy-security Release n'a pas de fichier Release.
N: Les mises à jour depuis un tel dépôt ne peuvent s'effectuer de manière sécurisée, et sont donc désactivées par défaut.
N: Voir les pages de manuel d'apt-secure(8) pour la création des dépôts et les détails de configuration d'un utilisateur.
E: Le dépôt [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) groovy-updates Release n'a pas de fichier Release.
N: Les mises à jour depuis un tel dépôt ne peuvent s'effectuer de manière sécurisée, et sont donc désactivées par défaut.
N: Voir les pages de manuel d'apt-secure(8) pour la création des dépôts et les détails de configuration d'un utilisateur.


What can I do / what I have to do?

thank you very much.

---

### Post by ajgreeny on 2022-04-29
It looks as though you are currently using groovy, ie 20.10, not 21.10 as you said and the repos for 20.10 have been moved and are now unavailable without using the EOL address.  This will probably be a long and tedious activity, requiring three upgrade moves, ie, 20.10 to 21.04, then 21.04 to 21.10, both of these needing the EOL repos to be enabled, and finally 21.10 to 22.04. I believe this offers far too may chances for things to go wrong so my advice is not to bother.

You can not simply do an upgrade to 22.04 from 20.10 so it will be simplest to clean install the new 20.04 LTS version after backing up all the personal folders and files in your home, and then restore them all after the clean install of 22.04.

You may like to consider creating a separate partition for /home which makes the version upgrade easier and quicker, with no need to restore the old home; youjust point the installer to it when choosing partitions in the installer, done by using the Something Else option as the installation method.
See 
[https://askubuntu.com/questions/1179437/how-to-install-new-version-of-ubuntu-and-keep-home-partition-untouched](https://askubuntu.com/questions/1179437/how-to-install-new-version-of-ubuntu-and-keep-home-partition-untouched)
[https://askubuntu.com/questions/142695/what-are-the-pros-and-cons-of-having-a-separate-home-partition](https://askubuntu.com/questions/142695/what-are-the-pros-and-cons-of-having-a-separate-home-partition)
[https://askubuntu.com/questions/1234838/is-it-necessary-to-have-a-home-and-swap-partitions-in-20-04](https://askubuntu.com/questions/1234838/is-it-necessary-to-have-a-home-and-swap-partitions-in-20-04)

---

### Post by olufsen17 on 2022-04-29
thank you to  				 					[ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar27747_27.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=27747") 				 				 					 						 	[URL="https://ubuntuforums.org/member.php?u=27747"][B][COLOR=#C61919][B]ajgreeny


[/B][/COLOR]
[/B][U][COLOR=#000000]Strange, because my system told me that my OS is Ubuntu 21.10 Impish (and I have Impish image on the screen).
[/COLOR][/U][/URL]

---

### Post by ActionParsnip on 2022-04-29
What is the output of
```

lsb_release -a; uname -a

```

---

### Post by grahammechanical on 2022-04-29
If you are on 21.10 (impish) then you should not have addresses for 20.10 (groovy) repositories in /etc/apt/sources.list. Please post the output of this command.

```
cat /etc/apt/sources.list
```

Here is a list of repository addresses for 21.10 (impish). This is what you should have in the sources/list file. You may have to edit sources.list to correct this problem.

[https://gist.github.com/wuseman/7e9ba901f8801304e4bc808ed83601a7](https://gist.github.com/wuseman/7e9ba901f8801304e4bc808ed83601a7)

Regards

---

