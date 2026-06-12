---
title: "installation l'oracle 10 XE  sur ubuntu 9.10"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by haha100 on 2010-06-16
[CENTER][SIZE=6]pour les expert de [COLOR=Sienna]ubuntu[/COLOR] pouvez-vous donner une explication en detaille concernant l'installation de
l'oracle 10XE
sous ubuntu
(j'ai déjà telecharger le fichier oracle-xe-universal_10.2.0.1-1.0_i386.deb )
et merci d'avance[/SIZE]
[/CENTER]

---

### Post by lechien73 on 2010-06-16
Excusez-moi, mais je n'ai parlé pas français depuis longtemps! Pour commencer, vous avez besoin d'un "swap space" grands sur votre disque. Puis:

[LIST]
[*]Ouvrez un terminal et écrire:

```
sudo dpkg -i oracle-xe-universal_10.2.0.1-1.0_i386.deb
```

[*]Aprés l'installation, écrire:

```
/etc/init.d/oracle-xe configure
```

[*]Acceptez les valeurs par défaut, et créer un mot de passe.

[*]Vous pouvez ensuite vous connecter à Oracle-XE avec Firefox sur:

```
http://127.0.0.1:8080/apex
```

[*]Le nom d'utilisateur est: **system**, et donnez le mot de passe que vous avez créé.
[/LIST]

J'espère que cela est utile.

---

### Post by haha100 on 2010-06-16
j'ai un probleme 
```
(Lecture de la base de données... 122961 fichiers et répertoires déjà installés.)
Dépaquetage de oracle-xe-universal (à partir de oracle-xe-universal_10.2.0.1-1.0_i386.deb) ...
You have insufficient diskspace in the destination directory (/usr/lib) to 
install Oracle Database 10g Express Edition.  The installation requires at 
least 1.5 GB free on this disk.
dpkg*: erreur de traitement de oracle-xe-universal_10.2.0.1-1.0_i386.deb (--install)*:
 le sous-processus nouveau script pre-installation a retourné une erreur de sortie d'état 1
Des erreurs ont été rencontrées pendant l'exécution*:
 oracle-xe-universal_10.2.0.1-1.0_i386.deb

```

---

### Post by lechien73 on 2010-06-16
Donc, il n'y a pas assez d'espace sur le disque.

S'il vous plaît exécutez la commande:

```
df -v
```

Et mettre les résultats ici.

---

### Post by haha100 on 2010-06-16
voila
```
Sys. de fich.           1K-blocs       Occupé Disponible Capacité Monté sur
/dev/loop0             4781488   3426240   1112356  76% /
udev                    900252       272    899980   1% /dev
none                    900252       436    899816   1% /dev/shm
none                    900252        92    900160   1% /var/run
none                    900252         0    900252   0% /var/lock
none                    900252         0    900252   0% /lib/init/rw
/dev/sda5             51199120  38795144  12403976  76% /host

```

---

### Post by lechien73 on 2010-06-16
C'est une disque 50Gb? Qu'est-ce que le périphérique de "loop0"? Si vous êtes sous Ubuntu à partir d'une image DVD?

Il est possible de créer un lien, parce que vous ne pouvez pas changer l'emplacement d'installation:

```
sudo mkdir -p /host/usr/lib/oracle
sudo ln -s /host/usr/lib/oracle /usr/lib/oracle

```
Et essayer de nouveau.

---

### Post by haha100 on 2010-06-16
non j'ai le ubuntu à coté de windows dans le demarrage c'est à dire "[COLOR="Red"]install incide windowss[/COLOR]"

---

### Post by lechien73 on 2010-06-16
Ok, je comprends. S'il vous plaît essayez la procédure précédente, et dites-moi si ça fonctionne.

---

### Post by haha100 on 2010-06-17
voila 
```
hamza@ubuntu:~$ sudo mkdir -p /host/usr/lib/oracle
[sudo] password for hamza: 
hamza@ubuntu:~$ sudo ln -s /host/usr/lib/oracle /usr/lib/oracle
ln: création d'un lien symbolique `/usr/lib/oracle/oracle': Le fichier existe
hamza@ubuntu:~$ 



```

---

### Post by lechien73 on 2010-06-17
C'est parce que le fichier est créé déjà. Il contient une installation partielle. Il nous faut donc l'enlever.

```
sudo rm -r /usr/lib/oracle
```

Et apres:

```
sudo ln -s /host/usr/lib/oracle /usr/lib/oracle
```

Et essayer de nouveau l'installation.

---

### Post by haha100 on 2010-06-17
[COLOR="Red"]des informations importants:[/COLOR]
quant je clique sur application je trouve dans la liste oracle 10g xe
mais il y a deux problemes :
[LIST=1]
[*]je n'ai pas de session
[*]je ne peut pas accéder à la page d'acceil de la base de données
[/LIST]
merci pour votre effort avec moi

---

