---
title: "Attempting to create USB Install drive in Startup Disk Creator"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by jbh54enwiler on 2018-09-22
I have bought a brand new 16GB USB drive specifically to set up as a boot drive for Ubuntu.  However, when I plug it in and launch the Startup Disk Creator app, the "Make Startup Disk" button is grayed out.  I also tried several other flash drives and got the same resut.  Do I have to format the drive a specific way to get the Creator to work?

---

### Post by ajgreeny on 2018-09-22
The USB drive needs to be Fat32.

However, I suggest you use [mkusb]("https://help.ubuntu.com/community/mkusb") if you need to create the boot disk for installing Ubuntu, not Startup Disk Creator.  It is much m,ore reliable in my opinion.

---

### Post by C.S.Cameron on 2018-09-22
+1 mkusb, SDC will waist 14.5 GB of your drive space that will become unusable.

---

