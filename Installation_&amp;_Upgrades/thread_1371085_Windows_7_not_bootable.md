---
title: "Windows 7 not bootable"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by presleyanne on 2010-01-03
Hi, I recently got a computer with Windows 7 on it and installed Karmic on it in a dual boot.  When I boot up, I get a choice between the first two partitions, which are the Windows recovery partition and the Windows system reserved partition, and Ubuntu, but not the actual Windows 7 partition.  I thought this might be because when I did the partitioning, I mounted the Windows 7 partition on Ubuntu.  So I unmounted it, but it still doesn't work.  I went into Disk Utility and the Windows 7 partition is shown as unrecognized and "unknown or unused", but it's set as NTFS and bootable.  Those are the things I would think would need to be set so I don't know where to go from here.

Incidentally, the only reason I care about booting into Windows now is that my internet connection has been horrible since I installed Ubuntu (this version; Hardy was fine on my old computer) and I'm wondering if it's the culprit, so if there's an issue with Karmic and wireless internet that I should know about, that would be great too!

Thank you!

---

### Post by hansdown on 2010-01-03
Hi presleyanne.

Karmic can be troublesome for some things, depending on your hardware.

Could you post your hardware, so someone can give some feedback?

---

### Post by presleyanne on 2010-01-03
Sure, my computer is a Sony Vaio VGN-NW270F.  Are there any other things that are relevant?

---

### Post by hansdown on 2010-01-03
If we can get a quick look at your partitions, someone can likely help.

Click applications> accessories> terminal.

Copy and paste 

```
sudo fdisk -l
```

In the terminal. If you could post a screenshot, we can see where the trouble may be.

---

### Post by presleyanne on 2010-01-03
This is what I got:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa2eb41af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1032     8287232   27  Unknown
/dev/sda2   *        1032        1045      102400    7  HPFS/NTFS
/dev/sda3   *        1046        7367    50781465    7  HPFS/NTFS
/dev/sda4            7368       38913   253393245    5  Extended
/dev/sda5            7368        7616     2000061   82  Linux swap / Solaris
/dev/sda6            7617       10412    22458838+  83  Linux
/dev/sda7           10413       14424    32226358+  83  Linux
/dev/sda8           14425       38913   196707861   83  Linux

```I'm kind of surprised because the partition that was showing as unknown in Disk Utility was sda3.

---

### Post by hansdown on 2010-01-03
Thanks presleyanne.

You seem to have a boot flag (*) on two partitions; /dev/sda2 , and /dev/sda3.

/dev/sda1 being unknown is a little unsettling.

/dev/sda2 is very tiny.

Before I start giving bad advice, maybe another member with more experience should have a look.

This is a nice notebook, and there have been wifi problems in 9.04 and 9.10.

I'm trying to find a how-to that will help.

---

### Post by Mark Phelps on 2010-01-03
> **presleyanne said:**
> Hi, I recently got a computer with Windows 7 on it and installed Karmic on it in a dual boot. 
Preinstalled Win7 boxes are typically configured with two partitions: a small one containing WinRE (for recovery), and a large one containing the rest of the OS.

So, how did you SHRINK the second partition to make room for Ubuntu?
>  When I boot up, I get a choice between the first two partitions, which are the Windows recovery partition and the Windows system reserved partition, and Ubuntu, but not the actual Windows 7 partition. 

The second partition IS the actual OS partition.  But you should choose the first one for booting the OS.

>  I thought this might be because when I did the partitioning, I mounted the Windows 7 partition on Ubuntu.  So I unmounted it, but it still doesn't work.  
What do you mean? Did you install from inside Win7 (using Wubi), or did you install to a separate partition?

I believe that ntfsprogs is installed by default in 9.10. so you should encounter no problems mounting the second Win7 partition.  I can think of no reason why you would want to mount the first Win7 partition.

> I went into Disk Utility and the Windows 7 partition is shown as unrecognized and "unknown or unused", but it's set as NTFS and bootable.  Those are the things I would think would need to be set so I don't know where to go from here.

As I said, there are two Win7 partitions.  They should both show up as NTFS. You should NOT have to mess with the boot flag at all, so, remove the boot flag from sda3.

---

### Post by presleyanne on 2010-01-03
I read that the Windows machine should have two partitions, but it looked like it came with 3 - recovery, system reserved, and C:.  I started up Ubuntu with a live CD and used gparted to shrink C:.  Then I started the installation process and made the rest of the partitions.  As I was doing that, I mounted C: as /windows.

---

### Post by presleyanne on 2010-01-03
I removed the boot flag from sda3, and restarted my computer.  The menu is the same - I can boot linux, Windows Vista (loader), or Windows 7 (loader), and both of the latter take me to a recovery process.

---

