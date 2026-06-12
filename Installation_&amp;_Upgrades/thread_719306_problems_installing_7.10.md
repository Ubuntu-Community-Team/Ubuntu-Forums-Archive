---
title: "problems installing 7.10"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by dbo33 on 2008-03-09
I'm trying to install Ubuntu 7.10 on my system from the DVD. I am installing using the text installer and everything works fine up until the bootloaders try to install.  I have an error when i try to install Grub and/or Lilo. My system is running RAID 1 through my motherboard and i noticed that when partitioning it doesnt recognize it as a RAID setup but rather 2 individual drives, so i tried disabling RAID and installing on one of the hard drives but still had the same problem when it came to installing a boot loader. 

Any ideas? the last thing i want is to be stuck reinstalling shitty vista

my system:
Dell XPS 420
intel Q6600 Quad-Core (8MB L2 cache,2.4GHz,1066FSB)
4GB Dual Channel DDR2 SDRAM at 800MHz - 4 DIMMs
2x750GB SATA 3Gb/s 7200 RPM HDDs in RAID 1
nVidia GeForce 8800 GT 512MB
Dual Drives: Blu-ray Disc Combo (DVD+/-RW + BD-ROM) and 16x DVD+/-RW
Dell 1505 Wireless-N PCIe Card

---

### Post by Peter09 on 2008-03-09
Can you post the error message that you are getting?

PC

---

### Post by dbo33 on 2008-03-09
it was very generic i forget the exact message order but it was (the GRUB boot loader failled to install on your hard disk) then just talked about retrying to install GRUB or try another boot loader. Lilo gave a different error but same generic failed to install just worded differently.  i tried just finishing install and it gave me the message of when booting i would have to use (/vmlinuz kernel on partition /dev/sda2 and root=/dev/sda2 passed as a kernel argument) i tried making a cd with a grub and boot off that with the argument: (kernel /vmlinuz root=/dev/sda2) but i must have done something wrong there because that didn't work

if it helps heres how i partitioned it

2 GB / ext3
8 GB swap
500 GB /home ext3

---

### Post by logos34 on 2008-03-09
> **dbo33 said:**
> 2 GB / ext3
8 GB swap
500 GB /home ext3

First off, that's way too little space for root and way too much for swap.

Try ~5-7 for /
~1-2 gb for /swap
rest for /home

[This guide]("http://www.easy-ubuntu-linux.com/ubuntu-feisty-installation.html") will show you how to install with separate /home. (It's the same for gutsy).

Disconnect one of the drives before installation.  See if that helps.  You can add the other afterwards as storage or whatever.

---

### Post by dbo33 on 2008-03-10
sorry i mixed the two up, here is my partition table:

2GB swap
8 GB /
500 GB /home

and installing gutsy wasn't the problem it was installing grub or lilo as a boot loader.  I haven't tried running on just one hdd yet, that does seem like a good idea tho so im going to give that a try.

Thanks for the ideas!

 if you think of anything else please let me know, or if you know of a way i can keep running raid 1 and have gutsy recognize it during install that would be great also.

---

