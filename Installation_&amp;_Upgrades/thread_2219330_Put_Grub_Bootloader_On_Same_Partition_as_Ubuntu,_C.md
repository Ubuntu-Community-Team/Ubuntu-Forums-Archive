---
title: "Put Grub Bootloader On Same Partition as Ubuntu, Can't get it to start"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by LawrenceVern on 2014-04-23
So basically I installed ubuntu on a random partition on a different hard drive (I normally use windows), as a side project, and didn't want my computer booting to grub every time, so I put grub on the same partition as Ubuntu itself. I've tried both booting off the different hard drive and using easyBCD to boot to it [IMG]http://i.gyazo.com/2b09d5c1ea1adefbc5cd1799dc596f83.png[/IMG], but I can't seem to get ubuntu (or grub itself) to start up. Anything that you guys can think of that might work?

---

### Post by Double.J on 2014-04-23
Hi there!


hmm this is interesting - it definitely can work - I've used easy bcd for years with grub on ubuntu's partition with no error. Just a thought, but in your pic it shows you using grub legacy setting? Does it make any difference choosing grub 2? Like I say it's probably going to come down to something simple; I've used it with linux and bcd since '09/'10


Jj

---

### Post by Luke M on 2014-04-23
First question is, did grub actually get installed in the partition boot sector?

[Verify that /sdb2 is the correct drive/partition]
sudo dd if=/dev/sdb2 of=dump bs=512 count=1
hexdump -C dump

---

### Post by oldfred on 2014-04-23
If you have two hard drives just install grub to the MBR of sdb and keep the Windows boot loader in sda.
Then you do not need EasyBCD.

You can set BIOS to boot grub on sdb. Or just use one time boot key to choose which drive to boot.
And at anytime since Windows boot loader still is in sda, you can directly boot it.

You do have to go back and install grub to sdb not the partition on sdb.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If you install Boot-Repair do not use auto fix. That installs grub to every hard drive and you do want to keep Windows boot loader on Windows drive.

---

