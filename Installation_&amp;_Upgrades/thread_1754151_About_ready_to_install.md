---
title: "About ready to install"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by tmette on 2011-05-09
Ok, I have two 500Gb HDDs in my computer at the moment.  One of them has my Win7 installation on it.  The other one I will use for Ubuntu 10.10.  Now, I know I am going to install it on the second HDD, but should I choose to install the GRUB on the first device?  This way the GRUB will come up every time I boot the computer?

Just want to get this right before I install.

---

### Post by Hedgehog1 on 2011-05-10
You can install it with Ubuntu on the 2nd drive and the Boot Loader on the 1st drive.  That will give you the Grub menu and the ability to select the OS from their.

You can, if you prefer, install everything (including the boot loader) on the 2nd drive and use the Bios boot selection function key to select the Ubuntu drive (it will default to the windows drive otherwise).

I personally prefer grub handling all my OS choices, so I would install the bootloader on the 1st drive (windows drive).

***The Hedge***

:KS

---

### Post by Quackers on 2011-05-10
Sadly my bios is locked so I cannot choose my second (internal) drive as a boot device. (Sony like to do that).
If I could I would have installed grub to the mbr of sdb and left sda's Windows bootloader alone.
Sadly Sony don't give me that choice, so Grub boots everything on both drives from sda.

---

