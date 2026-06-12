---
title: "problem with &quot;build-essential&quot; ???"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by BrutalGrinder on 2007-10-02
Hi!
I'm desperate... I want to install "build-essential" but I don't get it...
if I write  apt-get install build-essential   it returns:

build-essential:
 Dipende: libc6-dev ma non sta per essere installato o
   libc-dev
 Dipende: g++ ma non sta per essere installato


if I try with "libc6-dev" it returns:

libc6-dev:
  Dipende: libc6 (=2.5-0ubuntu14) ma 2.6.1-1ubuntu4 verrà installato


if I try with "g++" and returns:

g++:
 Dipende: g++-4.1 ma non sta per essere installato



Help me please!!!!!

---

### Post by Rui Pais on 2007-10-02
Hi,
you have installed a libc6 not-compatible with your Ubuntu version (the gutsy one over feisty).

Thats dangerous and can lend to full borked system (have you played with automatix or mix gutsy kernel with feisty?)

Try to download the corrects deb poackages from [here]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libc6&searchon=names&subword=1&version=feisty&release=all"), and then install it with:
```
sudo dpkg -i libc*.dev
```

Good luck

---

### Post by BrutalGrinder on 2007-10-02
sorry... I'm a newbie...
my architecture is i386, wich is the link for me? What i do?

:(

---

### Post by Rui Pais on 2007-10-02
> **BrutalGrinder said:**
> sorry... I'm a newbie...
my architecture is i386, wich is the link for me? What i do?

:(

click on links that say feisty... and choose i386 package.
That will take to a list of mirrors to download the package.
[Here for libc6]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.5-0ubuntu14_i386.deb&md5sum=93f5e50c41abfaeac5963a448b9881e0&arch=i386&type=main").

---

### Post by BrutalGrinder on 2007-10-02
it say that there is a newest version installed...

H-E-L-P!!!!

---

### Post by Rui Pais on 2007-10-02
try:
```
sudo dpkg --force-downgrade -i libc*.dev
```
or
```
sudo dpkg --force-overwrite -i libc*.dev
```

---

### Post by BrutalGrinder on 2007-10-02
nothing...
it reports:

dpkg: errore processando libc*.dev (--install):
 impossibile accedere all'archivio: Nessun file o directory
Sono occorsi degli errori processando:
 libc*.dev


impossibile to access to archive...

:(:(:(

---

### Post by Rui Pais on 2007-10-02
> **BrutalGrinder said:**
> nothing...
it reports:

dpkg: errore processando libc*.dev (--install):
 impossibile accedere all'archivio: Nessun file o directory
Sono occorsi degli errori processando:
 libc*.dev


impossibile to access to archive...

:(:(:(

You must type the command on the same directory of the downloaded deb package.
If for some reason the * produce a failure try with complete name. Tab completion avoids typos.
Write on correct path:
```
sudo dpkg --force-downgrade -i libc
```
then press TAB key for automatic completion of package (if don't complete the name you are not in the correct path).

Please note that i never tried those flags myself. I presume that they do what the names seems to imply. Broken libc is one of the worst problems that one can have, so act with care, search a lot in forum in google for ideas and other reports, and hope for the best. You will find people that have re-installed the OS just because a borked libc end up in a full broken system.

Good luck.

---

