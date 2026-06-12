---
title: "Telling Xubuntu not to use CD"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by CalcProgrammer1 on 2007-02-13
I'm having trouble installing xubuntu on an old PC.  It installs but without xfce or x server.  I'm stuck at terminal.  When I do apt-get install xubuntu-desktop, it loads some files from the Internet and others from the CD.  Problem is, that this computer has trouble reading the CD and says that the md5 check failed on all of the files its trying to get from CD.  I opened the apt's cdrom list in nano and erased it, but now apt-get is saying it needs the CD.  How do I make it get all files from the Internet and not use the CD?

---

### Post by taurus on 2007-02-13
Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and put a # in front of the first line, CDROM.  That would comment out the CD-ROM thing.  Then run

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by CalcProgrammer1 on 2007-02-13
Thx a lot :).

Seems to be working, it's currently installing stuff.

---

