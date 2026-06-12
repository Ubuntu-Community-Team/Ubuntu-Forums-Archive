---
title: "grub rescue says invalid extent"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by Robert_Friberg on 2014-08-14
Hi,

Installed 14.04 from usb and seemed to work fine. When booting from HD (Corsair SSD) I get an 'invalid extent' error and a grub rescue prompt.
I ran boot-repair with info only, here's the output: [http://paste.ubuntu.com/8049539/](http://paste.ubuntu.com/8049539/)

---

### Post by Robert_Friberg on 2014-08-14
Update: I was impatient and ran the recommended the boot-repair repair option but still get the "Invalid extent" message and grub rescue prompt.

---

### Post by yancek on 2014-08-14
I'm not sure if this would work, but the link below to another post here at the forums seems to indicate a smaller / partition could solve the problem.

[http://ubuntuforums.org/showthread.php?t=1997316](http://ubuntuforums.org/showthread.php?t=1997316)

---

### Post by Robert_Friberg on 2014-08-15
Thanks.I did a reinstall using a custom partitioning scheme with partitions for boot, / and /home and now it's working. It would be nice to understand exactly what was wrong before. It's only a 240GB SSD disk, so I doubt the size was the problem.

---

### Post by oldfred on 2014-08-15
Is BIOS set for AHCI, not IDE? It should be AHCI anyway for trim to work with an SSD.

The issue is an old one that was with older IDE BIOS that only supported smaller drives up to 137GB and users who add larger drives. It also seems to appear in external drives using USB. And there was a bug in grub several versions ago where partitions over 500GB would be an issue.

But none of those should apply to your system.

---

