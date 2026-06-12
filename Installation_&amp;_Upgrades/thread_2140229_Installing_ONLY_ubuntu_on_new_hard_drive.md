---
title: "Installing ONLY ubuntu on new hard drive"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by rumbarel on 2013-04-29
Please forgive me if this question has been answered somewhere....I looked all over and couldn't find anything.

   I have a computer with a new motherboard and a new hard drive (500GB SATA) that I want to install ONLY ubuntu on.

  What is the best way to do so?   Should I format the HD first?  and if so, what's the best method to do so?  thanks

---

### Post by carl4926 on 2013-04-29
I always do it manually first but the installer will do it all for you. It should be obvious what choices to make, just read the instruction as the install proceeds

---

### Post by fantab on 2013-04-29
Enter your BIOS set up and navigate yourself to find what mode is your SATA set to: there will be usually three, IDE, RAID, AHCI. It should be set to **AHCI**.

Does your new MoBo has **UEFI** feature? it should. The reason I ask is Booting from UEFI takes a slightly different partitioning approach then from 'disabled' UEFI, which is BIOS. 
For UEFI you need **GPT partition table** and a separate efi partition. (This is the future).
Or you can disable UEFI boot from BIOS-setup and Boot the 'old way' which uses **msDOS partition table**. (Kindly look up the terms in **bold** on google or on this forum).

The following links should get you started:
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
[http://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/](http://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/)
[http://www.anchor.com.au/blog/2012/10/the-difference-between-booting-mbr-and-gpt-with-grub/](http://www.anchor.com.au/blog/2012/10/the-difference-between-booting-mbr-and-gpt-with-grub/)
[http://www.rodsbooks.com/gdisk/booting.html](http://www.rodsbooks.com/gdisk/booting.html)
[http://www.petri.co.il/gpt-vs-mbr-based-disks.htm](http://www.petri.co.il/gpt-vs-mbr-based-disks.htm)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Since we don't like to partition our disks again and again, we must plan ahead.. Decide for yourself.

---

### Post by rumbarel on 2013-04-30
OK, so my "new" motherboard is NOT UEFI.   So how should I partition the new 500 GB hard drive?

---

### Post by Slim Odds on 2013-04-30
> **rumbarel said:**
> OK, so my "new" motherboard is NOT UEFI.   So how should I partition the new 500 GB hard drive?
That really depends on how you plan to use the machine.
You should probably just let the installer do its thing (select automatic).

---

### Post by fantab on 2013-04-30
Either let the Ubuntu installer do it for you or do it manually with GParted from Ubuntu: Boot Ubuntu DVD/USB, choose to "Try Ubuntu" and when the desktop is ready open Gparted. First create a partition table (see under Device), then partitions. If you do it manually then during Ubuntu install choose opttion "Something Else" at the screen where it asks you, how you want to install ubuntu and  point the installer to appropriate partitions...

Partitioning layout is a very personal thing, its upto you how you want to lay it out.
As a suggestion:
20-25GB Primary ext4 "/" mountpoint
20-25GB Primary ext4 (do not assign mountpoint) *in case in future you want to dualboot another distro or another Ubuntu flavour*
2-4GB SWAP
RemainingGB Primary ext4 "/home" mountpoint  [OR] RemainingGB Primary ext4 (no mountpoint)

---

### Post by rumbarel on 2013-04-30
This machine will be used pretty much exclusively for web browsing and email only, or I'd say 95% of the time, by my 83 year old father.

---

### Post by carl4926 on 2013-04-30
> **rumbarel said:**
> This machine will be used pretty much exclusively for web browsing and email only, or I'd say 95% of the time, by my 83 year old father.

Personally I always make /home separate
Easier for when you install the New release as you then just leave /home unformatted.

I's probably do

4GB swap (or = to 2xRAM)
20GB ext4 and assign to /
all the remaining space to /home ext4

---

