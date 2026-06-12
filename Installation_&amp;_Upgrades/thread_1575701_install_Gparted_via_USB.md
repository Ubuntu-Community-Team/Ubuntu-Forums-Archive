---
title: "install Gparted via USB"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by Gasmix on 2010-09-16
Hello,

We are trying to get GParted onto a fresh Ubuntu install but we have no internet connection as yet on the desktop.  We are trying to d/l from Sourceforge via an internet enabled laptop (running windows) a file / pkg. that can be transferred on a USB drive and ultimately installed on the new Linux machine.  We are having trouble...

How can we get Ubuntu to install Gparted from the USB flash drive?

---

### Post by lechien73 on 2010-09-16
You can download the deb file for GParted from: [http://packages.ubuntu.com/lucid/gparted](http://packages.ubuntu.com/lucid/gparted)

Be warned, though, there are quite a few dependency files, which you will have to download as well if they're not already installed.

I thought that GParted was installed by default, when I installed 10.04. Maybe that's just my selective amnesia kicking in again, though ;)

---

### Post by ajgreeny on 2010-09-16
Go to [http://packages.ubuntu.com/lucid/gparted](http://packages.ubuntu.com/lucid/gparted) on the windows machine and you can download the .deb packages for gparted, including any dependencies you need but do not already have on your ubuntu machine.

These can then be installed from the folder on the USB drive with ```
sudo dpkg -i /path/to/USB/folder/*.deb
```

EDIT:

Too slow again!
@ lechien73, gparted is on the live CD but does not get installed into the OS, unfortunately.

@ OP,  I think the most likely dependency that will not already be installed is **libparted0**, butcheck your machine with the list on that link we both gave you, and see what you don't have already.

---

### Post by lechien73 on 2010-09-16
> **ajgreeny said:**
> 
Too slow again!
@ lechien73, gparted is on the live CD but does not get installed into the OS, unfortunately.

Yours was a much more detailed reply though :)

I suppose I must have installed GParted when I was deleting my home partition. It's just another memory retrieval failure for me!

---

### Post by Gasmix on 2010-09-17
Thanks for replies.  We managed to d/l linux driver for USB modem and config a connection.  The rest was easy.  Gparted installed.

cheers,

---

