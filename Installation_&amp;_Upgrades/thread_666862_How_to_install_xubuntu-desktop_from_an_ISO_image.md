---
title: "How to install xubuntu-desktop from an ISO image?"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by login failed on 2008-01-13
I only have a 5.10 Ubuntu installation CD, so I installed in server mode and upgraded one version by one version to 7.10. Now I need to install xubuntu-desktop, and I've downloaded the iso image of xubuntu 7.10. I don't want to aptitude every package again from internet, because the speed is poor. I tried to extract the iso to a location and edit sources.list 

> deb /home/ntu7.10/ gutsy main restricted 

but it didn't work. How could I install xubuntu-desktop from the Xubuntu installation ISO image?

---

### Post by ryanVickers on 2008-01-13
can you enable using a CD as a repository in Synaptic? then mount the ISO and try installing the xubuntu-dekstop (from CD of course ;))

---

### Post by santiagoward2000 on 2008-01-13
Or if you prefer a command, just open a terminal and type:
```
sudo apt-cdrom add
```
Then, just install Xubuntu:
```
sudo aptitude install xubuntu-desktop
```
That should do it.
Cheers!

_EDIT:_
I forgot to say you should burn the .iso to a CD for this. I don't know how to do it straight from the .iso.

---

### Post by login failed on 2008-01-14
Thanks. Followed [this article]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html"), I mounted the iso image to /media/cdrom:

> sudo modprobe loop
sudo mount 7.10.iso /media/cdrom -t iso9660 -o loop

Then, I tried your tip and added cdrom to sources.list:

> 
sudo apt-cdrom add

so my sources.list became:

> # deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) gutsy main restricted
# deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
# deb [http://th.archive.ubuntu.com/ubuntu](http://th.archive.ubuntu.com/ubuntu) gutsy-security main restricted

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted


But, when I was trying to 

> sudo aptitude install xubuntu-desktop

I got errors:

> Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
Couldn't find any package whose name or description matched "xubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...


Was there any step wrong?

---

### Post by santiagoward2000 on 2008-01-14
Is the .iso from a LiveCD or an AlternateCD? I'm not sure if you can do it from a LiveCD.

---

### Post by login failed on 2008-01-14
The full name of this iso image is:

> xubuntu-7.10-desktop-i386.iso

Is this image OK? Or should I download the Alternate iso image?

---

### Post by login failed on 2008-01-14
OK. I shall try the alternate image first.

---

### Post by login failed on 2008-01-14
Hi, I tried the alternate image, it works! Thank you very much for your help!

---

### Post by santiagoward2000 on 2008-01-14
> **login failed said:**
> Hi, I tried the alternate image, it works! Thank you very much for your help!

You're welcome! :KS
I'm glad I've helped!

---

