---
title: "Dual Boot with RAID 0?"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by kskwerl on 2011-04-17
So here's my scenario. I have (3) 60GB SSD. I want to use (2) in RAID 0 for Ubuntu and (1) alone for Windows 7.

What is the best way to get about this? I know how to create the RAID 0 array with the (2) disks and install Ubuntu on it. But how do I get the RAID array with Linux on it to dual boot with Windows 7?

Linux - RAID 0 (2) SSDs
Windows 7 - (1) SSD

Thanks.

---

### Post by dino99 on 2011-04-17
The dual boot is drived by the bootloader grub, but i'm not sure you can boot on a raid0 as it is not set at boot time yet

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

related thread: [http://ubuntuforums.org/showthread.php?t=1380981](http://ubuntuforums.org/showthread.php?t=1380981)

there is the stripping solution (software raid) but i wonder if its a good choice

---

### Post by kskwerl on 2011-04-17
> **dino99 said:**
> The dual boot is drived by the bootloader grub, but i'm not sure you can boot on a raid0 as it is not set at boot time yet

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

related thread: [http://ubuntuforums.org/showthread.php?t=1380981](http://ubuntuforums.org/showthread.php?t=1380981)

there is the stripping solution (software raid) but i wonder if its a good choice

Thanks for the help man, maybe I'll just use 1 SSD for each with no raid :\

---

### Post by dino99 on 2011-04-17
> **kskwerl said:**
> Thanks for the help man, maybe I'll just use 1 SSD for each with no raid :\

seems a good choice (often the simpler the better)

---

