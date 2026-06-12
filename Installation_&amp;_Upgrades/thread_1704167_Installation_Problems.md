---
title: "Installation Problems"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by Aruman on 2011-03-10
Hi I'm Aruman and I'm new to Ubuntu Forum

My Problem is that I have a new Sony Vaio Z series with the 128GB SSD HD(dual 64GB Hd) And I want to install Windows 7  Ultimate 64-Bits and Ubuntu 10.10 32-Bits and using a partition to share files between them (Fat32) but when trying different times and different ways of partition the drives I got diff errors like first i got Grub loading error 17, then Error 21 and now Error 22, what I'm doing wrong? maybe the dual 64 GB is giving me some problems for the partitions? what's the best way to do this?

I want 40GB for Win7, 20 GB for Ubuntu 10.10 around 8GB for linux-swap and the rest for Shared Files(Fat32) between the two Os.


I've done this before with WinXp and Ubuntu on one single physical HD but never with the new SSD HD (dual physical drive ) maybe theres the problem? don't know much about the Solit State Drives.

Also I've tried installing Ubuntu 10.10 64-Bits but I can't see anything  the Graphics is way off is there a problem with the 64-Bits Version?  that's why now I choose the 32-Bits.


Anyways thanks a lot,

Aruman.

---

### Post by An Sanct on 2011-03-10
Welcome to the forums!

First: SSD is "just" another hard drive, the way information is stored and the read speed make no difference to OS (Windows/Linux) it is treated just like a normal hard drive.

Second: why 8GB swap? Do you really need 8Gb of swap?

Third: If you want to share data between OSes, Linux has no problem with reading NTFS, so it would be best to make the shared partition NTFS.

About the grub errors, I don't know them. I would install windows7 first and then install Ubuntu alongside windows, that way you get both OS without problems.

I use 64bit Ubuntu, never had a problem (I didn't cause myself).

---

### Post by coffeecat on 2011-03-10
Welcome to the forum.

First...

> **Aruman said:**
> Also I've tried installing Ubuntu 10.10 64-Bits but I can't see anything   the Graphics is way off is there a problem with the 64-Bits Version?   that's why now I choose the 32-Bits.

It's unusual for graphics to be OK in the 32-bit version and not in the 64-bit version. This is unlikely to be related to running 64-bit. What graphics chipset do you have?

> **Aruman said:**
> I got diff errors like first i got Grub loading error 17, then Error 21 and now Error 22,

This is perplexing. Those grub errors are from legacy grub which Ubuntu has not used since the now obsolete Jaunty/9.04 release, yet you say you installed version 10.10. Ubuntu has been using grub 2 since the 9.10 release and you do not get numerical grub errors with grub 2. Have you ever installed an earlier version of Ubuntu to that machine or any other non-Ubuntu Linux distro?

So that we can diagnose what the problem is, boot up with the live Ubuntu CD, choose "try Ubuntu" so that you get to the live desktop, make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to those instructions and post the contents of the RESULTS.txt file. When you post that file, please remember to enclose it between [noparse]```
 and 
```[/noparse] tags for legibility. You can use the # icon in the message toolbar for this.

---

### Post by Aruman on 2011-03-10
Ok thanks Guys,

First I Partition the First  SSD drive in 40GB for W7 and and 20GB Ext3 for Ubuntu and the second SSD I partition it 8GB LinuxSwap and the rest Fat32,

Then I Part. the Fisrt SSD 40GB W7 and 20GB Unallocated and on the Second SSD, I part. it 20GB Ext3 for Ubuntu, 8GB LinuxSwap and the rest FAT 32. I also try installing Backtrack 4 that's why the other errors.

In these two methods I get those errors 17, 21 ,22.

I used System Rescue Gparted for the partitions.

So it's best to install Win 7 and Ubuntu (or Backtrack 4) on the fisrt SSD and the second SSD do the Linux Swap and format the rest Ntfs in place of FAT32?

Thanks,

Aruman.

---

