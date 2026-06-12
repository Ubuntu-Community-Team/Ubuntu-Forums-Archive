---
title: "Ubuntu+XP+Zenworks=Reboot Loop"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by kubstix on 2007-01-26
Alright well I figured out the reboot looping problem when it reaches GRUB.  I have a 25GB NTFS Partition for Windows and a 10GB for Ubuntu.  I installed GRUB on the Windows Partition's MBR and everything has worked fine.  Soon as i install Zenworks Desktop Management for the Novell system on Windows, thats when it hits the fan.  I can boot into Linux as many times as I want with GRUB, but the minute I boot into Windows then reboot.......zenworks seems to erase GRUB and cause a reboot loop.  Has anyone heard of this, or know how I can get around it?

---

