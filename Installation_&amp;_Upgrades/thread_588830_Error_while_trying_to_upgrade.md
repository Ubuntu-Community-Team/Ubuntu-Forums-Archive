---
title: "Error while trying to upgrade"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Fiki on 2007-10-23
I tried to upgrade from ubuntu fiesty to ubuntu gutsy through the automatic updater after getting all necessary updates. When it gets to the end of the downloading process i get this error:

Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.bz2](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.bz2](http://packages.dfreer.org/dists/feisty/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I can't get it to work and although it suggests there is a problem with my network connection i know this isn't true. I tried using the alternative cd to update my system but that failed as well. Any suggestions?

---

### Post by Fiki on 2007-10-23
Also, is there any easy way to upgrade from a non 64-bit OS to a 64 bit OS. I know my processor supports 64 bit but I didn't know enough about 64 bit at the time so i chose not to install that version. Is it possible to upgrade to the 64 bit version of gutsy without losing anything i currently have?

---

### Post by ixtlenet on 2007-10-23
Yes i get the same error just now when i try to upgrade to 7.10....

can anyone shed some light please... ?

---

### Post by Fiki on 2007-10-31
bump^

---

### Post by PmDematagoda on 2007-10-31
Please post your sources.list file using:-

```
sudo gedit /etc/apt/sources.list
```

---

### Post by PmDematagoda on 2007-10-31
> **Fiki said:**
> Also, is there any easy way to upgrade from a non 64-bit OS to a 64 bit OS. I know my processor supports 64 bit but I didn't know enough about 64 bit at the time so i chose not to install that version. Is it possible to upgrade to the 64 bit version of gutsy without losing anything i currently have?

No, you will have to reinstall, you cannot upgrade a 32bit OS to 64 bit.

---

### Post by zvacet on 2007-11-01
```
gksudo gedit /etc/apt/sources.list
```

and put # sign in front of that two lines.Save and close.

```
sudo aptitude update
```

---

