---
title: "[SOLVED] apt-get install prompting for cd to be loaded"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by Ba66e77 on 2007-12-18
I'm running the server version of 7.10 and when I try to install screen and curl, I'm getting prompted to insert the initial install disk.  What's the story with that?  Why is it not fetching the packages for the online repository?  If I didn't have a necessary repository enabled, it just wouldn't find the package, right?

barrett@igor:~$ sudo apt-get install curl screen
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libcurl3
The following NEW packages will be installed:
  curl libcurl3 screen
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/944kB of archives.
After unpacking 1688kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

---

### Post by njparton on 2007-12-18
Do you have all the online repos enabled? Including universe and multiverse?

---

### Post by taurus on 2007-12-18
Edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, make sure there is no # in front of all the lines that start with **deb** & **deb-src**.  Save it and run

```
sudo apt-get update
sudo apt-get install curl screen
```

---

### Post by Ba66e77 on 2007-12-18
Thanks, taurus.  That got it.

---

### Post by gfd_2 on 2007-12-18
you could also open Synaptic open the box for Repositories and uncheck the box at the bottom to ensure the system won't try to read off the install CD.

---

### Post by taurus on 2007-12-18
> **gfd_2 said:**
> you could also open Synaptic open the box for Repositories and uncheck the box at the bottom to ensure the system won't try to read off the install CD.

BUT he is running a server version so there is no synaptic!  Everything is from a command prompt.

---

