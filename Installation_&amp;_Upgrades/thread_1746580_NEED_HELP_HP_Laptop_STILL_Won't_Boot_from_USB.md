---
title: "NEED HELP: HP Laptop STILL Won't Boot from USB"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by evilbellylint on 2011-05-01
Started a new thread, as the old one ([http://ubuntuforums.org/showthread.php?t=1738599](http://ubuntuforums.org/showthread.php?t=1738599)) had run its course with no solution.
 

**_Brief Overview:_**
[LIST]
[*]Prepared brand new Sandisk 4GB USB stick for use as Ubuntu Live USB distro
[*]Used Unetbootin to install the downloaded Ubuntu Minimal iso -- went smoothly.
[*]Entered BIOS setup on my HP dv7 laptop - arranged boot order so laptop would
boot from USB first.
[*]Regardless of what I attempt (and I've attempted a LOT) HP dv-7 still refuses
to boot from the USB distro.
[/LIST]**_What I've Already Troubleshot:_**[LIST=1]
[*]Suspected Sandisk USB stick contained U3 code, preventing it from booting: 
 
> Downloaded Sandisk's U3 Removal Tool to solve issue. Eventually discovered
this particular USB stick is not embedded with U3 code.
[*]Rebooted & tapped F9 to call up Boot Manager. Sandisk USB is listed as a boot
option, so that's not the issue.
[*]Used Windows Command Line to reformat USB stick a 2nd time -- just in case:
 
> DISKPART > LIST DISK > SELECT DISK 0 > CLEAN
> CREATE PRIMARY PARTITION
> LIST PARTITION > SELECT PARTITION 1 > ACTIVE
> FORMAT FS=FAT32
> ASSIGN
[*]Repeated entire Unetbootin procedure -- again, installed distro without error.
[*]Repeated Step 2 - HP dv7 laptop STILL claims no bootable device found.
[*]Repeated Step 3 - this time formatting as FAT16. Did not help.
[/LIST]**ADDENDUM:**
 
7. Also tried the above steps, using each of the available USB ports on the laptop, to no avail...
 
 
(If you glanced through my original thread, you noticed a forum member with an
HP dv-# laptop successful booting from a USB stick, using the same procedures.)
 
HELP??????? :confused::confused::confused:
 
EBL

---

### Post by dren on 2011-12-09
I have the exact same problem.

I have two dv7 laptops.  One of them boots from a USB disk that I made.  The other enters into the USB boot and sits there with a blinking cursor.

Did you ever get this resolved?  These laptops suck.

---

### Post by kurt18947 on 2011-12-09
You don't get a message "boot error" or anything like that?  If you have a Windows install, you might try formatting the USB stick in Windows then create the live install.  I have one desktop that will **only** boot from USB sticks formatted in Windows. It won't boot from factory formatted USB sticks nor from partitions created by disk utility.  This may not be your problem  but it might be something to try.  I start windows 7,  insert the stick, select and format.  Quick format has worked.  There is something in the BIOS that looks for some sort of flag that Windows sets but factory formats and formats done in Ubuntu disk utility don't set.  I'm not knowledgeable enough to compare the partitions and find the difference.  This only happens on one machine; others will boot from a stick not formatted with windows.

---

### Post by 2F4U on 2011-12-09
Did you try something else than unetbootin. It sometimes seems to be causing problems, at least to me. What comes to my mind, if you do it from Windows, is Fedora's live usb creator.

---

