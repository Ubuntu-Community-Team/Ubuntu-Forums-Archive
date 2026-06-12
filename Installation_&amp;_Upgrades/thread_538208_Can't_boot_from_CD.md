---
title: "Can't boot from CD"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by caydence on 2007-08-29
I just received a free old computer from my workplace that I thought I could use for my kids.  I want to install Ubuntu on there, but the computer is so old, there is no option to boot from the CD-ROM in the BIOS settings.

The computer is an old Dell Inspirion 500Mhz computer with 2 SCSI hard drives.

Is there a way to boot the CD from the floppy drive so I can install it?  What other options do I have?  There is no OS on the computer right now.

Thanks!

---

### Post by khughitt on 2007-08-29
What OS is it running? There is now a [Windows installer for Ubuntu]("https://wiki.ubuntu.com/install.exe/") that you could try, although I've never used it myself.

---

### Post by logos34 on 2007-08-29
Try using **Smart Boot Mananger** floppy to boot the cdrom.

(using rawwrite in windows):
[https://help.ubuntu.com/community/SmartBootManagerHowto?highlight=%28smartboot%29](https://help.ubuntu.com/community/SmartBootManagerHowto?highlight=%28smartboot%29)

Or to make the SBM floppy on a linux machine, you want to copy the '**sbm.bin**' (~1.4MB) file from the **'/install'** dir on the ubuntu CD:
> 
**sudo mkfs.msdos /dev/fd0**
**cd /path/to/install ** (-->e.g. '/media/cdrom0/install')
**sudo dd if=sbm.bin of=/dev/fd0**
**cmp sbm.bin /dev/fd0**  (-->checks for errors)


---

### Post by caydence on 2007-08-30
Thanks for the help everyone!  Got it working.  Looking forward to giving Ubuntu a try.  :)

---

### Post by khughitt on 2007-08-31
Congrats :) What'd you end up doing to make it work?

---

