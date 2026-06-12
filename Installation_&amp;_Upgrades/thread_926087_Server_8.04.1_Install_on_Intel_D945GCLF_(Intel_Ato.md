---
title: "Server 8.04.1 Install on Intel D945GCLF (Intel Atom)"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by alundrigan on 2008-09-21
When trying to install Ubuntu Server 8.04.1 on an Intel D945GCLF machine (Intel Atom processor, 2GB DDR2 RAM, 2x 750GB SATAII HDDs, Realtek GbE PCI card), the installation will either freeze or cause the machine to reboot.

Installation freeze
If I go through the installation procedure, partition the drives, and mark all partitions to be formatted, once the installation procedure reaches the point where it installs libssl0.9.8 (6%), it will hang.  The CD-ROM spins down, and the install will not respond to Ctrl-Alt-Delete.  A cold reboot is required to restart the machine. 

Spontaneous Reboot:
If I go through the installation procedure, partition the drives, and don't mark EVERY partition to be formatted (ie: I marked root for formatting, but not /boot), the machine will reboot spontaneously at some point early in the "Installing the base system" process....it happens to quickly to determine exactly where. 

Additional information:
(1) When I select the memory test option from the Ubuntu Server CD menu, memtest86+ goes wonky after testing ~20% of the memory...random stripes of colors, like the display memory has been trashed. 

(2) I have tried Ubuntu Desktop 8.04.1, with no success.  The LiveCD freezes during it's boot, and if I press Ctrl-Alt-F1 early enough, I get to see a kernel panic, most of which scrolls off the screen. 

(3) I am attempting to use the following partition setup:
```
RAID1 device #0 - 748.6GB Software RAID device
      #1 748.6 GB    ext3       F ext3     /
SCSI3 (0,0,0) (sda) - 750.2GB ATA WDC WD75000AACS-0
      #1  primary  501.7 MB  B  F ext3     /boot
      #2  primary    1.0 GB     F swap     swap
      #3  primary  748.6 GB     K raid
SCSI4 (0,0,0) (sdb) - 750.2GB ATA WDC WD75000AACS-0
      #1  primary  501.7 MB  B  F ext3
      #2  primary    1.0 GB     F swap     swap
      #3  primary  748.6 GB     K raid

```

Has anyone encountered a similar problem?

Thanks in Advance!
-Adam Lundrigan

---

### Post by nowshining on 2008-09-21
how long did u wait after the install froze the first time?? did you wait up to 10m-20m before doing anything else??

---

### Post by alundrigan on 2008-09-21
Thanks for the suggestion.  I did not leave it for as long as you suggested, however I am sure that the several minutes I did leave it should have sufficed.  I am repeating the installation process again, this time booting the netinstall from a usb stick (made via UNetbootin)...if it hangs on libssl again, I will leave it for the ~20 minutes you suggest.

---

### Post by alundrigan on 2008-09-21
When using the netinstall from USB stick, the install hangs on "Extracting dpkg (19%)".  The activity lights on both the network and USB stick stop, and the install showed no signs of progress for more than 20 minutes after that happened. 

I am beginning to think it has something to do with the RAM.  I have never encountered a bad stick of memory before, so I have no experience with what its effects would be, but as I mentioned in the first post memtest86+ seemed to trash the (shared) video memory when I ran it.

---

### Post by nowshining on 2008-09-22
okay did u burn the CD/DVD??

What speed did u burn it at??

did you check the checksum after burning??

---

### Post by alundrigan on 2008-09-23
> **nowshining said:**
> okay did u burn the CD/DVD??
Yes.  Also tried installing by booting the network install from USB stick.  Same result. 

> **nowshining said:**
> What speed did u burn it at??
24x

> **nowshining said:**
> did you check the checksum after burning??
No

---

### Post by nowshining on 2008-09-23
> **alundrigan said:**
> Yes.  Also tried installing by booting the network install from USB stick.  Same result. 


24x


No


try re-burning it but this time at 1x the speed or 4x the speed... higher speeds of burning have been known to cause problems...and re-burning a new disc at a lower speed usually helps..

---

