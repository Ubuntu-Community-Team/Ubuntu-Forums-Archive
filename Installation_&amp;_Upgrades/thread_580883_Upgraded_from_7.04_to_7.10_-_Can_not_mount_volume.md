---
title: "Upgraded from 7.04 to 7.10 - Can not mount volume"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by UKCamaroSS on 2007-10-19
Hi,

I am very new to linux... downloaded 7.04 last week and used the update manager to upgrade to 7.10 last night.

Everything on my pc worked with 7.04, but after the install of 7.10 I got the following message:

Can not mount volume.
$MFT has invalid magic.
Failed to load $MFT:Input/output
error failed to mount 'dev/sda1' :Input/Output error
NTFS is either inconsistent, or you have hardware faults, or you have a SOFTRAID / FakeRAID hardware.

My pc specs are:
AMD Athlon 64 300+ 
512 MB 
Nvidia GeForce FX5700LE graphics card

2 harddrives:
C: 75GB 
E: 228 GB

This is a dual boot pc, C: drive has both Windows and Ubuntu on it. Ubuntu can not mount E: drive.... 

I have booted back into windows and ran chkdsk /f, then rebooted windows (twice), but on going back to Ubuntu the drive was still not mounted.

What can I do to fix this...(it worked in 7.04 with no issues when I installed from the LiveCD).

Thanks,

---

### Post by UKCamaroSS on 2007-10-19
Hi,

Does anyone know what I need to do, to correct this mount issue?

---

### Post by vambo on 2007-10-19
Does it boot up with the older kernel? When you boot select 2.6.20-16 (I think that's it) and not the Gutsy kernel - 2.6.22-14.

---

