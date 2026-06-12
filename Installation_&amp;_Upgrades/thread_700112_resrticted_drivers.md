---
title: "resrticted drivers"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by bvav22 on 2008-02-18
just installed 7.10 on my dell inspiron e1505, and im having some trouble enabling these restricted drivers. i went into the software sources to download the sources and enable them.  however i can only download the one for the fglrx driver and not my broadcom wireless car. AND the flgrx driver wont install, it says "Could not apply changes! Fix broken packages first"


any suggestions?

---

### Post by jan quark on 2008-02-18
to fix broken packages run 
these commands


```
sudo apt-get -f install
```

or/and

```
sudo dpkg --configure -a
```

if you have a broadcom wlan card 

( you can check this with the command ```
lspci
``` )

you can also use this small guide for enabling the wlan drivers

[http://laiconic.quotaless.com/tutorial1.html](http://laiconic.quotaless.com/tutorial1.html)

---

### Post by bvav22 on 2008-02-18
ok well after an update i got the wireless card working, but i tried both of those commands and the package is still damage for the ati card.

---

### Post by bvav22 on 2008-02-18
ok so i tried this

bvav22@bvav22-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages


then i followed these steps to install the libsdc++5 package..... (toward the bottom of page)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


however i cannot locate the ./db2setup file to finish!!!!!

---

### Post by bvav22 on 2008-02-18
ttt

---

