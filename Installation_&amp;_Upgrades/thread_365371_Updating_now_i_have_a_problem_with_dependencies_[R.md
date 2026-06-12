---
title: "Updating now i have a problem with dependencies [Resolved]"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by remakeit on 2007-02-19
I have this error upgrading Avidemux from ubuntu version (2.1.x) to 2.3.
I can't recover the installation and i don't know how to resolve this problem.....
I had tried with apt-get -f install......this is the response....
If i try to remove Avidemux or some lib of dependencies all the packages are to removed....

sudo apt-get -f install
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso
Reading state information... Fatto
Correzione delle dipendenze in corso... fallita.
I seguenti pacchetti hanno dipendenze non soddisfatte:
avidemux: Dipende: libasound2 (> 1.0.12) ma 1.0.11-7ubuntu3 è installato
Dipende: libc6 (>= 2.5-0ubuntu1) ma 2.4-1ubuntu12.3 è installato
Dipende: libfontconfig1 (>= 2.4.0) ma 2.3.2-7ubuntu2 è installato
Dipende: libgcc1 (>= 1:4.1.1-21ubuntu1) ma 1:4.1.1-13ubuntu5 è installato
Dipende: libpango1.0-0 (>= 1.15.1) ma 1.14.5-0ubuntu1 è installato
Dipende: libpng12-0 (>= 1.2.15~beta5) ma 1.2.8rel-5.1ubuntu0.1 è installato
Dipende: libslang2 (>= 2.0.6-3) ma 2.0.6-2 è installato
Dipende: libstdc++6 (>= 4.1.1-21ubuntu1) ma 4.1.1-13ubuntu5 è installato
libxml2: Dipende: libc6 (>= 2.5-0ubuntu1) ma 2.4-1ubuntu12.3 è installato
libxml2-dev: Dipende: libxml2 (= 2.6.26.dfsg-2ubuntu4) ma 2.6.27.dfsg-1ubuntu1 è installato
E: Errore, pkgProblemResolver::Resolve ha generato uno stop, questo può essere causato da pacchetti bloccati
E: Impossibile correggere le dipendenze

Impossible to correct the dipendecies......

Please.....someone to help me.....thank you in advance!

---

### Post by aysiu on 2007-02-19
Dependency problems usually stem from conflicting repositories.

Get a fresh set by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then do ```
sudo aptitude update
sudo apt-get -f install
sudo aptitude install avidemux
```

---

### Post by SadaraX on 2007-02-19
This is not perfect, but this might help. This is a build by me of Avidemux that seems to work under Edgy.


First you need to remove the old Avidemux. Run 'sudo apt-get remove avidemux' to remove it. Next download and install this deb file.
[http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb](http://students.washington.edu/cdobrich/avidemux_2.3.0_i386.deb)

If my copy does not work, you can also try getting a DEB file from getdeb.net. Good luck

---

### Post by remakeit on 2007-02-22
I can't remove Avidemux.....apt-get get an error where all packages must be unistalled..... :(      included kdelib and more.......
Thank you for your help!

---

### Post by sheepshearer on 2007-02-22
how about...

```
dpkg -r --purge <your package>
```

it will leave you with dependency problems. but hey, you have them already!

---

### Post by remakeit on 2007-02-25
Thank you a lot.....

With these commands :

sudo aptitude update
sudo apt-get -f install
sudo aptitude install avidemux

i had resolve my problems......
Thank you again.... :guitar:

---

