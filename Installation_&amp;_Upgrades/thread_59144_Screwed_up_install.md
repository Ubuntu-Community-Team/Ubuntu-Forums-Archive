---
title: "Screwed up install"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by tufyuma on 2005-08-22
I tried to install to a second HDD, so I could put it that drive into another computer that I cannot get to read the install cd or the live cd (CD's work on other computers).  Now that drive doesn't seem to work at all.  I would like to reformat and start over but the Bios sees it (as a slave or master, however I have it set) but after that it is invisible (to windows).  I would like to use it but even using it as the master it never boots up.

Any ideas??

Thanks
Jim G.

P.S.  I am a newbie to Linux, please type slow ;-)

---

### Post by MrCheese on 2005-08-23
[QUOTE=tufyuma]I tried to install to a second HDD, so I could put it that drive into another computer that I cannot get to read the install cd or the live cd (CD's work on other computers).  Now that drive doesn't seem to work at all.  I would like to reformat and start over but the Bios sees it (as a slave or master, however I have it set) but after that it is invisible (to windows).  I would like to use it but even using it as the master it never boots up.

Any ideas??

Thanks
Jim G.

P.S.  I am a newbie to Linux, please type slow ;-)[/QUOTE]

Ok, slow typing enabled ..........

First, Windows doesn't understand Linux filesystems so unless you installed Linux on fat32(!) you'll never see the disk in Windows.

Second, make sure you have the boot flag set on the second hdd so the system knows it can boot from it. You should be able to run fdisk from linux (or Windows - I think that will work too) to set the Bootable flag to on.

Hope this helps.

Paul.

---

