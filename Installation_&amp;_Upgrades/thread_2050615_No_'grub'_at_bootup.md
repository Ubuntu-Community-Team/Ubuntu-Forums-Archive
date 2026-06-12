---
title: "No 'grub' at bootup"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by dlw on 2012-08-31
Fresh install along side W7
Install went well.
However, no 'grub' at bootup.
What happens during boot is;
HP screen appears, then
A text screen appears asking if I want to boot into W7 or W7 recovered. I had a problem a few months ago and had to do a recovery. 
The boot process never sees 'grub'.
Any ideas on how to solve this?

dlw

---

### Post by 3v3rgr33n on 2012-08-31
Hi

I've had this problem a couple of times. Your best bet would to load a LiveCD


Have a look at this [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by mörgæs on 2012-08-31
Be aware that most of the thread mentioned is obsolete. 

The part at the end concerning Boot Repair is still valid.

---

### Post by drmrgd on 2012-08-31
As mörgæs says, Boot Repair is what you want:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Depending on how your system is set up, it should be a simple matter of having the Grub bootloader be flagged on the /boot partition and set to chain load Windows.  If you like, you can post the results of the Bootinfo Script here so that we can assess your setup.  For most setups, though, the Boot Repair will handle the job quite nicely.  Just in case, you might also consider to have your Windows 7 install disc handy in case you hose the Windows bootloader and can't boot any OS.

---

### Post by dlw on 2012-08-31
Do not have W7 install CD. Have hidden partition.
Result of 'Bootinfo' is [http://paste/ubuntu.com/1177774](http://paste/ubuntu.com/1177774)

---

### Post by darkod on 2012-08-31
You never mentioned you have three disks. Go into BIOS and set the second disk, /dev/sdb, to be the first boot options. That's the 1TB disk.

The grub2 bootloader is there as you can see at the top of the results.

---

### Post by dlw on 2012-08-31
The BIOS does have that option.
Only has CD, USB or HD.
No sd1 or sd2

Any Ideas on what to do?

---

### Post by drmrgd on 2012-08-31
> **dlw said:**
> The BIOS does have that option.
Only has CD, USB or HD.
No sd1 or sd2

Any Ideas on what to do?

It won't be listed as sdb in BIOS as that's the way that Linux names the drives (just as Windows names them C: or D: or whatever).  Just look for the 1 TB hard drive on your system and use that as the primary boot device in BIOS.  It'll probably be labeled something like "ATA Hitachi HDS72101" in BIOS based on the Bootinfo script you posted.

---

### Post by darkod on 2012-08-31
There are two different settings that should exist in most newer BIOSes.

One setting is usually only for device types, like CD-ROM, HDD, USB, etc.
But in most cases there is another setting called HDD Priority or similar, that actually lists only the HDDs, and in which order they should be read for a bootloader.

Look more carefully in the BIOS, if you don't have this option you will have to move grub2 to /dev/sda.

---

### Post by dlw on 2012-08-31
OK! It's working.
Went ahead an ran 'boot-repair' and it fixed it.
Thanks for the help.

dlw

---

### Post by darkod on 2012-08-31
> **dlw said:**
> OK! It's working.
Went ahead an ran 'boot-repair' and it fixed it.
Thanks for the help.

dlw

It was working all the time, you were just booting the wrong disk. What boot-repair did was install grub2 to all disks, so it doesn't matter which one you boot from. :)

You could have done that manually too.

---

