---
title: "Format partition if it's boot?"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by thunderbirdje on 2008-11-06
Hi

I'm ready to get rid of my Vista partition! Wiha :D But... Is it that easy?

My situation:

Laptop came with Vista -> Transformed in dual boot VISTA + UBUNTU.

**I am wondering if I just can format the NTFS partition (sda1 - see below for fdisk info-) without damaging 'the booting of my laptop'? Maybe GRUB is on sda1? If I format it... will my laptop still (spontaneous) boot?**

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x23fca1d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   258973549   129486743+   7  HPFS/NTFS
/dev/sda2       299933550   310211264     5138857+  83  Linux
/dev/sda3       310215150   312576704     1180777+  82  Linux swap / Solaris
/dev/sda4       258983865   299933549    20474842+  83  Linux

Partition table entries are not in disk order
```

Thanks in advance :-)

---

### Post by caljohnsmith on 2008-11-06
Yes, make sure you format the sda1 partition and not delete it, because if you delete it, your partition numbering might change and make your computer unbootable until you reinstall Grub. :)

---

### Post by thunderbirdje on 2008-11-07
Thanks! It worked! :D Wauw great!

I'm just curious... how can you see when GRUB is on the partition or in the MBR?

---

### Post by dabl on 2008-11-07
Here's everything you ever want to know about Grub, and then some:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

:)

---

### Post by caljohnsmith on 2008-11-07
> **thunderbirdje said:**
> Thanks! It worked! :D Wauw great!

I'm just curious... how can you see when GRUB is on the partition or in the MBR?
I'm glad everything went OK. :) And about Grub being on a partition or in the MBR, actually Grub is in both places; if you boot your drive on start up and get a Grub menu, that means you have Grub installed to the MBR of that drive, but in order to work, Grub also has boot files that it needs in some other partition (in your case, the Ubuntu partition), specifically the Grub "stage2" file and the menu.lst. If you want to know whether a particular drive has a Grub MBR or a Windows MBR, you can do:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
And replace sda with the drive in question. If that command returns "GRUB", you have Grub in the MBR, but if it returns "Missing operating system", you have a Windows MBR. 

That link that dabl gave is a great place to start if you want to learn more about Grub. Anyway, cheers and have fun. :)

---

