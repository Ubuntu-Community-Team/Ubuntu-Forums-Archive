---
title: "Cannot Install Ubuntu on Hardware FDE SSD"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by smilon on 2013-02-23
I have a new Dell Latitude laptop with an Opal compliant Hardware FDE SSD. When installing Ubuntu 12.04.2 it fails to write to the disk. I get the following error:

Partition Disks
Input/output error during write on /dev/sda
ERROR!!!

Now, if my understanding is correct, hardware FDE shouldn't be making any difference here given it should be transparent to Ubuntu? Does anyone have any idea what would cause this? The disk currently has Windows 7 on it (which I would like to replace with Ubuntu).

---

### Post by smilon on 2013-02-23
I have tried using BIOS and UEFI in case it made a difference, it didn't... still can't write to the disk :(. I would have thought it would be unlocked when you get passed BIOS?

---

### Post by smilon on 2013-02-24
Okay, figured it out. The Dell security software on Windows 7 ties in with the BIOS. This means the drive isn't unlocked until just before windows starts (not after the initial BIOS password).

I logged into Windows, disabled all security via the Dell security manager, then installed Ubuntu no problems.

---

