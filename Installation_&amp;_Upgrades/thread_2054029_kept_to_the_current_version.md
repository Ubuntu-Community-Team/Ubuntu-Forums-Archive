---
title: "kept to the current version"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by mune on 2012-09-06
I login via ssh in a remote  box in my home net:
```
fmune@lello:~/Scaricati$ ssh -X mune@192.168.1.10
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-26-generic i686)

 * Documentation:  https://help.ubuntu.com/

15 packages can be updated.
4 updates are security updates.

No mail.
Last login: Thu Sep  6 01:24:00 2012 from lello.local
```

I see there are new packages. I search for some more:
```
mune@grilli-secure:~$ sudo apt-get update
[sudo] password for mune: 
Ign http://it.archive.ubuntu.com precise InRelease                                                                              
Ign http://security.ubuntu.com precise-security InRelease                    
Ign http://extras.ubuntu.com precise InRelease       
Ign http://it.archive.ubuntu.com precise-updates InRelease
Trovato http://security.ubuntu.com precise-security Release.gpg
Scaricamento di:1 http://extras.ubuntu.com precise Release.gpg [72 B]
..................... SNIP .........................
fmune@lello:~/Scaricati$ ssh -X mune@192.168.1.10
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-26-generic i686)

 * Documentation:  https://help.ubuntu.com/

15 packages can be updated.
4 updates are security updates.

No mail.
Last login: Thu Sep  6 01:24:00 2012 from lello.local
mune@grilli-secure:~$ sudo apt-get update
[sudo] password for mune: 
Ign http://it.archive.ubuntu.com precise InRelease                                                                              
Ign http://security.ubuntu.com precise-security InRelease                    
Ign http://extras.ubuntu.com precise InRelease       
Ign http://it.archive.ubuntu.com precise-updates InRelease
Trovato http://security.ubuntu.com precise-security Release.gpg
Scaricamento di:1 http://extras.ubuntu.com precise Release.gpg [72 B]
--------------------- CUT ------------------
Trovato http://it.archive.ubuntu.com precise-updates/restricted Translation-it                                                  
Trovato http://it.archive.ubuntu.com precise-updates/restricted Translation-en                                                  
Trovato http://it.archive.ubuntu.com precise-updates/universe Translation-it                                                    
Trovato http://it.archive.ubuntu.com precise-updates/universe Translation-en
Recuperati 791 kB in 31s (25,2 kB/s)                 
Lettura elenco dei pacchetti... Fatto
```
and upgrade:
```
mune@grilli-secure:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati mantenuti alla versione attuale:
  hplip hplip-data libhpmud0 libsane-hpaio linux-generic linux-headers-generic linux-headers-generic-pae linux-image-generic
  printer-driver-hpcups printer-driver-hpijs
0 aggiornati, 0 installati, 0 da rimuovere e 10 non aggiornati.
```

In the very beginning I thoght it could be related to the fact I compiled an app, but now I am concerned to always keep an ancient kernel that became vulnerable to crackers. This situation -not upgrading the kernel- is getting over 1.5 months. I'm starting to be worried.

What can be?

---

### Post by zvacet on 2012-09-06
Try with 

```
sudo apt-get dist-upgrade
```

---

