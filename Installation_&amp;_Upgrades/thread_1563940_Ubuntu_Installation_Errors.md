---
title: "Ubuntu Installation Errors"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by dabluebery on 2010-08-29
Hi:

I'm brand new to UBUNTU and Linux. I just inherited a computer with a locked Vista operating system that I decided could be my blank slate for a UBUNTU installation.

I'm getting this error message as UBUNTU starts its thing:

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1uuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

**

I should mention that I got this error once already, and thought maybe the existing partitions on the hard disk might be getting in the way, so I used "killdisk" to erase the drives and start from scratch. I also had to change the SATA operation from "AHCI" to "ATA" to get the killdisk boot cd to work. I have since reverted to AHCI.

The computer is a Dell with the Intel Core 2 Duo 3.0 ghz processor.

I've done some basic VBA programming and can write pretty complicated spreadsheets but that's the extent of my knowledge. I have very little hardware experience and have never used linux before [except on my android smartphone, haha] and never on the back-end so please be patient if I don't understand what you're asking me to do.

Thanks in advance.

---

### Post by dabluebery on 2010-08-30
I spoke with a friend on the phone earlier who said that the error I'm getting sounds like the CD I'm using for the image didn't write properly or maybe it is having a conflict with the cd drive of the destination computer. He suggested writing the UBUNTU ISO file at the lowest speed possible and trying again.

Am I on the right track? This guy knows more than I do but I don't know enough to trust what he's saying.

---

### Post by Rubi1200 on 2010-08-30
> **dabluebery said:**
> I spoke with a friend on the phone earlier who said that the error I'm getting sounds like the CD I'm using for the image didn't write properly or maybe it is having a conflict with the cd drive of the destination computer. He suggested writing the UBUNTU ISO file at the lowest speed possible and trying again.

Am I on the right track? This guy knows more than I do but I don't know enough to trust what he's saying.
Your friend may well be right.

Also, check the MD5SUM of the CD:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

It would also be helpful if we knew the computer specifications, especially RAM and graphics card.

Thanks and good luck :)

---

### Post by dabluebery on 2010-08-30
There's 2 gig of DDR2 SDRAM installed, two 1 gig sticks. I don't see where to get any info about the graphics card from the bios, if you really want it I'd need furthur instruction.

I burned a copy of the disc at the slowest possible speed and I'll see how that does first, I'll also try the md5sum tool. Thanks.

---

