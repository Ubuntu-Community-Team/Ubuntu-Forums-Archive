---
title: "Ubuntu 10.04 LTS HTPC/Blu-Ray?"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by freezkatlodge on 2010-08-28
**Liteon BD-ROM Blu-Ray?**             
                                                              I'm trying to build HTPC with a SATA LiteOn BD-ROM  iHOS104-06 drive 
on an Abit NF-M2SV with an AM2 5400 (I think)
2GB GSkill ddr2-800 (red heatsinks) running at 1.9v
470W PCP&C Silencer

[http://www.abit.com.tw/page/en/motherbo](http://www.abit.com.tw/page/en/motherbo) ... ME=NF-M2SV

 Previously, I installed fedora8 on the 40GB SATA Hard drive no problem  with an IDE cdrom drive. It sat for a year, then I decided to make a  Blu-Ray player and DVR out of it. I wanted to upgrade to Fedora13. So I  tried the online "Pre-upgrade" tool. That messed it up. So I burned a  LiveCD. The Blu-Ray drive read the cd but died during the install saying  it couldn't read any drives, 

I pulled out a Ubuntu 10.04lts live cd and the drive couldn't read it at all. Like the boot=nocdma issue with old cd-rom drives.

I was able to install U10.04 using an ide cdrom drive.

Things to note:
SATA HDD and BD-Rom drive were detected in BIOS
XP install died when it started writing on the HDD ...might be bad hdd

edit:
The new kernel still doesn't fix issues with some  nv sata controller doo-dad. There doesn't appear to be a click on patch either. LiteOn got their drive to work on Mandriva 2007 so according to their non-response for the last 2 years, "they're done", So until a kernel is released or an update comes through to fix this, my Linux HTPC is impossible

---

### Post by freezkatlodge on 2010-08-29
bbb

---

