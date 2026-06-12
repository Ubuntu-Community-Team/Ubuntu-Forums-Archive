---
title: "Ubuntu on a USB drive on a XP system"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by krobert999 on 2008-10-06
I decided to try Ubuntu 64 but rather than wipe out Windows 2 C if it works, I installed it on a USB hard drive. After installation, the system reported a boot error when trying to boot from the USB drive, so I tried to boot Windows from the hard disk only to get a grub loading error which means that the installation modified the wrong drives MBR. All the files were loaded onto the USB drive, but the MBR of the C drive was changed. To bring the system back to life, I had to run the DOS command FIXMBR so now the system works again but I really wanted to move on. Any advice? System info: 

Haier with 512 Mb RAM, Intel Core 2 processor
Windows XP (US English)
Ubuntu V7.04

Thanks!

---

