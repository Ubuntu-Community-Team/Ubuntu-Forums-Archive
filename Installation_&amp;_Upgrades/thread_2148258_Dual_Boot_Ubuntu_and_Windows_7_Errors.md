---
title: "Dual Boot Ubuntu and Windows 7 Errors"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by hootis on 2013-05-24
So, I've tried many things and will probably forget a few but here's basically what's going on.
I have 2 hard drives one is 3tb(which lead to problems installing windows but has since been fixed) and I want to install windows 7 on the 3tb drive and ubuntu on the other.  At the moment i have both installed however when I use bios to boot into windows it crashes immdiately and restarts into bios.  However when I unplug the sata port to the Ubuntu install I can boot into windows with no problems.  I can boot into ubuntu with both plugged, and I was trying to get grub to detect the windows install with no luck ( I mounted the drive, then ran update grub, it detected my usb drive as a boot option but not the windows hard drive even though it was mounted which lead me to think its something to do with the drive being over 2.2tb).

note I have tried installing windows with both drives plugged in and it fails to reboot during installation until the ubuntu drive is unplugged.  I have currently installed both windows and ubuntu while the other drive was unplugged this seemed to work for a few other people, not sure if it makes a difference in my case and the end result is the same.


The thing I was going to try next was to reinstall Ubuntu with a boot partiton on the windows drive as well as installing grub on the windows drive.  Any suggestions, I've read a bunch of dual boot threads but non really seamed to match my problem.

---

### Post by fantab on 2013-05-25
To use HDD more than 2TB you have to use GPT partition table as the older MBR will not support HDD more than 2TB. With GPT Windows will only Boot with UEFI, but Ubuntu will boot in both UEFI and BIOS modes. If you want to dual boot then both OS MUST boot in either UEFI or in BIOS and not one in UEFI and one in BIOS.

Since you have a 3TB drive you will have to use GPT table and Windows will only boot from GPT in UEFI mode. Does your BIOS support UEFI Boot? You can check this from Bios-setup.
Have you enabled RAID from BIOS? or Were the HDDs you have were at any point in time used in RAID array? Check the BIOS Setup to confirm in what mode is SATA set: it will be IDE, AHCI and RAID. We want AHCI, no RAID and no IDE.

If you have an Intel board then check if you have something called 'Intel Smart Response Technology [SRT] enabled. You have to disable it.

Confirm the above and we can take it from there.

---

