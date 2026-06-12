---
title: "Intall GRUB in a logical partition"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by jesusrop on 2007-11-19
I have the following partitioning:

sda1 40 GBy NTFS bootable for Vista
sda2 30 GBy NTFS for XP

sda3 Extended
sda5 1 GBy SWAP Logical
sda6 9 GBy EXT2 for kubuntu Logical

sda4 30 GBy NTFS for data

I would like to install GRUB to sda6 in orther to boot from there and use the vista bootloader (I use mainly windows and don't want to run trough 2 boot menus every time I boot). How do I do this?

Tried to manually install GRUB to sda6, sda0,6 and every possiible convination with sda and a 6 I could gess without succes.

Any hel please??

---

### Post by torgrot on 2007-11-19
You would tell Grub to put in (hd0,5)  I got to that from the fact you appear to only have one disk drive hd0 in grub terms,  and you want to put it in the sixth partition which in grub numbering from zero is 5  You might want to check out this page for more help

[http://users.bigpond.net.au/hermanzone/p15.htm#splash](http://users.bigpond.net.au/hermanzone/p15.htm#splash)

torgrot

---

### Post by quall on 2007-11-22
Hello, I am having a similar issue as the OP and hoping someone could help.

I want to keep my current bootloader, NTDLR, and would like to install grub on my linux partition's boot sector...which is (hd0,2) or /dev/sda3. I do not want it to touch my MBR and want to keep NTDLR.  

I installed ubuntu with the included installer, and since the only option was to either install grub or not, I chose not to, since it would have gone onto my MBR.

I booted to the LIVE CD after, which I then tried to install grub to the specified linux partition:
```
ubuntu@ubuntu:~$ grub-install /dev/sda3
Could not find device for /boot: Not found or not a block device.

```

I then tried to install in grub:
```
grub> setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

```

The files do not exist because I did not want to install grub on the MBR, and skipped the original grub install. How do people install grub onto a partition without stage1 or stage 1.5?

---

### Post by quall on 2007-11-23
I think I can recall how I did this setup on my laptop way back.
1. backup the mbr, currently containing NTDLR
2. install ubuntu and allow grub to install onto the mbr
3. make another copy of the mbr which now has grub
4. restore the original mbr, copy the grub mbr onto windows C drive
5. add an entry into NTDLR to boot the mbr copy containing grub.

I will see how it works out and post in case anyone else has a similar issue.

---

### Post by quall on 2007-11-23
Well, turns out that the installer automatically added windows as a boot option. I had a great deal of trouble with booting windows under grub last time, and it was just easier to boot linux with NTDLR. I decided to just keep grub. The Ubuntu install is really nice I must say :) 

However, I am fairly confident that my method above would have worked, except instead of creating a copy of the grub MBR and booting to it with NTDLR, a copy of the linux partition's boot sector would have been just as good.

---

