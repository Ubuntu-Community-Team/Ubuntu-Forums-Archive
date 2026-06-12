---
title: "How much disk space for Ubuntu"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by pgte3 on 2008-07-23
The Ubuntu install guide states the the minimum requirements for an install of Ubuntu 8.04 is at least 4 GB of disk space (for full installation and swap space).

If I install Ubuntu, that is download...

[http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-i386.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.1-desktop-i386.iso)

and do a non-custom install. How large should a Ubuntu partition be to hold this install and have some room for updates and some new packages?

Application data will be stored in another partition which will be mounted.

---

### Post by Pumalite on 2008-07-23
Are you talking USB? 4 GB will do.

---

### Post by pgte3 on 2008-07-23
I was not thinking USB...I was talking about a hard drive. I am trying to get a idea of the disk needed and used by Ubuntu. I realize that number can vary greatly depending on what packages are installed.

For example how much disk is used by the intial install? How much will be need to handle updates for that install over time? Any suggestions for other growth?

---

### Post by zvacet on 2008-07-23
Depends on your available free space.You can do it this way:

1.root = 10GB                   mountpoint /
2.swap = 2xram
3.home = rest of free space    mountpoint /home

---

### Post by pmlxuser on 2008-07-23
if you let ubuntu do non custom ubuntu install, the hard sisk space is at your mercy.
but at least its recomended to have 4Gb to install Ubuntu.

You can actually mount different partition at differnt mount point like

/
/home
/var
/*** blah blah
depending on how you want your system to perfom

i remember i once mounted a partition in the /home for documents
and mounted another within /home at /Music to keep all my Music files on a separate partition but not to sho as if its a different partition (just for the love of it)

so basically you can assign as much as you want for your data.

---

