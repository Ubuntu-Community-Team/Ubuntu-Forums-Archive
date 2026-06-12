---
title: "Detecting File System Freeze on install"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by matt_jaroz on 2008-09-09
Hi all,

I am new to linux, I have managed to get myself a free laptop but it didnt have a hdd, so my friend said try ubunutu. its a inspiron 1100 with 2.4GHz Celeron 256 RAm at the moment so went for xubuntu to start.

I have a problem on the install.  When installing, it freezes at 15% when "Detecting File System".  I cannot move the mouse, and the cd drive is firing up every few minutes but still not progressing. I have put in a 120 GB brand new hdd which it does seem to recognise. 

I have seen a few threads about this, upgrade RAM could be an answer - i have some on order but i need an os very soon!

Any help is much appreciated, Im a beginner so easy terminology would be great, many thanks

Matt

---

### Post by Tang on 2008-09-09
> **matt_jaroz said:**
> Hi all,

I am new to linux, I have managed to get myself a free laptop but it didnt have a hdd, so my friend said try ubunutu. its a inspiron 1100 with 2.4GHz Celeron 256 RAm at the moment so went for xubuntu to start.

I have a problem on the install.  When installing, it freezes at 15% when "Detecting File System".  I cannot move the mouse, and the cd drive is firing up every few minutes but still not progressing. I have put in a 120 GB brand new hdd which it does seem to recognise. 

I have seen a few threads about this, upgrade RAM could be an answer - i have some on order but i need an os very soon!

Any help is much appreciated, Im a beginner so easy terminology would be great, many thanks

Matt
Hi, Matt
Are you trying to install the 8.04 release?
I would suggest downloading and burning [Gparted live CD]("http://gparted.sourceforge.net/")

With that you can partition and format (ext3) the new drive ready for the XUbuntu install.

If Gparted doesn't 'see' the new drive, best you re-check your bios settings

---

### Post by matt_jaroz on 2008-09-10
Thanks for the help tang, 

I managed to load up Gparted.  It recognises the hdd and out of the 120gb hdd i now have a small partition (~700mb) and the rest formatted as ext3.

though when i try and install, when using change partition (guided) on the install, it says too small eventhough the xubuntu partition in 110gb! i increased the other partition to 10% and it seemed to freeze.

maybe i will try again tomorrow, when i try the normal guided partition to use the whole disk it freezes at 15% as usual!!

grr. i'll get it sorted in the end!!

---

