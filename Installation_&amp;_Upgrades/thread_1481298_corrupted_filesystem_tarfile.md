---
title: "corrupted filesystem tarfile"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by complience on 2010-05-12
I'm trying to install a package (mythTV backend - but im sure the package is not at fault) and I keep getting this error

corrupted filesystem tarfile - corrupted package archive

New build - ubuntu lucid 32bit

I think it might be a hardware fault memory/hardrive/motherboard or somthing to do with an error in /home/ partition filesystem.

To be honest im not sure and its driving me mental

Would consider anyones input on possible causes of a Corrupted filesystem. 

Tried complete deleting (including cache) and reinstalling the package.

force fskchk , restarted = nothing.
Error checked the harddrive = nothing

frustrated as this is only the latest error in a series of problems ive been having with ubuntu on this build.

---

### Post by lemming465 on 2010-05-14
The first thing to do is reboot into memtest86+ and exercise your memory for a few hours, or even overnight.

If the package has any kind of checksum available (md5? sha256?) or digital signature, check that it wasn't corrupted by the download process.  Maybe download a new copy.

Disk corruption can be due to undervoltage power supply, leaky motherboard capacitors, firmware bugs on the disk controller, delaminating disk platters, or a zillion other problems.  See what smartctl from the smartmontools package says.

---

