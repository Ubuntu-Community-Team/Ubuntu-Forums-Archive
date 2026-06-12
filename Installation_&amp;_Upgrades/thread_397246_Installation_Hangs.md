---
title: "Installation Hangs"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by RichardM33 on 2007-03-30
I've successfully installed 6.06 LTS on a Thinkpad and a Dell Dimension but can't get my cd to work on a clone with a SuperMicro motherboard.

When I boot from the Live CD, I get a notice that the system has identified a bootable cd during the SCSI Bios loading. Instead of the splash screen I get a text 'boot' prompt with some optional parameters. I've tried several combinations noacpi, etc. but each time the installation hangs at 'decompressing the kernel...'

My system configuration is:

SuperMicro S2DGU
Dual Processor - Slot2 - Two Pentium III Xeon 550Mz Installed
Adaptec 7890 SCSI on motherboard
512MB ECC SDRAM
Two 9GB SCSI HDD
Diamond Fire GL-1 Video
(also I/O card, SoundBlaster card and Hauppauge TV card installed)

Windows 2000 Pro is installed on a NTFS partition on the first HD.

According to one linux website the  motherboard is listed as supported.

Any help or direction would be appreciated. TIA

Richard

---

### Post by yabbadabbadont on 2007-03-30
That sounds more like a bad CD than anything else.  If possible, burn a new one on a different computer using the slowest speed possible.

---

### Post by RichardM33 on 2007-03-30
Thanks for the suggestion, yabadabadont, but since it boots and I just used it to install Ubuntu a couple of days ago I don't think that's it.

Update:

It was the video card. I swapped out the Diamond Fire GL-1 (:( ) for an SIS card I had and the installation completed flawlessly.:)

---

