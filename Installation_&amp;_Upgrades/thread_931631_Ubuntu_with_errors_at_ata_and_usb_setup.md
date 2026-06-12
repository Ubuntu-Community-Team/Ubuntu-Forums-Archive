---
title: "Ubuntu with errors at ata and usb setup"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by xefialtis on 2008-09-27
I have a little older machine, my wife and kids use it for everything...I have decided to go the way of Ubuntu, instead of Windows, and, well, things aren't going so well...

Here is my hardware:
ASUS P4VBX-MX mobo w/ P4 3ghz processor.
1 gig ram, and 2 SATA 150 Segate 160 gb drives (which I want to RAID)

I pop the latest Install CD in for Ubuntu 8.04. It reads the disk, starts the install, and then it all starts to go to hell.

I get a:
failed to read native max address (err_mask=0x4)
and:
revalidation failed (errno=-5)

Then I get:
usb 5-4: device not accepting address 5 error -110

I searched this out a bit, and I found others had this same problem. I guess it has something to do with the ORDER the system is recognizing devices, and the install process creating conflicts between hardware and IRQ settings.
[http://ubuntuforums.org/showthread.php?t=862456&highlight=failed+read+native+max+address](http://ubuntuforums.org/showthread.php?t=862456&highlight=failed+read+native+max+address)
and
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

However, when I try to run the script in the live Ubuntu desktop, prior to executing the INSTALL, nothing happens, and having followed the other suggestions, I find that nothing changes and the same problem happens again.

When I do get into the install parts, it doesn't recognize my SATA hard drives, and it doesn't deal well with my mouse (choppy and slow).

Any ideas on how to change up the install of Ubuntu to get it to work right? Even if I have to disable the USB or something...

---

### Post by xefialtis on 2008-09-27
It is sometimes bad form to respond to your own posts, but I got it figured out...
pci = noacpi 
acpi = off

Take your pick, this worked.

---

