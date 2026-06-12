---
title: "Updating with slow internet connection"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by leoncius on 2012-02-04
Hi all!
I'm about to install Kubuntu 11.10 on a couple of machines (A & B) that have slow internet connection (I've downloaded the CD image at another place (C) with a faster connection). My question is whether there is a way to download proper updates for A & B at location C and then burn them to a CD and apply them to A & B.
Thanks!

---

### Post by jerrrys on 2012-02-05
There are several ways to do that.  Here is one:

[http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/](http://rxezlqu.wordpress.com/2010/02/15/updating-ubuntu-on-slow-connectionsoffline/)

[ATTACH]212088[/ATTACH]

---

### Post by oldfred on 2012-02-05
A couple more suggestions, I have not used any of them.

Offline Updates:
[http://keryxproject.org/](http://keryxproject.org/)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

### Post by leoncius on 2012-02-05
Thank you guys! That's what I needed.

---

