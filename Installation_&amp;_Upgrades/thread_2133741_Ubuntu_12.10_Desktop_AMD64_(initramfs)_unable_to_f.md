---
title: "Ubuntu 12.10 Desktop AMD64 (initramfs) unable to find a medium"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by InfernalRage on 2013-04-09
Hello,

I am currently trying to install Ubuntu 12.10 Desktop AMD64 on a 50GB unallocated partition.  I downloaded "ubuntu-12.10-desktop-amd64.iso" and have tried mounting it on my 16GB USB flash drive using Pendrive Linux, Unetbootin, and LinuxLive USB Creator.  The md5sum is the same as the one listed on the Ubuntu release site.  I can boot using the UEFI or standard USB in the boot options.  After selecting either Run Ubuntu without installing or Install Ubuntu I get the same error stating "(initramfs) Unable to find a medium containing a live file system".  I have only briefly used Ubuntu in the past, so I am not that experienced with it.  Any help resolving this issue so I can install Ubuntu would be appreciated.  Please let me know if you need more information.

System Specs:
Windows 7 Professional 64-bit
AMD FX-6300
GIGABYTE Radeon HD 7870
8GB RAM (4GBx2)
GIGABYTE GA-990FXA-UD3 AM3+ AMD 990FX SATA 6Gb/s USB 3.0 ATX AMD Motherboard
Samsung 840 Pro Series 128GB SSD (Windows 7 installed on this drive)
WD Black WD1001FALS 1TB (contains all my data files i.e documents, music, videos, etc)
SAMSUNG Spinpoint F3 ST1000DM005/HD103SJ 1TB (50GB of this drive are unallocated to install Ubuntu on)

---

### Post by edentjeh on 2013-04-09
I've had this same issue when my USB disk was NTFS formatted, as soon as i changed that to FAT32 i was able to boot from my USB disk just fine.

---

### Post by InfernalRage on 2013-04-09
I had formatted it to FAT32 before I mounted it each time.

---

### Post by InfernalRage on 2013-04-10
I have also tried a different USB flash drive and I was getting the same error.

---

### Post by InfernalRage on 2013-04-12
I tried looking around the forums some more and I tried solutions that worked for other people, but none of them worked for me.  For example, I have my USB in a USB 2.0 slot and ensuring it is on AHCI instead of IDE.  I will continue to search the forums some more, but any help would be great.

---

### Post by InfernalRage on 2013-04-13
I still haven't found a solution yet.  Any thoughts?

---

### Post by InfernalRage on 2013-04-14
The SATA controller type is set to AHCI, the OS installation type set to "Other" on my bios, the md5sum matches the one listed on the Ubuntu hash list, and I am plugged into a USB 2.0 slot (I have tested it on every USB connection on my PC).  These seem to be the solutions that other people have used which have worked for them, however they are not working for me.  I can try to burn it to a DVD if the USB is an issue.

---

### Post by kevin.nyman on 2013-11-30
I know it's a bit late, but I found an answer here: [http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433) because I have the same motherboard and had to enable IOMMU mode in bios.

---

### Post by InfernalRage on 2013-11-30
Not at all and thank you for even replying.  I will definitely give that a shot soon.

---

### Post by amartinson on 2013-12-11
> **kevin.nyman said:**
> I know it's a bit late, but I found an answer here: [http://ubuntuforums.org/showthread.php?t=2143433](http://ubuntuforums.org/showthread.php?t=2143433) because I have the same motherboard and had to enable IOMMU mode in bios.

This worked for my gigabyte mobo! Amazing!

---

