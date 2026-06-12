---
title: "After installation, &quot;PXE-E61: Media test failure, check cable&quot;"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by mr746977 on 2013-01-18
Hi everyone. I have a Lenovo Thinkstation D30 that I'm looking to load Ubuntu on. The computer shipped with Windows 7 preinstalled. Loaded in bay 1 is a 128 GB Samsung SSD for the OS and in bays 2 and 3 are two 2 TB hard drives configured as RAID1. I created a live CD of Ubuntu server and installed it on the SSD, but after installation and startup (running through the software RAID controller and BIOS), the system returns the error "PXE-E61: Media test failure, check cable". It suggests to press any key and try again, but this does nothing.

The next step I took was putting a Live CD on a thumb drive and booting from there. GParted sees that the drives have been formatted and partitioned properly, and, after reinstallation (and setting the intel RAID1 to mount /home), there is no change. I have also attempted to install with /boot and grub as their own partitions, and have confirmed that setting the boot flag to grub does not yield results.

My best guess is that the solid state drive is not being recognized (possible that it's booting to the RAID array), but installing another operating system seems to be a strange way to cause this.

If anyone has any pointers or ideas, it'd be greatly appreciated!

---

### Post by dabl on 2013-01-18
That error translates to "I can't find any bootable hard drives so I've moved on to try to do a network boot, and that ain't workin' either".

You need to check all drive power and data cables, verify that the SSD and 2 hdds are seen in BIOS, and that the BIOS boot sequence is correct.  It MAY be necessary to set the "boot" flag on the SSD, if that is where you installed grub.

(FYI, I have a PCI SSD, OCZ RevoDrive, and my BIOS does not recognize it as a bootable device, therefore I had to install /boot on a different SATA device.)

---

### Post by mr746977 on 2013-01-24
Sorry for the late reply; I've gone through all of the steps and it doesn't seem to work still. I now get an error that reads like so when I open Gparted in the live CD:

"/dev/mapper/isw_jjahdfhjh_Volume0 contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted- possibly by a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?"

This error also pops up for /dev/sdb and /dev/sdc, which appear to be the two component drives, and /dev/sdd, which is the flash drive the live CD runs from. Very odd, since I haven't fiddled with the partition tables since the install, or at least intentionally.

---

