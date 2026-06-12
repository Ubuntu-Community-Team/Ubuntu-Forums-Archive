---
title: "Vista will not boot after install Solved!"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by yyyc186 on 2008-06-05
Hello all,

I finally broke down and bought a new laptop.  Toshiba Satellite A215-S5848.  It came pre=loaded with Vista naturally.

First off, I had a PITA of a time getting any CD-ROM Backup utility to boot so I could get a good image backup.  There seem to be a few BIOS issues for Acronis, and about 3 other packages I had.  I wanted to get a good image before attempting the install.  I finally ended up trying some Linux backup software from a place in the UK.  It was cryptic, but it would boot.

What I learned from that is, if you have a USB keyboard hooked up to your notebook, in particular an HP keyboard, unhook it.  Some backup software also boots better if you unplug your network cable.

The install went smoothly.  I never installed any restricted drivers.  I'm installing the 64-bit AMD version.  I even let it download and install all of the KDE stuff since that is the best (most professional) desktop on Linux.

After about 4 hours of installing software, copy files around, etc.  I decided to try booting Vista again just to ensure all was well.  Imagine my dismay when it crashed, then tried to throw me into recovery where it said there were no operating systems on my notebook.  Arrrggghhh.

To add insult to injury, most of the computer stores around here don't stock software.  If you want software, you have to go to an office supply store (in this case Office Max).

I've been in software a long time and knew what had happened.  Vista installs a small boot loader partition in front of the actual Vista partition.  Gparted didn't bother to update the loader partition.  Since the drive parameters didn't match what the loader had it wouldn't load.

Partition Commander Professional 10 to the rescue.  I had to play around unhooking things to get it to boot due to the BIOS problems with USB and network card, but I was able to boot from the CD.  After you do that, all you have to do to fix your problem is change your Windows partition size, then click on Apply to write the changes to disk.  This software is smart enough to update the boot loader partition parameters with the new size of your NTFS partition.

Your next boot into Vista will force a ScanDisk on you.  It will then force a boot, but after that you can load Vista or Ubuntu just fine.

:)

---

