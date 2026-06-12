---
title: "libncurses5-dev error"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by JDRMP on 2010-03-10
*[SIZE=4]I have installed UBUNTU 9.10(2.6.30)[/SIZE]*
 
*[SIZE=4]I'm trying to execute the following command:[/SIZE]*
[SIZE=4]apt-get install linux-headers-`uname -r` mercurial build-essential cvs subversion libncurses5-dev[/SIZE]
 
*[SIZE=4]I get the following error:[/SIZE]*
[SIZE=4]*Package libncurses5-dev is not available, but is referred to by another package.*[/SIZE]
*[SIZE=4]This may mean that the package is missing, has been obsoleted, or[/SIZE]*
*[SIZE=4]is only available from another source[/SIZE]*
*[SIZE=4]E: Package libncurses5-dev has no installation candidate[/SIZE]*
 
 
[SIZE=4]](*,)I cannot find it anywhere in the files. [/SIZE]
[SIZE=4]Any help is greatly appreciated[/SIZE]
[SIZE=4]Thanks [/SIZE]

---

### Post by dstew on 2010-03-11
Try it on its own command line with root privleges:```
sudo apt-get install libncurses5-dev
```Do you get the same error? The package is in the Ubuntu development archive, so you should not need to activate any new repositories.

---

### Post by JDRMP on 2010-03-11
> **dstew said:**
> Try it on its own command line with root privleges:```
sudo apt-get install libncurses5-dev
```Do you get the same error? The package is in the Ubuntu development archive, so you should not need to activate any new repositories.
 
Yes same error.  I reinstalled 9,10 and it works now.  I must have installed wrong or somehow deleted the package.
 
Thanks for the help

---

