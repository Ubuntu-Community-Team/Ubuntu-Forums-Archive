---
title: "Multidrive multiboot"
date: 2015-08-11
forum: Installation &amp; Upgrades
---

### Post by Leprechaun7 on 2015-08-11
Hi, if this is a redundant question please post the link. I found this hard to search.

I have linux and windows installed on an SSD. I want to add another SSD and install linux maybe windows on that as well. I want to be able too chose any of the four oses in the grub menu. How do I go about installing fresh oses on the new SSD so that it won't conflict with the current SSD and they can all boot happily ever after?

Thanks for the help

---

### Post by TheFu on 2015-08-11
I have no idea how to dual boot Windows, there is usually a catch with MSFT stuff. But for almost all Linuxen - grub will discover each of the installations an make a menu entry automatically on the boot disk, regardless of the disk where the OS is actually loaded.  Make sense?

---

### Post by yancek on 2015-08-11
Which windows do you have currently installed and which windows do you plan to install?  If you are using windows 8 or newer and UEFI, the method is going to be different.  You would simply install the new system to the new drive so you would need to know how the drives are labelled.  In a Linux system, the first drive would be seen as sda, the second as sdb and so on.  In windows the labelling is different.  You could disconnect the current drive and install to the new SSD and after finishing run update-grub.  If you are using UEFI, it adds a complicating factor to booting.

---

### Post by oldfred on 2015-08-11
If Windows is BIOS based, it is important that BIOS is set to boot from drive you are installing Windows into. If you install to sdb, but BIOS boots from sda, it will install its boot into sda.
Windows also only install boot files into the one NTFS formatted partition with the boot flag.
Windows is only directly bootable from primary partitions, so if installing on same drive better to have install in a primary partition.

I might have one drive as Windows and one drive as Linux. And unplug other drive when installing.
Discusses Vista, but still the same for all BIOS/MBR based Windows systems.
       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

