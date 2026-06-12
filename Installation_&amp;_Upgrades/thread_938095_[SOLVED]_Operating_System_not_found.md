---
title: "[SOLVED] Operating System not found"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Person98 on 2008-10-04
MY friend gave me his laptop to fix, it had an error "operating system not found" which appears directly after it passes the press f2 to enter bios screen. Since he didn't have his Windows CD i decided to install ubuntu (i am a user). The install went fine, it formated and installed without error (so i know the hard drive works), however when i rebooted off the install, it gave me the same error "operating system not found" The odd thing is that the bios can see the harddrive, the live cd can read and write the hard drive, I was thinking that possibly the master boot record might be corrupt but i would have though installing ubuntu would have fixed that. Any ideas on what i should do next? i could try updating the bios if you think that might help but it seems like it would be a pain to do

---

### Post by Phreaker on 2008-10-04
It's probably the mbr. 
If the hdd has more than one partition ,check which one is bootable and active

---

### Post by melojo on 2008-10-04
from the live cd type sudo fdisk -l from a console and post the output.
This show your partitions

---

### Post by Person98 on 2008-10-04
hi thanks for the advice the fdisk shows:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255heads,63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280
Disk identifier: 0x881e3473

Device  Boot   Start    End    Blocks     Id  System
/dev/sda1  *       1    7112   57127108+  83  Linux
/dev/sda2       7113    7296   1477980     5  Extended
/dev/sda5       7113    7296   1477948+   82  Linux Swap / Solaris


any thoughts?

---

### Post by melojo on 2008-10-04
have a look here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Person98 on 2008-10-04
i tried both of the "quickstart" and "Overwriting the Windows bootloader" sections and neither worked i still get the same error, I was looking in the BIOS in the boot priority, and noticed there is an ! in front of the the harddrive, do you perchance know what that means?

---

### Post by Person98 on 2008-10-04
nevermind apperently that means the hard drive is disabled therefore it is fixed huzzah, thanks for the help

---

