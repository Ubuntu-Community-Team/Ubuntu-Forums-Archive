---
title: "Dual boot RAID Vista / Ubuntu on drive 3 with Grub"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by ryanfx on 2007-10-28
Like the title says, I am moving to a new desktop soon where I will have a total of four drives.

3 HD's in RAID 5 (mobo raid... I know I know.....) for vista

and 1 separate HD for linux.  How should I go about configuring grub to boot this system?


Thank you for  your assistance!

---

### Post by confused57 on 2007-10-28
The Gutsy installer will probably recognize your 3 drive Raid as 3 separate drives, for a total of 4 with your proposed Ubuntu drive.  I would recommend that you set the drive you're planning on installing Ubuntu as the first hard drive booted in bios, before you boot up the live cd to install.  Make a note of how the installer recognizes this drive, e.g. /dev/sdd, etc...then when you're prompted to install grub, click the "Advanced" button, then type in "/dev/sdd"(or however the drive is designated).

From my experience with helping others with a similar setup, you definitely don't want to install grub to the first Raid hard drive's mbr...when grub is installed, it "should" automatically detect your Vista install and include an entry to boot Vista.  You would need to leave your system set up to boot first to the Ubuntu drive, in order to boot Vista from grub.

If you have any problems booting Vista from grub, you should be able to go into bios and select your 1st Raid hard drive as the first hard drive booted and boot Vista from Vista's IPL on the mbr.

---

### Post by ryanfx on 2007-10-28
sounds good, when I get the new box built I will give that a shot and report back!

Thanks!

---

### Post by LESINTHELOFT on 2007-10-28
Hi i have this setup already installed (XP though) XP boots normally if I set my raid array as first boot device. How do i get it to boot from grub

---

