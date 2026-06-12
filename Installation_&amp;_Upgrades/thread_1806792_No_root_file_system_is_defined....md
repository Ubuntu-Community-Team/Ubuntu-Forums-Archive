---
title: "No root file system is defined..."
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by aesh60 on 2011-07-18
**I tried to install Ubuntu 11.04 and when I need to choose partition to install, that  ****problem is showing me :**
[B]
> No root file system is defined.

Please correct this from the partitioning menu.


I tried  to change the file system to swap area but isn't helpful.[/B]

**Shaked**

---

### Post by westie457 on 2011-07-18
> **aesh60 said:**
> **I tried to install Ubuntu 11.04 and when I need to choose partition to install, that  ****problem is showing me :**
[B]



I tried  to change the file system to swap area but isn't helpful.[/B]

**Shaked**

In the partitioning screen is a box marked 'USE AS'. Click here and select the first option from the menu. It is just a   /    nothing else. / is the symbol for root.

---

### Post by aesh60 on 2011-07-18
> **westie457 said:**
> In the partitioning screen is a box marked 'USE AS'. Click here and select the first option from the menu. It is just a   /    nothing else. / is the symbol for root.

[B]I try what do ypu say and still have this error 
additional I look up google and see that should to create new partition  in the size between 2 - 4GB [/B]

---

### Post by westie457 on 2011-07-18
Here is a rough guide to installing.
During the install setup process select various things pertinent to your location. IE Time zone and keyboard and language.
In the where to install screen optons are there to install side by side with other OS, use the whole drive (this wipes everything off). The last option here is called Something Else, in this one you get to choose which drive and partition to use. If you choose to use the partition that already has an EXT3 or 4 file system on in the box with Do Not Use change this to EXT4 tick the small box to format and then in the box Use as select / . if you have separate partitions for /boot /swap and /home these will need to be formatted as well. Click okay/forward/continue. A warning box will appear about losing data and changes being written to disk. Clicking Accept also mean these changes cannot be undone and the install goes ahead. After a while a prompt about Grub should appear accept the default unless you have an esoteric disk arrangement and want/need Grub somewhere else. A short while after this a prompt to reboot shows. Click okay.
If the install was from a CD you have chance to eject it.
If from USB you will need to change bios settings to put the USB after the hard drive. Voila a brand new install of Ubuntu.

Back-tracking slightly... If you already have an EXTx (x= 2,3 or 4) there is no need to format unless you want a clean install or if you change the EXT.

---

