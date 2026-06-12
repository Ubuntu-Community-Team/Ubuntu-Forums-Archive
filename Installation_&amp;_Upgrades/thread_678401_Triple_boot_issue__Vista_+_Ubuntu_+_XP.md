---
title: "Triple boot issue :: Vista + Ubuntu + XP"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Stibily on 2008-01-25
Hi.

I currently have a dualboot system with Vista Business and Ubuntu 7.10. However, I am now looking to install XP. I have allocated 10GB freespace for the install, however, whenever I choose this as the installation partition during the XP installation it says I have reached the maximum number of partitions for the hard disk. I assume this is because Vista has a recovery partition which was preinstalled and Ubuntu has a Swap partition. So my question is this:

Do I require the Ubuntu Swap partition? If so, is it possible to move it to the Ubunutu partition or is it separated for a reason? *And for the Vista people - do I need the Vista Recovery partition if I have the original Vista disk, which includes recovery tools?*

As you may tell, I am desperate to allow myself this extra partition but I am clueless on how!

Any comments are greatly appreciated!

Many thanks.
::Tom

---

### Post by benanzo on 2008-01-25
The error you are receiving is due to the fact that an MBR-based disk can only have four primary partitions.  I believe all versions of Windows are required to be installed on a primary partition in order to be bootable.  I would advise you to create an *extended* partition at the end of the disk for the Ubuntu swap and install XP on the now-freed primary partition.  You can have as many extended partitions as you want.

---

### Post by Stibily on 2008-01-26
Thank you very much for the information. I have decided however to remove the Vista Recovery partition as I have it on DVD anyway, and use this as a primary partition for installing XP.

I will inform you of the result ;)

::Tom

---

### Post by Stibily on 2008-01-26
Ok. I decided to remove the Vista Recovery partition and I went ahead with the XP install. I now have Vista bootloader working with Vista and XP both showing up. I used EasyBCD to add XP to the list. However, I wish to have the good ol' Ubuntu GRUB menu back.

How can I reinstall GRUB so that it recognises all 3 OS's?

***UPDATE***
I have now successfully reinstalled Ubuntu's GRUB. The current set up is:

-------------------------------
Ubuntu 7.10
Ubuntu 7.10 :: Recovery mode
Ubuntu 7.10 :: mem... test

Other systems:

Windows...
-------------------------------

I have told the "Windows..." option above to load Vista, which loads its bootloader containing Vista and XP.

Many thanks for all input.
::Tom

---

### Post by chazaw on 2008-03-22
I used the Super Grub Disk to fix this.

---

