---
title: "Upgrading a multiboot install"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by OldGreySteve on 2007-05-12
I am an experienced Windows user who has recently started experimenting with Linux.

I have a multiboot setup with Windows and Fedora on the first hard disk and Ubuntu 6.10 on the second hard disk.

I would like to update to the new Ubuntu 7.04 release.  If I do an upgrade using the update manager in Ubuntu, will my grub menu still work with the other two OSs?  Is there anything I have to do to preserve the settings?

---

### Post by starcraft.man on 2007-05-12
> **OldGreySteve said:**
> I am an experienced Windows user who has recently started experimenting with Linux.

I have a multiboot setup with Windows and Fedora on the first hard disk and Ubuntu 6.10 on the second hard disk.

I would like to update to the new Ubuntu 7.04 release.  If I do an upgrade using the update manager in Ubuntu, will my grub menu still work with the other two OSs?  Is there anything I have to do to preserve the settings?

Well, I'd back up any important data stored in Ubuntu (if you got it in seperate home partition thats good enough). Then if your upgrading, make sure to disable compiz/beryl if you have it installed and remove it from sessions, prolly easiest to just uninstall it completely. Then change your drivers back to 2d ("vesa" or "nv" in the xorg file, an easy switch out). Then after all that, I would do the upgrade to Feisty. 

Note that even doing all that may lead to some problems, so I do recommend downloading the Live or alt CD. It helps to be prepared. If you get any critical errors preventing you from booting then, you will be able to reinstall clean.

As to the question about multiboot, the upgrade should preserve your GRUB long as all goes well. Remember to put back your correct drivers and windows manager when your done upgrading :)

Hope it goes well.

---

