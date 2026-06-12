---
title: "grub problems installing Ubuntu 10.04 64bit on an external USB drive"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by domel07 on 2010-07-15
The default (graphical) installer did not work on my PC (i7 quadcore 8 GB DDR3). I have installed Ubuntu using the alternative installer (Desktop, 64 bit) on my external USB drive. I installed grub on the MBR of the second drive (/dev/sdb) as I did not want to touch my (first) Windows disk. After reboot (chosing the USB drive as boot device, else Windows is booted) grub reports an error and enters the rescue mode. I tried all possible combinations of "root=(hdX,Y)" in grub.cfg to no avail.

I repeated the whole procedure but now disconnected the internal HD with Windows. Installation went smooth again (Windows disk was not seen this time), but after reboot (the internal drive connected or not) I again get (slightly different this time) grub error: can not find file.

What am I doing wrong? Thanks for any hints.

-- Dominik

---

### Post by C.S.Cameron on 2010-07-15
Have you checked the MD5SUM of your iso file?

---

### Post by domel07 on 2010-07-15
No, but I have used the on-cd verification tool before the installation.

> **C.S.Cameron said:**
> Have you checked the MD5SUM of your iso file?

---

### Post by oldfred on 2010-07-15
Post the results.txt and we will see if something looks out of place. You have the newest processor and sometimes that also can be a problem. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by domel07 on 2010-07-15
From the script description, I need to first boot into the system, which I can not. I get a failure BEFORE booting.


> **oldfred said:**
> Post the results.txt and we will see if something looks out of place. You have the newest processor and sometimes that also can be a problem. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by C.S.Cameron on 2010-07-15
The on CD option is not as reliable as MD5, I have had false negatives.

---

### Post by efflandt on 2010-07-15
You have not stated the original grub rescue error, but let me guess: **error: unknown filesystem**

I got that error on a brand new Dell Studio XPS 8100 w/i5 650 3.2 GHz, 8 GB DDR3 when attempting to boot 64-bit Lucid on ext3 somewhere beyond the 453 GB point of a 500 GB USB drive (WD Passport).  But the strange thing is, 2 laptops from 2006 have no issues booting that system on that 500 GB USB.  And my new PC boots 64-bit fine from a 160 GB WD Passport.

Even stranger is that once I installed 64-bit Lucid to my internal drive, it had no problems booting 962 GB out on a 1 TB drive.  The only difference in that case is that I left that standard Win7 mbr untouched, and put grub on sda4 instead.

My thread [http://ubuntuforums.org/showthread.php?t=1526407](http://ubuntuforums.org/showthread.php?t=1526407) provides more details, but so far does not reveal any answers.

---

### Post by oldfred on 2010-07-15
You can run the boot_info_script from the Ubuntu liveCD or most of the rescue CDs based on linux.

---

### Post by domel07 on 2010-07-16
No, it's not unknown filesystem, it's something like file not found.
I also tried ext3 instead of thedefault ext4 - problem still there.

Then I installed from debian testing netinst - IT BOOTS FINE, gets stuck much later on X (another story)

So something is clearly wrong in the Ubuntu installer. I will check the ISO's MD5 sum as advised and will come back should this be a problem.

> **efflandt said:**
> You have not stated the original grub rescue error, but let me guess: **error: unknown filesystem**

I got that error on a brand new Dell Studio XPS 8100 w/i5 650 3.2 GHz, 8 GB DDR3 when attempting to boot 64-bit Lucid on ext3 somewhere beyond the 453 GB point of a 500 GB USB drive (WD Passport).  But the strange thing is, 2 laptops from 2006 have no issues booting that system on that 500 GB USB.  And my new PC boots 64-bit fine from a 160 GB WD Passport.

Even stranger is that once I installed 64-bit Lucid to my internal drive, it had no problems booting 962 GB out on a 1 TB drive.  The only difference in that case is that I left that standard Win7 mbr untouched, and put grub on sda4 instead.

My thread [http://ubuntuforums.org/showthread.php?t=1526407](http://ubuntuforums.org/showthread.php?t=1526407) provides more details, but so far does not reveal any answers.

---

### Post by domel07 on 2010-07-16
The exact error message:

error: file not found
grub rescue>

---

### Post by efflandt on 2010-07-16
I did get the **error: file not found**  grub rescue on an older desktop PC that did not like the new partition alignment of 10.04.  The old PC would not even boot the 160 GB USB drive until I repartitioned it from 9.10 and used partman/alignment=cylinder kernel boot parameter while installing (also added to /etc/default/grub).  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)

In that case grub rescue could successfully **ls (hd0,2)/**, but **ls (hd0,2)/boot** displayed ascii happy face symbol, and **ls (hd0,2)/boot/grub** said **file not found**.  From grub rescue can you **ls** any partition on any drive?  Note that when you boot from USB, the boot drive will probably be (hd0) regardless of what sd it is after a system comes up.

But the alignment boot parameter not help for 500 GB USB on the old or new PC (which boots fine on 2 laptops), so there must be some other issue at play for some computers or BIOS version or settings.

---

