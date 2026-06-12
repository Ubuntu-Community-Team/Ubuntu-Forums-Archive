---
title: "Restoring Windows after installing Ubuntu"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by marcel3003 on 2012-02-08
OK, this may be more of a Windows issue, but I'll ask anyway: some time ago I wanted to install Windows 7 and Linux Mint together. I have two physical hard drives and I first installed Windows to the second one and it also created 100 MB "System Reserved" partition on the first hard drive that was probably used for booting. Then I installed Mint on the first one and everything was fine: Mint and that 100 MB Windows partion were on the first drive and the main Windows 7 partition on the second, and I could boot into Windows using GRUB. But after some time I thought about replacing Mint with Ubuntu, so I installed it on the first drive. The problem is, I had completely forgotten about that 100 MB Windows partition and let Ubuntu use the whole drive, thus deleting that partition. After installation, Windows 7 did not appear in GRUB. However, with help of some online guide I've managed to add an entry that points to it, but it still doesn't want to boot, displaying "BOOTMGR missing" message. Using Windows DVD to repair booting also doesn't work: "bootrec /rebuildbcd" detects Windows installation, but when I try to activate it, it says "The volume does not contain a recognized file system. Please make sure that all required file system drivers are loaded and that the volume is not corrupt. ". Chkdsk doesn't change anything and I've also tried using diskpart to activate the partion or expand filesystem, but it doesn't help either. I've even installed Windows on VirtualBox and tried to copy the boot files from System Reserved to that main Windows partition, but they don't work, probably because they point to a location that now doesn't exist. Is there any hope for saving me from doing a Windows reinstall? Please help.

---

### Post by darkod on 2012-02-08
One thing you might be missing, you have to have the boot flag on the correct partition.

In fact, because windows is very "stupid" about anything out of the ordinary, what I would do is:
1. Temporarily disconnect the ubuntu disk.
2. Go into BIOS and set it to boot from the win7 disk in case it doesn't automatically (with only one disk present it should be automatic).
3. Boot with the Ubuntu cd in live mode, open Gparted and look if the boot flag is activated on the win7 partition. In case it's not, do a right-clik, Manage Flags and set it.
4. Then reboot with the win7 rescue disc and try the automated repair process few times. Failing that, try the manual commands again.

With a little luck it will create the boot files when it detects the installation and the boot flag. Check that win7 boots fine.

After that simply connect the ubuntu disk, set BIOS to boot from it and once inside run:
sudo update-grub

to detect the win7 boot files.

---

### Post by marcel3003 on 2012-02-10
It worked! Thank you!

---

### Post by darkod on 2012-02-10
No problem, glad you got it going. Please mark the thread as solved in Thread Tools above the first post.

---

