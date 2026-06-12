---
title: "Problem with libtool"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by comeback-of-the-year on 2010-02-01
Hey guys. I've found loads of useful information on here in the past so I though I would register and actually post for once. ;)

I'm currently having a problem running a tar installation. I've looked around for a solution on here but can't seem to find one. 

Anyhoo, here is my problem whilst trying to install Ogre.

```
#####:~/Desktop/new/ogrenew$ ./bootstrap
Libtool 1.4 or above is required. Aborting build...


#####:~/$ sudo apt-get install libtool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libtool is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Says I have the newest version yet still won't work. 

I tried skipping the ./bootstrap command and going straight to ./configure but then I get error messages when it comes to make. 
:(

Any ideas?

---

