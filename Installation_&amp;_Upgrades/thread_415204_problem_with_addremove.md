---
title: "problem with add\remove"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by redneckracin on 2007-04-20
ok i select all the packages that i want but then this error pops up

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/beryl-core/libberylsettings0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/universe/b/beryl-core/libberylsettings0_0.2.1.dfsg+git20070318-0ubuntu2_i386.deb)
  Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)


I also installed automatix2 and it also seems to have issues installing and downloading packages

---

### Post by rich.bradshaw on 2007-04-20
Which version are you using? It could be that the server is hammered because of people upgrading to Feisty...

Unlikely, but possible. Does the internet work etc?

---

### Post by redneckracin on 2007-04-20
yeah I get the internet just fine.

Like with Automatix2 it has downloaded all the packages and stuff but then just doesn't want to install my stuff.

add\remove just doesn't want to download anything at all.

---

### Post by Ambimom on 2007-04-20
Check your sources list found in the file system under: /etc/apt/sources.list

This is mine:

> 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

   

If you want to edit the source list then open a terminal and type:
> sudo gedit /etc/apt/sources.list  

Remember to save the file text that appears with a filename you'll remember in case you need it again.

If your sources list is markedly different than the one above, try replacing yours with this one. 

Try to download again.  

If it doesn't work, then go back to the original.  It's worth a try.

Good luck.

---

### Post by mindaslab on 2007-04-21
I'm using 7.04, and i get the same problem!!

I think its the problem with the server

:guitar:

---

### Post by mindaslab on 2007-04-21
Hey !!! It has worked for me without any modifications. Just think its the problem with the server.

:guitar:

---

