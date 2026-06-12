---
title: "Need help with Ubuntu on portable HDD"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by colecampbell666 on 2008-01-03
I am posting a new topic because I got no response in the other one.

> **colecampbell666 said:**
> Hi!
I downloaded Ubuntu (7.10) last night, and burned the live CD. I downloaded it to try it out, but more importantly to get past the security at my school, by having it on my portable HDD. As my USB HDD (WD Passport 250 Gb) locks up my desktop on bootup, I decided that I'd have to use my mom's laptop to install it. I put in the live CD, and on the desktop clicked install. I followed the instructions and selected my USB drive, deciding to format 200 Gb and leave 50 NTFS, as I had some important files on it. Everything seemed to go off without a hitch, and Linux works perfectly on her laptop, doing _most_ of the things I tell it to. I can't seem to install any programs from the Add/Remove window. When I click on a program, no matter which one, it says:

[IMG]http://i18.tinypic.com/8bxyz3q.png[/IMG]

This is not the least of my problems, when I remove my HDD and try to boot XP, the GRUB1.5 screen appears with an "Error 21". I'm certain that I installed Ubuntu to my USB HDD.

The main reason that I'm posting: It doesn't work at school. The majority of school PCs are Dell Optiplex gx620s, with some HPs, (not sure which model) and on the Dells Linux doesn't load. I select "USB device" in the utterly crap BIOS, and it refuses to load. I've heard of a GRUB bootdisk, is this what I need?

Thanks in advance for any replies!

[color=red]EDIT: OK. As I've now learned GRUB apparently gets loaded onto the main HDD a.k.a my mom's laptop. I don't know how to remove the GRUB partition. I didn't understand the directions for installing GRUB to the root (presumably Ubuntu) directory. If I do this, it should make Ubuntu auto-load on any PC if the BIOS is set, correct?

Another thing - Firefox now loads, but closes the second it loads a page.[/color]

[color=darkred]EDIT2: I am re-installing Ubuntu, and set the boot-loader to be installed on hd1 in the advanced options. EDIT3: It is stuck at "Detecting file systems".[/color]

I really need help; my mom'll kill me if her laptop doesn't work.

---

### Post by chris_nava on 2008-01-03
Unless you select "Advanced..." on the final screen of the ubuntu install and tell it otherwise it will put grub on your primary hard drive's MBR.

This will get your MBR back and allow the laptop to boot windows properly.
[http://keyboardsamurais.de/2007/10/26/fixing-your-windows-mbr-after-fuing-it-up-with-ubuntu-or-grub/](http://keyboardsamurais.de/2007/10/26/fixing-your-windows-mbr-after-fuing-it-up-with-ubuntu-or-grub/)

< RANT >If you install on a secondary drive the installer should consider all other drives OFF LIMITS unless you approve the change.</ RANT >

---

### Post by colecampbell666 on 2008-01-03
Thanks. I used SuperGRUBDisk to reset the PC, it works fine. The laptop has one HDD, how do I set it to put GRUB on my portable HDD?

And another thing, how do I format the HDD using the Live CD? And would I need a boot disk if I were plugging the drive into a new PC?

---

### Post by colecampbell666 on 2008-01-03
OK. I figured out how to format a drive, They all have a lock icon beside them in GParted. I formatted the old Linux-Swap partition, but that's as far as I've got.

---

### Post by Gregmond on 2008-01-03
> **colecampbell666 said:**
> Thanks. I used SuperGRUBDisk to reset the PC, it works fine. The laptop has one HDD, how do I set it to put GRUB on my portable HDD?

And another thing, how do I format the HDD using the Live CD? And would I need a boot disk if I were plugging the drive into a new PC?

If you want it to work entirely off the external, I would suggest setting the cmos/bios of the PC/laptop to not see the internal HDD while you do the install, this way it only sees the external drive. Then if you tell the system to boot of the external it should work propely (*crosses fingers*).

To format the drive, from the live CD/DVD, go to the system menu, then under the administration (might be preferences, currently at work not on Linux) look for Partion Editor (gnome partion editor on 7.04 from memory). It should allow you to partion and format drives.

Gregmond 
:)

---

### Post by colecampbell666 on 2008-01-03
Thanks. My HDD is partitioned into two drives, the original FAT32 drive, and the ext3 Linux drive. I can't touch either drive on the Live CD, and when I boot the drive, and logon as root, they are still off-limits.
[img]http://img140.imageshack.us/img140/8295/hddhb7.png[/img]
This is while booting from my HDD. I can't touch either drive.

---

### Post by colecampbell666 on 2008-01-03
OK. I went onto WinXP and reformatted my drive. I went onto Ubuntu and installed it, only to hang at "5% formating ext3 drive...blahblahblah". I'm pretty sure that I caused that and I'm going to give it another go.

---

