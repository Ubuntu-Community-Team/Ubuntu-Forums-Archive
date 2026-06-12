---
title: "Grub 1.5 - error 22 impossible to avoid"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by javipas on 2006-08-27
Hi all,

I'm a longtime linux user, but I can't solve this. I've got three SATA hard drives with serveral partitions on all of them. 

The first one (/dev/sda) contains, amog others, the Windows XP partition

The second one (/dev/sdb) contains several data partitions

The third one contains the linux partitions: (/dev/sdc5 -> openSUSE 10.1, /dev/sdc6 -> Ubuntu Dapper 6.06).

Dapper was the last one installed, so grub was installed from there. Everything ran fine, but suddenly when I rebooted grub was always showing the "error 22". It can't find the partitions, though they are still there. 

I tried to boot from the Ubuntu Live ISO, opened a terminal, mount my Ubuntu root partition and make a "grub-install /dev/sda" to reinstall grub, and although I got no error messages (the device map was right, as always) but when I rebooted the error appeared again.

What I did yestertady was to resize one partition on /dev/sda, install another Ubuntu Dapper onto /dev/sda7 and see if that work. It did, the MBR changed, and grub installed succesfully again, including all the OS's. 

But again, I couldn't boot my "old" linux partitions, I could only boot Windows and the last Ubuntu on /dev/sda7. If I try to boot Ubuntu on /dev/sdc6) or openSUSE on (/dev/sdc5) it tries, but it says it can't find the partitions (hd2,5) and (hd2,4)respectively, though all is correct on my menu.lst file. 

So it seems the MBR that grub has is corrupt by some reason. I can boot on my openSUSE inserting the DVD and choosing the "boot an installed OS" option that appears when the instalation begin, but this not the desirable way to work...

---

### Post by cleentrax on 2006-08-27
> **javipas said:**
> Hi all,

I'm a longtime linux user, but I can't solve this. I've got three SATA hard drives with serveral partitions on all of them. 

The first one (/dev/sda) contains, amog others, the Windows XP partition

The second one (/dev/sdb) contains several data partitions

The third one contains the linux partitions: (/dev/sdc5 -> openSUSE 10.1, /dev/sdc6 -> Ubuntu Dapper 6.06).

Dapper was the last one installed, so grub was installed from there. Everything ran fine, but suddenly when I rebooted grub was always showing the "error 22". It can't find the partitions, though they are still there. 

I tried to boot from the Ubuntu Live ISO, opened a terminal, mount my Ubuntu root partition and make a "grub-install /dev/sda" to reinstall grub, and although I got no error messages (the device map was right, as always) but when I rebooted the error appeared again.

What I did yestertady was to resize one partition on /dev/sda, install another Ubuntu Dapper onto /dev/sda7 and see if that work. It did, the MBR changed, and grub installed succesfully again, including all the OS's. 

But again, I couldn't boot my "old" linux partitions, I could only boot Windows and the last Ubuntu on /dev/sda7. If I try to boot Ubuntu on /dev/sdc6) or openSUSE on (/dev/sdc5) it tries, but it says it can't find the partitions (hd2,5) and (hd2,4)respectively, though all is correct on my menu.lst file. 

So it seems the MBR that grub has is corrupt by some reason. I can boot on my openSUSE inserting the DVD and choosing the "boot an installed OS" option that appears when the instalation begin, but this not the desirable way to work...

I've been getting that error a lot lately, and some others, while I try to set up a RAID-5 home server. It seems that grub or dapper don't like dealing with drives unless they are ATA and hooked up to the motherboard. I have two PCI IDE cards, both of which supposedly work with Linux, but if I add them to my system, then GRUB  won't work. I hear the same thing happens sometimes with SATA drives, but I haven't used them. Do you have an IDE drive you can use as your boot drive?

---

### Post by javipas on 2006-08-28
> I've been getting that error a lot lately, and some others, while I try to set up a RAID-5 home server. It seems that grub or dapper don't like dealing with drives unless they are ATA and hooked up to the motherboard. I have two PCI IDE cards, both of which supposedly work with Linux, but if I add them to my system, then GRUB won't work. I hear the same thing happens sometimes with SATA drives, but I haven't used them. Do you have an IDE drive you can use as your boot drive?

In fact, I'm starting to think that all my problems could be a SATA issue. All my HDDs are SATA, and I noticed when I tried to reinstall openSUSE in the third trive (the one that failed, Ubuntu didn't work) the wizard showed a warning about missing support for RAID systems. 

The odd thing is, I don't have RAID installed. I've disabled that option on my nForce4 motherboard BIOS. 


So now I'm running from Ubuntu on /dev/sda6, but none of my Linux systems on /dev/sdc (the ones I mentioned before) are accessible from GRUB. All of them give me a Error 22.

---

