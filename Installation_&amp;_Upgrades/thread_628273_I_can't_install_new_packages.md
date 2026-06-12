---
title: "I can't install new packages"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by andxy on 2007-12-01
sudo apt-get install gparted
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Reading state information... Fatto               
Pacchetti suggeriti:
  xfsprogs reiser4progs jfsutils ntfsprogs
I seguenti pacchetti NUOVI (NEW) saranno installati:
  gparted
0 aggiornati, 1 installati, 0 da rimuovere e 33 non aggiornati.
È necessario prendere 0B/342kB di archivi. 
Dopo l'estrazione, verranno occupati 1954kB di spazio su disco.
(Lettura del database ... dpkg: errore processando /var/cache/apt/archives/gparted_0.3.3-2ubuntu6_i386.deb (--unpack):
 files list file for package `compiz-gnome' is missing final newline
Sono occorsi degli errori processando:
 /var/cache/apt/archives/gparted_0.3.3-2ubuntu6_i386.deb
L'operazione è stata bloccata perché si sono verificati troppi errori.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Someone can help me??

---

### Post by charleseddy on 2008-01-15
Sorry it took so long--i'm sure the nature of the problem, along with the fact that it's in a foreign language and should have been in a different forum, were part of the problem. 

This usually happens after filesystem corruption, when fsck removes or changes things that corrupt dpkg/info. This solution should work:

1. sudo gedit /var/lib/dpkg/status
2. Delete the section for compiz-gnome.
3. sudo mv /var/lib/dpkg/info /var/lib/dpkg/info_old
4. sudo mkdir /var/lib/dpkg/info
5. sudo apt-get update
6. sudo apt-get -f install

---

