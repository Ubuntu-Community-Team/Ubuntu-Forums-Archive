---
title: "Dell Inspiron 2650 Xubuntu install blinking cursor on boot"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by reyemtm on 2010-01-22
I have an old laptop, and am a basic linux user, but this install is crazy. I know that I have to have acpi=off to work, and got Linux Mint 7 installed from the live cd but want Xubuntu. The Xubuntu 9.1 live CD works fine as long as I put the acpi=off parameters in the boot string, and I check the additional options just to be sure. But after install I cannot even get into the grub, it says grub loading for a split second then blinking cursor.

No hardware issue because the live cd works fine, Linux Mint worked fine and XP worked fine before I deleted it. Ideas?

---

### Post by reyemtm on 2010-01-22
Okay, found the hidden grub menu  - WHY is this hidden? - by pressing shift, then edited the grub with acpi=off, now how do I make that permanent?

THX

---

### Post by bomasro on 2010-02-03
I am playing with my old Dell Inspiron 2650.   Installing Xubuntu 9.1 with acpi=off and everything seems to be going well.  This will be a dual boot system with XUBUNTU9,1 ON ONE PARTITION AND uBUNTU8.1 on another to compare which is better and see if I can notice any performance improvement using XUBUNTU.  

The Ubuntu 8.1 worked fine with no 3D Nividia proprietary driver installed.  However when I tried intalling the 3D Nividia proprietary"96" linux driver the LCD screen hung up and I had to backtrack to the Vesa driver.  Now I didn't try this with the acpi-off set.  Passiby this would make the proprietary driver work?? Anybody know?

---

