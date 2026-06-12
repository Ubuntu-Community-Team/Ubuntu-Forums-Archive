---
title: "Error when installing - connection status changed"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by drifter129 on 2008-07-14
Hi all,
I am attempting to install ubuntu on my media PC as i have finally had enough of vista media centre - and plan to use MYTHTV.
initially i tried installing ubuntu over the top of vista but got the error message:

[204.440000] ata2: (irq_stat 0x00000040, connection status changed) buffer I/O error on device fd0 logical block 0
exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0x2 frozen.

the message repeats over and over again and the numbers at the start appear to increase each time.

I have tried completely reformatting my hard drive and repeating the install - same error. I then tried installing windows XP and then repeating the install but still get the same problem. :(

does anyone have any ideas?

system spec as follows:
   
AMD AM2 Athlon 64 4600+   
Asus M2A-VM 
2GB (2x1GB) Corsair TwinX XMS2, DDR       
1000 GB Samsung HD103UJ Spinpoint 
Pioneer BDC-202BK 5x Blu-Ray Reader
Asus WL-138g V2 54G Wireless PCI

---

### Post by Partyboi2 on 2008-07-14
Try disabling the floppy in the bios or at the main menu press F6 and try adding ```
nofloppy
```

---

### Post by drifter129 on 2008-07-14
OK - i don't have a floppy drive installed in my system, but i will certainly check in the BIOS and try the fix you have suggested this evening.

---

### Post by drifter129 on 2008-07-14
OK - checking the BIOS, the floppy was enabled. I disabled it,but still get an error message

the message has  changed slightly in that it no longer gives the bit about buffer I/O error.It now reads:

[313.188000] ata2: (irq_stat 0x00000040, connection status changed)
[315.528000] ata2: exception Emask 0x10 SAct 0x0 SErr 0x40c0000 action 0x2 frozen.

it just repeats again and again, but with different numbers at the start..

---

### Post by drifter129 on 2008-07-15
have also tried adding "nofloppy" at install menu, but still same problem..

---

### Post by zipperback on 2008-07-15
Check in your computer BIOS, and see if there is a setting for something like "boot record protection" or "virus protection" or something similar.
Some systems have a bios option that you can turn on which prevents changes to the MBR (master boot record) portion of the hard drive.

If that is active, turn it off, and then try the installation again.

Also be sure that you have run the media check from the boot menu on the Ubuntu LiveCD.

I hope this helps you.

- zipperback
:popcorn:

---

### Post by Partyboi2 on 2008-07-15
Another thing you could try is booting using pci=nomsi as a boot option. (Same way you tried nofloppy)

---

### Post by drifter129 on 2008-07-15
still no luck i'm afraid.

I checked the BIOS several times, and there is nothing that mentions MBR or virus protection.
I also tried the option of pci=nomsi - this didn't work either. 
I have also changed the SATA controller option in the BIOS from IDE  to AHCI - same issue.

I'm confused that the message refers to ata2 when i have my primary drive connected to ata1.

in case it helps, the message is prefixed with a header of: "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7"

---

### Post by drifter129 on 2008-07-17
ok - i managed to "resolve" this by taking out the HDD and hooking it up to my primary PC upstairs and installing ubuntu that way. Luckily it did boot up when i put the drive back in my media PC. still get the same message when rebooting or shutting down though (i have to switch off by holding down the power button). 

I have founfd the following thread regarding issues with the M2A-VM motherboard running linux, so will give these actions a try next.

---

### Post by drifter129 on 2008-07-17
here is the link to the thread: [http://ubuntuforums.org/showthread.php?t=435075](http://ubuntuforums.org/showthread.php?t=435075)

---

### Post by drifter129 on 2008-07-22
still having major problems, and on the verge of giving up on linux.

after putting the HDD back into my media PC after installing ubuntu, i have found that the OS is not detecting the DVD-RW at all. when inserting any disc, no icon appears on the desktop. the cd-rom folder just shows "0 items". I can hear the drive spinning and trying to read the disc. This is preventing me from loading ndiswrapper from the ubuntu disc.

I am now wandering if the initial error message is in some way related to the optical drive, as it is a SATA drive?

---

### Post by thefortrees on 2009-06-14
I had the same problem with my SATA hard drive - disabling ACPI seemed to do the trick!

[http://ubuntuforums.org/showthread.php?t=257912](http://ubuntuforums.org/showthread.php?t=257912)

---

