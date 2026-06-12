---
title: "Vmware wont install due to previous version"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by AndreasMeier on 2005-08-22
Hi there,

I read in the forum, that a converted rpm-to-deb-file of vmware will not work in Ubuntu, but a tar.gz will.
So I got the tar.gz and tried to install it,
but now I receive an error message, telling me, that a previous version was found.

I, in fact, had installed the previous version as converted rpm-to-deb-file, but uninstalled it before I tried the tar.gz.

So, what the problem here ?

Regards
Andreas

---

### Post by CameronCalver on 2007-01-26
yes i am having the same problem did u find a fix?

---

### Post by aforonda on 2007-02-21
I'm also having this problem, I'm pretty shocked how difficult it is to install vmware on Ubuntu.

---

### Post by gamerteck on 2007-02-21
Did you search your system for VMWARE?  Sounds like you have some residual files in one of the directories.  I would check your /bin and /lib for vmware.

*EDIT*
Wow, I just realized how old this thread was, didn't look at the first post date till now :P.

---

### Post by zvacet on 2007-02-21
Search in etc,etc/init.d,tmp.home,usr/bin and delete every vmware file or folder.
```
sudo rm -r filename
```
After that just reinstall.

---

