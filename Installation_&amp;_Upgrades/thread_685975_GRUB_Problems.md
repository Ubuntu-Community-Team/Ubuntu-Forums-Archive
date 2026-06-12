---
title: "GRUB Problems"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by ErusGuleilmus on 2008-02-02
I have 3 partitions on my hardrive, one for Windows Vista, one for Ubuntu 7.10, and then a third for openSUSE 10.3. They where installed in that order. 

When I installed openSUSE, it installed its own boot loader over GRUB, and I now cannot boot into Windows, SUSE's boot loader sees them, but I can not boot into them. Will reinstalling GRUB allow me to access all three again? 

Thanks!

---

### Post by logos34 on 2008-02-02
> **ErusGuleilmus said:**
> Will reinstalling GRUB allow me to access all three again? 

Maybe, maybe not.  Grub doesn't always work with Vista.  

Check the 'root' lines in grub..vista should be (hd0,0) if it's the first partition

If it still doesn't work, you might want to try using [EasyBCD]("http://neosmart.net/wiki/display/EBCD/linux") to modify Vista bootloader to boot linux

---

### Post by ErusGuleilmus on 2008-02-03
I installed Ubuntu 7.10 over openSUSE, and this also reinstalled GRUB. I cannot, however, yet boot into Windows. When I attempt to, I get a screen saying that some .exe is missing, and that I should put in the install DVD. I do this, and click repair, but the Windows DVD can not find a Windows partition to repair. I also can not mount that partition in Ubuntu. ls my Windows partition gone for good, or is there something that I can do to fix it, or at least salvage some of the data in it?

Thanks!

---

### Post by froy02 on 2008-02-03
What is the output for code 'sudo fdisk -l' ?  Does it show a partition of the type 'HPFS/NTFS'?  If it does then your partitions are intact, Only your MBR is messed up.  If that's the case here's a thread on how to install GRUB with live CD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ErusGuleilmus on 2008-02-03
Here is the out put of sudo fdisk -l : ```


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c1324

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7594    60994560    7  HPFS/NTFS
/dev/sda2            8456        8515      481950   82  Linux swap / Solaris
/dev/sda3            8516        9729     9751455   83  Linux
/dev/sda4            7595        8455     6915982+  83  Linux

Partition table entries are not in disk order
william@william-laptop:~$ 

```

Grub being installed doesn't seem to be the problem. GRUB was reinstalled when I installed Ubuntu over openSUSE. GRUB sees the Windows partition. I get an error message when I boot into it, however.

---

### Post by froy02 on 2008-02-05
It looks like all your partitions are intact though they are not in order.
The first thing you have to do is fix the MBR so that Vista can boot regularly.
Here's the website that would tell you how to do that in Vista:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

After Vista is recovered go to the other thread in Ubuntu forum to re-install grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

A little background on grub.
It must be installed on the first boot hard drive set by the Bios. 
It is then re-directed to the a partition which could be on the same drive or a different one but nonetheless a primary bootable partition.
It needs to find a menu.lst file in that partition and from there you make your selection which OS to run and it would re-directed again to the partition that you chose. 
It would then run the OS in that partition.
In your case (sd0,0)  (sd0,2)  (sd0,3) or  they could be designated (hd0,0)   (hd0,2)   (hd0,3).
(sd0,1) is your swap partition.
Grub starts count from 0. 
When using /dev/sda1x, the count starts with 1 so /dev/sda1=(sd0,0) in grub.

---

### Post by logos34 on 2008-02-05
> **froy02 said:**
> In your case (sd0,0)  (sd0,2)  (sd0,3) or  they could be designated (hd0,0)   (hd0,2)   (hd0,3).
(sd0,1) is your swap partition.
Grub starts count from 0. 
When using /dev/sda1x, the count starts with 1 so /dev/sda1=(sd0,0) in grub.


Grub does not use 'sd_'.  GRUB makes no distinction between sda and hda drives

Please read this:
['A Quick Guide to GRUB's Numbering System' ]("http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System")

---

### Post by froy02 on 2008-02-07
> Grub does not use 'sd_'. GRUB makes no distinction between sda and hda drives

Please read this:
'A Quick Guide to GRUB's Numbering System'

Thanks, that's a great tutorial about grub, very useful for me since I have been trying these linux OS.  I am moving away from window$ and now I can because I have been testing Ubuntu for 4 months now and it looks very good.  I am able to try several OS's because all my computers' hard drives are removable so I can just remove and plug in another one.  If I mess up, I just re-install.
Thanks again.

---

