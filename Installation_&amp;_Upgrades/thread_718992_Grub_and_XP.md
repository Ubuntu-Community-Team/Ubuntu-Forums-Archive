---
title: "Grub and XP"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by flavourful on 2008-03-08
I just got a new laptop with Vista pre-loaded (yuck), and the first thing I installed XP in a second partition. That went over fine, but I was only able to boot XP.  I 'repaired' Vista's boot file using the repair console on the Vista install cd, so at that point I could only get into Vista.  I achieved a dual boot using EasyBCD within Vista so I could do either one, though I intended to delete Vista as soon as I got XP running stable and made sure all the drivers worked.

long story short, I got XP to run stable and deleted my Vista partition to install Ubuntu. Now I can't get into XP because it relied on the EasyBCD within Vista to load, both of which are now gone.

I put an entry into grub's menu.lst to fix it, but when I loaded windows it gave me a "BOOTMGR is missing". I can pretty much guarantee that the menu.lst entry is correct, and pointing to the right partition.   
The problem seems to be within windows, not grub. I could probably completely rebuild XP's boot files using the original cd and it's repair console, but I believe that would overwrite the boot sector and allow me to only get into windows again. 
 
Any suggestions? 
The only thing I could think of is to rebuild and boot to XP, then get back into Ubuntu using the CD; but from there I don't know how to get the Grub boot manager to take precedence again. help!

---

### Post by Pumalite on 2008-03-08
Start from scratch. Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete everything in your drive. Make 1 partition for XP at the beginning of the drive formatted ntfs. The rest of the drive a partition formatted ext3. Install XP first in sda1 (1st partition). Install Ubuntu last and let Grub install to MBR (by default). You'll have dual boot.

---

### Post by excogitation on 2008-04-30
Sorry, Pumalite, but I don't agree at all.

I second
> **flavourful said:**
> 
... rebuild and boot to XP, then get back into Ubuntu using the CD
and install grub again - if there's no better solution.

---

