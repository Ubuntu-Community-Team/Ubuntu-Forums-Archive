---
title: "Help with install?"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Xandoris on 2010-07-04
I have tried different versions of Ubuntu before via a live CD/USB and now I want to make a permanent install of ubuntu 10. However I can't seem to get the partitions done correctly as I don't want to do wubi install. I can't create enough partitions off the Ubuntu live CD im running on a different computer (the one im going to install it on) because Gparted is telling me I can't exceed 4 primary partitions.

I'm currently running Windows 7 Professional 64 bit, any help people?
Also I was looking at [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) but when i get to the partition selection I'm not sure if a swap partition is put into it.

---

### Post by howefield on 2010-07-04
> **Xandoris said:**
> because Gparted is telling me I can't exceed 4 primary partitions.

This is correct, you need to create logical partitions within an extended partition. Your extended partition would count as one of your primary drives.

---

### Post by Xandoris on 2010-07-04
> **howefield said:**
> This is correct, you need to create logical partitions within an extended partition. Your extended partition would count as one of your primary drives.
But what about the swap partition would it go into that extended partition or not?
(As one might gather I don't mess with partitions a lot.)

---

### Post by howefield on 2010-07-04
> **Xandoris said:**
> But what about the swap partition would it go into that extended partition or not?

Yes, all your Ubuntu partitions could be contained within the extended partition. I'd recommend 3 partitions one for /, one for /home and one for swap.

---

### Post by Xandoris on 2010-07-04
Will i need to add any flags to the partitions under the extended one?

---

### Post by howefield on 2010-07-04
> **Xandoris said:**
> Will i need to add any flags to the partitions under the extended one?

No.

Presumably you have defragmented windows and shrunk the size of the windows partition to whatever you need it to be, using your windows applications.

Then load up up the Ubuntu Live CD and use GParted to created an extended partition in the now empty space, then split that up into however many logical partition you want/need, formatted however you want, eg ext4.

Then during the installer, just mount the relevant partitions when you get to the disk partitioning stage.

The installer will take care of the rest.

---

### Post by Xandoris on 2010-07-04
I don't think Windows will let me shrink the in use partition. I tried to shrink it yesterday and it locked up the Computer Management panel for the Virtual Disk Service.

---

### Post by howefield on 2010-07-04
> **Xandoris said:**
> I don't think Windows will let me shrink the in use partition. I tried to shrink it yesterday and it locked up the Computer Management panel for the Virtual Disk Service.

I thought Windows Disk Management let you resize in Windows 7, but I haven't used it since the Beta and RC, my recollection may well be flaky, the point being that tools designed to work on "windows" file system would probably be a better bet for manipulating windows file systems than tools designed to work on "linux" file systems, and vice versa. 

> How large should I make the different partitions while having 138.39GB set aside for the Ubuntu install?

Your choice really, I'd probably go for something like 20 gig for /, twice your RAM for /swap (although if you have lots maybe 1 x the RAM) and the rest for /home.

---

### Post by ajgreeny on 2010-07-04
With win7 you must use its own disk management to shrink the OS partition, and not be tempted to use gparted on the ubuntu live CD or you will suffer badly, I'm afraid, and probably not be able to boot windows at all.

Run the Ubuntu live CD and from that either show us a screenshot of gparted, with the win7 disk partitions showing, or more simply use the terminal and run ```
sudo fdisk -l
```(that's a lower case L at the end, not 1) then post the output back here.  That will give more chance to know better what we are dealing with.

Regarding sizes of partitions, with almost 140GB available, I suggest 8 - 10GB for root (/), up to 4GB for swap, particularly if you want to hibernate ubuntu, but possibly less if hibernation is not something you want to do, and the rest for /home.

---

### Post by Xandoris on 2010-07-04
Well I have to run chkdsk in windows a few times on boot, but I seem to have it working even though I did the partitions in Ubuntu. I'm going to check how well win 7 is going to be working. (Hope to god it will). If worst comes to worst, I can always reinstall win 7 with the OS install CD i got for it. Or use the system recovery disk I also made before starting this task.

---

### Post by Xandoris on 2010-07-04
And now it seems to be working just fine. I have to select Win 7 in the grub menu during boot about two times but i can live with that. Thanks for the help.

---

