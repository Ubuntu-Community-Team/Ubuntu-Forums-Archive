---
title: "Linux Headers + Virtual Box Installation"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by minime283 on 2008-11-11
Hi Guys,
So I tried to uninstall virtual box and add the virtualbox source to my software sources to reinstall it and when I reinstalled, I got an error, here's the error log:

Attempting to install using DKMS

Error! Could not locate dkms.conf file.
File: /usr/src/vboxdrv-2.0.4/dkms.conf does not exist.
Failed to install using DKMS, attempting to install without
Makefile:142: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.

After researching a bit I find in /lib/modules/ (Which is where I believe the linux headers are held?) It can't find the headers for my kernel. If I type uname -r it says I have 2.6.24-19-generic and that folder is in the /lib/modules/ folder but I also have folders with higher version numbers in there. If I try to apt-get install linux-headers-(that version it's asking) I get this error message 

Package linux-headers-2.6.24-19-generic is not available, but is referred to by another package.

Also, in the libs module folder there are other folders there with higher version numbers: 2.26.27-7-generic etc.

And, if I try to do apt-get install linux-headers-2.26.27-7-generic I get **linux-image-2.6.27-7-generic is already the newest version.**

Anyways, any help would be greatly appreciated, as I need to get my homework off of my virtualbox image for tomorrow :(

---

