---
title: "Dual boot and Acronis restore"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by ineuw on 2008-09-11
I have a Grub dual boot XP\Ubuntu 8.04 installation and my XP crashed due to a major registry corruption.

I have the XP\Acronis image stored on the 2nd non system disk\drive, but because it's dual boot, the Acronis boot CD, which I use to boot doesn't see my physical disks!

I can still dual boot, and when in Windows I can navigate. but cannot connect to the Internet. I also lost the use of most of the Administration tools, and the Application references in the registry and are corrupted and because of this the Menu shortcuts don't work.  After several attempts, I managed to activate the system recovery but it didn't help.

Currently, I booted into Ubuntu on the same machine.  Here I have internet access, (so I know that this is not a hardware problem).  I can also access all the data on the NTFS drives from Ubuntu.

Here are the disks\drives configurations:

Disk 0 = Windows\Drive C: system boot drive NTSF <- applications, no data
         Windows\Drive D: non system NTSF   <- data

Disk 1 = Windows\Drive E: non system NTSF   <- data
         Windows\Drive S: non system NTSF   <- stored Acronis image 
         Linux\Ubuntu 8.04

Does anyone have any idea how I can reinstall my Acronis image to get my Windows up and running again?  I am sure that the problem is because of the registry corruption.

Many thanks in advance.

---

### Post by diver858 on 2008-09-15
Did you try this? Instructions are not quite right, but the basic approach is straightforward, great idea, and very effective option.

[http://ubuntuforums.org/showthread.php?t=449167&highlight=Adding+Acronis+Grub+list](http://ubuntuforums.org/showthread.php?t=449167&highlight=Adding+Acronis+Grub+list)

---

### Post by ineuw on 2008-09-15
The only solution that worked quickly, was to reformat drive C: which eliminated the dual boot.  Then, Acronis recognized the disk drives and I restored the mirror copy (Windows XP).  I lost Ubuntu but this is not serious as I was just getting familiar with it and there was nothing crucial lost.

I decided not to play with dual boot again and I am buying an additional disk drive dedicated to Ubuntu.

My Acronis is a Windows installation and I know that there may have been other solutions but time is valuable to me.  To reformat and restore Windows took me a little over an hour.  The OS and software data was about 9GB uncompressed.

Thanks again

---

### Post by diver858 on 2008-09-16
It is not necessary to reformat the drive to remove grub / dual boot - use the repair option from your XP install disk and run fixmbr - quick and painless.

---

### Post by ineuw on 2008-09-16
> **diver858 said:**
> It is not necessary to reformat the drive to remove grub / dual boot - use the repair option from your XP install disk and run fixmbr - quick and painless.

You're absolutely right. I realized this after restoring, as I still had to repair the boot sector with fixmbr because the restored copy contained the dual boot with nowhere to go.  This happens when one rarely (and unexpectedly) crashes and without prior experience with dual boot systems.

---

