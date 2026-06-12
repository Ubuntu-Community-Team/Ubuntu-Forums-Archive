---
title: "help me install a program?"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by michaelgg13 on 2008-04-18
ok i have looked everywhere on how to install tarballs but everywhere i go it nevers works and i need help. i unzip a tarball and extract the files to the desktop but i have no clue how to install them and if i sorta do i always get some sort of error that im doing something worng. (btw im trying to install a driver for my wireless card)

---

### Post by seepage87 on 2008-04-18
tarballs usually contain source code, which you would have to compile into something your computer can use.  They don't install by themselves typically.  If you can't find what you're looking for in the package manager (and you usually can), ideally what you want is a .deb file.  Where did you get this tar from?  Do they have a .deb you can get?  If you really need to install from source (which I doubt) we can help you, but there's almost definitely a better way.

---

### Post by seepage87 on 2008-04-18
Also, what wireless card do you have?  Do the drivers show up in the restricted driver manager?

---

### Post by michaelgg13 on 2008-04-18
it is a belkin wireless g fd57000

---

### Post by Ub1476 on 2008-04-18
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Personally I prefer to use Synaptic, but if it's a package with very fast development (like Deluge bittorent client), I would download a .deb file from their website. For other stuff like Avant-Window-Navigator, I add the the repositories for it's packages in System>Administration>Software Sources, and can then download it from Synaptic like with packages already added in the Debian repos (the Debian repos are those Ubuntu use and contain all the packaes you can find in Add/remove or Synapic).

If you want to install a package from terminal type:

```
./configure
make
sudo make install
```

Even though a driver doesn't install this way.. Have you checked in System>Administration>Restricted Driver Manager/Hardware Drivers?

Also post the output of the command below to see how Ubuntu recognize your wireless card:

```
lspci
```

---

### Post by michaelgg13 on 2008-04-18
they dont have a .deb for the driver(and if they did how do you install it?)

---

### Post by Ub1476 on 2008-04-18
Drivers doesn't install with a .deb. They are usually a .bin file. Still, please answer to this: 

> Even though a driver doesn't install this way.. Have you checked in System>Administration>Restricted Driver Manager/Hardware Drivers?

Also post the output of the command below to see how Ubuntu recognize your wireless card:

```
lspci
```

---

### Post by michaelgg13 on 2008-04-18
hold on let me boot up linux and check
EDIT: This is what i got from the command:01:06.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
also under driver manager thing i had my graphics card thats it and i took my computer downstares for a wired connection to install it.

---

### Post by michaelgg13 on 2008-04-18
bump

---

### Post by Sef on 2008-04-18
Don't bump until after 24 hours has gone by.   Otherwise you could get an infraction.

---

### Post by michaelgg13 on 2008-04-18
ruh roh sorry

---

