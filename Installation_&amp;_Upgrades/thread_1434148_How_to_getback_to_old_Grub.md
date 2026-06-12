---
title: "How to getback to old Grub?"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by jestinjoy on 2010-03-19
I installed Ubuntu Karmic in my desktop with Grub 2(Default GRUB version). It took so much time to load GRUB compared to the time when I was using Jaunty with its default GRUB.

How could I make the existing GRUB load faster or getback to the old GRUB. Please help.

---

### Post by drs305 on 2010-03-19
The long load time is often due to grub not being installed on the disk that first boots. If you can change the boot order of the disks listed in the computer's BIOS so that the drive on which GRUB is installed is the first one looked at the boot process will probably go much faster.

How to enter BIOS depends on the type of computer you have, so if you don't know how to get into the BIOS let us know. Normally it is with the DEL key or one of the function keys. You may even see a quick splash screen on boot which tells you which key to press to enter SETUP.

---

### Post by jskandhari on 2010-03-19
It usually HAppens when you update.. and the Kernel Update is also available.

Look for old-menu.lst or simillar files in the GRub folder.
View them and if you find your old Grub file in it..

Simple open the new Grub and Copy paste the old settings ( intelligently i.e. to make the changes where in possible such has Kernel version and so on.. ) :: DO THIS IN SUDO MODE else you won;t be able to Edit it :)

---

### Post by jestinjoy on 2010-03-19
Boot hard disk is the same as the place where GRUB is installed. Is there any way to change back to an old GRUB.

---

### Post by 2hot6ft2 on 2010-03-19
Check the Grub 2 Guide in my sig, if you're sure you want to do it.
Edit: Uninstalling GRUB 2 section 12

---

