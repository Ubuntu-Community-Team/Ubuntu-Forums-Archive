---
title: "alternate install with external PATA CD-ROM using Cypress Semi chipset"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by zeus77 on 2010-05-26
Oh boy, this was a doozy.  Maybe this will help someone out.

This applies to you only if you meet ALL of the following four conditions:
[LIST][*]you're trying to install Ubuntu 10.04 **alternate** CD (or, heck, maybe a later version if this bug doesn't get fixed).
[*]you've got a USB-connected external PATA CD-ROM drive
[*]the chipset used in that external CD-ROM enclosure is a Cypress Semi
[*]while going through the install, you get a pop-up message that says, "No common CD-ROM was detected".[/LIST]
Again, this only applies to people using a **Cypress Semi** chipset; don't waste your time with this if you're not in this boat.  If you're not sure which chipset your external CD-ROM drive uses, connect it to a Linux box that works, and type 'lsusb'.  But that's beyond the scope of this here post.

Here is the fix to get things working.  You'll need to find a working computer that already has the version (e.g. x86, amd64, etc) of Ubuntu 10.04 installed on it which is identical to the version you are trying to install.  I realize this is a bit of a chicken-and-egg problem.  Good luck with that.

On a working Ubuntu 10.04 PC:
[LIST=1][*]Insert a USB stick.  
[*]Copy the file called 
/lib/modules/2.6.32-21-generic/kernel/drivers/usb/storage/ums-cypress.ko
to the USB stick.  Note that your kernel version (e.g. 2.6.32-21) may be slightly different in the last 2-digit number; that shouldn't be a problem.[/LIST]
Now, on the PC where you're trying to install Ubuntu, when the error message pops up during install, do this:

[LIST=1][*]"Load CD-ROM drivers from removable media?" --> Choose NO.
[*]"Manually select a CD-ROM module and device?" --> Choose YES.
[*]"Module needed for accessing the CD-ROM" --> Choose NONE (only choice).
[*]At the next screen, hit Alt-F2.  You will be dumped to the command line.  Press Enter for the command prompt.
[*]Type 'ls /dev/s*' to get a list of devices.  Take a good look at this list, and maybe even write it down.
[*]Insert the USB stick.
[*]Type 'ls /dev/s*' again to get a list of devices.  Note which device is NEW, which corresponds to the USB stick.  For me, it was /dev/sdb1.  In the following, I will assume it was also /dev/sdb1 for you (so replace it with whatever below if it's something different for you).
[*]Type these commands
```
mkdir /media/tmp
mount -t vfat /dev/sdb1 /media/tmp
cd /media/tmp
insmod ums-cypress.ko
```
[*]Wait a second or two.  Hopefully the CD-ROM drive starts spinning.  Type 'ls /dev/s*' again, and hopefully yet ANOTHER new device shows up.  For me, it was called /dev/sr0.  
[*]Press Alt-F1.  Back to pretty color land.
[*]In the input box which probably says '/dev/cdrom' by default, change it to '/dev/sr0' or whatever is the case for you.[/LIST]

Hope this helped.
zeus77

---

