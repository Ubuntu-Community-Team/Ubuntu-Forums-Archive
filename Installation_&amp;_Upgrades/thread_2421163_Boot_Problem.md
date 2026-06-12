---
title: "Boot Problem"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by eddugo on 2019-06-17
Hi;
I an trying to set up an older pre uefi machine.  I upgraded it to Windows to 10 and now attempted to dual boot 19.04 as well.  It worked for a short time and now will not boot into Ubuntu.  Attempt to read or write outside of disk.  Hit any key error message.  Ran boot repair and it didn't help. [http://paste.ubuntu.com/p/CZpTPnz8P6/](http://paste.ubuntu.com/p/CZpTPnz8P6/)

Thank you

Ed

---

### Post by oldfred on 2019-06-17
One thing Boot-Repair does with multiple drive MBR systems is install grub to MBR of every drive.
Better to only use Advanced mode and only install grub to MBR of Ubuntu drive and keep (or re-install) a Windows boot loader to Windows drive.

Even more important with Windows 10 as grub only boots working Windows. And Windows 10 will turn back on the fast start up setting with major updates and when it sets hibernation flag grub will not boot it. But if you have Windows boot loader in MBR, you can in BIOS change & directly boot it. 
If you only have grub, you have to use your Windows repair/recovery flash driver or installer with repair console to get into Windows.

I might try booting with your multiple card reader unplugged as a test. My systems change drive order with flash drives plugged in. Ubuntu uses UUID to boot, so it still should boot, but my old system would stop searching for drives when I had multiple flash drives and get confused sometimes. Many systems on reboot promote flash drives to first in drive order for BIOS & grub, but HDDs may still first once booted. 

Boot-Repair says it installed grub ok. Do you have sdb set as default drive? If not change it.
And install a Windows Boot loader into sda and confirm Windows boots ok from sda's MBR. Grub will boot it from sdb, if fast start up is off.

You should note if you use e for edit you will see this:
set root='hd1,msdos5'
and multiple other places where it says drive is hd1. But with flash drives it may be any hdx.
I often directly boot ISO using device and if flash drive(s) plugged in have to edit hdx and sometimes just have to experiment.
Note it is also in linux line and all need to be changed, if experimenting.
When you boot directly from sdb, it should still be hd0.

---

### Post by eddugo on 2019-06-17
Hi;
Windows 10 works fine.  It's after I select Ubuntu that I get the error message.  Also, there is no card reader or other flash drive plugged in - could it be seeing an internal one?
I changed the hard drive boot sequence - sdb first- didn't help.  Fast boot is disabled.

It will boot if I go to a different kernel in the grub menu - does that mean I have a HD partition problem?

Thank you

---

### Post by oldfred on 2019-06-17
If another kernel boots, then something about new kernel not correctly configured.

I might boot from sdb's grub and in Boot-Repair run the full reinstall of grub to sdb and include install or reinstall of most current kernel.

---

### Post by eddugo on 2019-06-18
Hey Olfred;

This turned out to be a night mare.  I started with the reinstalls that you recommended and boot-repair stopped after running for about 20 minutes.  Restarted it and it stopped again.  Tried other fixes and after many hours of getting the same error message, i decided to wipe sdb clean and do a fresh install - even removed all partitions.  I didn't use any partitions and just gave it a "/" for the root.   Didn't work.  Got same error message even after running boot repair and making sure grub was on both drives.   I read through numerous forum articles - no help.  Finally I read an instruction for putting Ubuntu on a new hard drive with no partitions.  That article recommended a 250MB boot partition in the front of the drive.   When booted it went into Grub recovery so i ran boot repair again and it seem to be fine now.  Hopefully it will continue to work, but I don't really know what was wrong and fixed it.

Thank you

Ed

---

### Post by oldfred on 2019-06-18
Very old BIOS had a 137GB limit on where boot files could be on a drive. Rather than boot partition often better to just use a smaller 25 to 30GB / (root) partition and use rest of drive as /home.

But if it works that is fine.

---

### Post by eddugo on 2019-06-18
Thanks again  I will mark it solved.

---

