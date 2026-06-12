---
title: "NO ROM BASIC System Halted"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by neubee on 2010-05-12
Trying to get started.  I using an old 1999 PC 512 MB RAM used to have W-2000.  I had difficulties getting CD to be boot drive.  I had to remove floppy drive to stop it from being the first drive.  I'm using the Linux Starter Kit with Ubantu Live 9.10.  My PC was having issues so I skipped the dual boot and went straight to a clean install.  I had to double click on WUBI in the disk directory to get the install started.  Install appeared to be going fine about 60%... then I got distracted to fix lunch for sick kid.  When I came back screen was black and I could not wake up screen with mouse or keyboard.  I turned off PC.. restarted and have message that says NO ROM BASIC System Halted.... what do I do?  I seem to be stuck in the middle somewhere.

---

### Post by psusi on 2010-05-12
Does the bios even see the hard disk any more?  That message usually indicates that the very old bios can't find any disk to boot, and still has an even older error message to print when that happens, that dates back to the time of the apple IIe when the BIOS had a built in BASIC interpreter that would start if it could not find a boot disk.

---

### Post by neubee on 2010-05-12
Yes I believe it does... when in setup under the Advanced tab the Primary IDE master shows WDC WD800JB-00JJC which I'm pretty sure is my Hard Drive.  Do you know if there is any way or hope to update the BIOS?  Maybe this machine is more of a boat anchor than I expected.  I was really excited with Linux first started the install I liked the look.

---

### Post by psusi on 2010-05-13
It sounds like the MBR may be corrupt then.  Either way to diagnose the problem you need to get the system to boot, which it sounds like you can't do if the bios won't boot from a cdrom or usb flash stick.

---

