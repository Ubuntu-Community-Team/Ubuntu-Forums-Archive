---
title: "aptitude install from local usb drive"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by davmaz on 2007-05-24
Hi - I've downloaded and created 4 directories on a USB drive that contain ALL of the current ubuntu packages.  I can mount it, but I can't get aptitude to go to the usb drive to find packages I want to install.

Do you know an option for aptitude, or another program that I can tell to look on the USB drive for the source?

Thanks!

---

### Post by shad0w_walker on 2007-05-24
There are two ways you can do this. If you feel comfortablte installing them from a command line you can use dpkg

If you want to install using synaptic, you can run 'gksu nautilus' and copy the contents of the folders into the folder:  /var/cache/apt/archives/

Aptitude wont automatically install the new packages this way but you can select them and install from the packages so it doesnt try to download them.

If you want instructs for DPKG (It will let you install all the packages with out having to select each one by hand from synaptic) then let me know and i will write up some instructions.

---

### Post by davmaz on 2007-05-24
I don't mind using the command line (dpkg), but it's not clear how to do that...

Can you give me an example? For instance, I have 4 DVD sized directories on my usb drive, mounted as /media/usb/ubuntu-dvds/ubuntou0,1,2,3
Those are the ones I want to use.

---

### Post by davmaz on 2007-05-24
I even tried editing /etc/apt/sources.list and put entries like
deb file:/media/usb/unbuntu-dvds/unbuntu0/ feisty main restricted
but it still went to the S L O W us.debian.org

---

### Post by trippinnik on 2007-05-24
even easier open up Synaptic click File then Add downloaded packages.  You can then select your usb disk's directory.

---

