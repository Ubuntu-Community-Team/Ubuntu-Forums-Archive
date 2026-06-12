---
title: "How to Resize Ubuntu Root Partition"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by kanaqsasak on 2010-10-05
Hi,
I installed linux on my system and made a dual boot system with Windows 7. But, I realize that my Windows system demands more hardisk space at this time (I planned to have just linux installation in my laptop after graduation, because some of my academic task still needs Windows platform). So I want to squeeze up my linux partition to be smaller. Currently my partition table is 

[IMG]http://img337.imageshack.us/img337/8918/hardiskpartition.png[/IMG]

How do I resize my linux root partition? I don't want to try erasing my linux partition, cos I will start everything over and I just don't have that enough time. And I know it will erase the boot loader, then I have to recover the MBR that is still looking so risky for me. Can someone please give some help?

---

### Post by Mark Phelps on 2010-10-05
From the Windows screen, can't tell which partition is your Linux root.  Would be better to boot into Ubuntu, open a terminal, and run "sudo fdisk -lu" (that's a lowercase L, not a one).

As to partition resizing, would recommend you do the following (once you determine your root partition):
1) Download and burn a GParted LiveCD (can get it from distrowatch.com)
2) Boot with the GParted LiveCD
3) Resize the appropriate Linux partition
4) If needed, move the other Linux partition to have the new unallocated space next to the Windows partition
5) When done, reboot, then boot into Ubuntu to be sure it still loads OK

Now, boot into Win7 and use the Disk Management utility to expand the size of the Win7 OS partition.  Do NOT do this using GParted.  Doing that runs the risk of corrupting the Win7 OS partition and rendering it unbootable.

---

### Post by timeoutmode on 2010-10-29
i have just been using ubuntu for about a week. isn't possible to resize the ubuntu partition in windows 7 disk partition? or i can only do this using gparted?

---

### Post by sikander3786 on 2010-10-29
> **timeoutmode said:**
> i have just been using ubuntu for about a week. isn't possible to resize the ubuntu partition in windows 7 disk partition? or i can only do this using gparted?
Only gparted. Windows 7's partitioner doesn't support ext3/ext4 filesystems.

---

### Post by timeoutmode on 2010-10-29
thank you.. i really am enjoying ubuntu.. i'm one of those who had no problem with my hardware.. everything works fine.. thanks..

---

