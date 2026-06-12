---
title: "Can't install any linux OS on my server - BUG: soft lockup - CPU#0 stuck"
date: 2022-01-01
forum: Installation &amp; Upgrades
---

### Post by zealios on 2022-01-01
I have been struggling for a while, and any help would really make my day :) Thanks.


Server Hardware:
Dell R5500 Poweredge
2x: Intel Xeon 5000
128gb DDR3 RAM
Unknown ****** GPU (i think Nvidia)
4x: 2TB WD HHDs


I recently wiped my disks on my server, since i wanted to switch to a new OS.
I wanted to use Ubuntu Server, but when o tried installing the same error kept popping up;


BUG: soft lockup - CPU#0 stuck
and something about snd_hda_intel


First off, this is unlikely to be a hardware issue on my side, since my hardware was active recently and was running with no problems.
After a little research I think it seems to be a kernel bug or something. I tried with Ubuntu Desktop and Fedora Server -same issue.
I have tried the online fixes i could find, like adding nouveau.modeset=0 after quietsplash, and I tried to select the option nomodeset, but still nothing changes.
I saw someone talking about a BIOS update fixing it, but I don't know how to check if i'm up to date, or what updates I need.
Also I don't know if did anything wrong with the modeset, it seems to solve everyones problem online.


Again I would appreciate ANY help you guys could give.

---

### Post by ubfan1 on 2022-01-01
sudo dmidecode will output lots of info, under the BIOS Information section, find the version.  Then check with Dell for any firmware updates for your hardware.  The updates are vendor specific, maybe a windows .exe file, a DOS exe file, or a bin file that you just have to put onto a USB and select the update option at power on.

---

