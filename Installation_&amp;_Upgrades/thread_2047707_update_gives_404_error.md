---
title: "update gives 404 error"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2012-08-25
What do I do in this situation (note that other packages were updates fine on a previous run a minute earlier) ? Thanks

```
$ sudo aptitude full-upgrade 
Les paquets suivants seront mis à jour*:      
  cups cups-bsd cups-client cups-common cups-ppdc libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 
  libcupsppdc1 
11 paquets mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de télécharger 2 705 ko d'archives. Après dépaquetage, 52,2 ko seront utilisés.
Voulez-vous continuer*? [Y/n/?] 
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libcups2 amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsmime1 amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libcupscgi1 amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsimage2 amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsppdc1 amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main cups-common all 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main cups-bsd amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main cups-client amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main cups-ppdc amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main cups amd64 1.5.3-0ubuntu3
  404  Not Found
Err http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libcupsdriver1 amd64 1.5.3-0ubuntu3
  404  Not Found
0% [En cours]E: impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.5.3-0ubuntu3_amd64.deb*: 404  Not Found
                                              
E: impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.5.3-0ubuntu3_amd64.deb*: 404  Not Found

```

---

### Post by zvacet on 2012-08-27
Try with 

```
sudo aptitude safe-upgrade
```

or in Ubuntu software center>edit>repositories change server to main.

---

### Post by dargaud on 2012-09-11
Thanks, but that didn't help. This did:
> sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

