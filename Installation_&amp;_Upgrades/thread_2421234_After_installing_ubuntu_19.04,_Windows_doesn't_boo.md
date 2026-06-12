---
title: "After installing ubuntu 19.04, Windows doesn't boot anymore"
date: 2019-06-18
forum: Installation &amp; Upgrades
---

### Post by quantumsavi on 2019-06-18
Hi, I've recently installed ubuntu 19.04 in dual boot with windows 10 (both in UEFI). GRUB recognizes windows, but when I choose the option "Windows Boot Manager" the windows logo and the loading animation appear only for a few seconds, then the computer reboots, bringing me back to grub selection menu. I tried many things, including ```
sudo update-grub
``` and using boot-repair, but none of them worked. Here is the log for boot-repair, if that helps: [https://paste.ubuntu.com/p/35q4kqtqZG/](https://paste.ubuntu.com/p/35q4kqtqZG/) (I also have a 2tb hard drive as a secondary drive for data, but I use only one 240gb ssd for the operating systems).

edit: The windows partition is still accessible through the file manager in Ubuntu. I've also disabled secure boot.

---

### Post by ubfan1 on 2019-06-18
When grub starts the Windows bootloader, its job is done.  If all the Windows files are still in place, then maybe the Windows partition is too small.  In any case, this does not seem to be an Ubuntu problem.

---

### Post by yancek on 2019-06-18
There is no indication that your EFI partition (sda2) is marked active/bootable.  Might not be a problem but I would use GParted from the Ubuntu install media to check that its is marked active/bootable. Your windows entry in grub.cfg is correct so that is not the problem.  If you look at the boot repair output you will see the following a number of times for different partitions.

> The device '/dev/sda3' doesn't seem to have a valid NTFS.


Also several of your windows partitions show 'unknown filesystem' which I would guess you need to run chkfdsk from your windows install DVD or some other windows utility you can download.  Can't do this from Linux usually although you could try running 'ntfsfix' from Ubuntu.  You may need to install it first.  Unless it is an extremely minor problem, it probably won't help but won't hurt to try.

---

### Post by oldfred on 2019-06-18
You are showing LDM, how did you add that?
With BIOS/MBR systems it was called dynamic disks and seen as SFS.
It is somewhat like Linux's LVM - logical volumes
They were originally used as a work around for the MBR 4 primary partition limit as opposed to the more common extended partition and logical partitions. 
But with gpt you can have up to 128 partitions, and can even add more with partition table changes. So no need for dynamic partitions.

It used to be that Ubuntu/Linux did not work at all with dynamic partitions. But some driver was updated and it can read some data.

Do you really want or need LDM?
Some third party Windows partition tools would convert dynamic to basic partitions with MBR, not sure if they also work with gpt or not.
       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

