---
title: "help!! duel boot win7 &amp; Ubuntu on RAID-0"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Ceiber Boy on 2011-01-13
in BIOS i configured 2 1TB HDD in RAID-0

installed win7, it saw 1 2TB HDD, installed fine.

went to install ubuntu, it did not see win7 or give an option to resize the partition

resized the partition in win7 leaving 1TB of unalocated space

installed ubuntu into unaclocated space made by win7

near end of install GRUB failed to install, my only option was to finish the install without grub! so windows will boot but not ubuntu.

both OS are clean installs and can be reinstalled

the plan was to install both os on same RAID-0 array

please help

Thanks

---

### Post by Ceiber Boy on 2011-01-13
do i use the alternate CD and use the software RAID install to install into the space created by win7?

---

### Post by Ceiber Boy on 2011-01-15
ok.. this is what I've learned and done, i hope someone in a similar situation can benefit from this.

With GRUB it can only be installed on a single HDD as it's drivers dose not support multi disk installation, so if one was using a hardware RAID controller (unlike me who was using a BIOS RAID controller) Ubuntu would just see a single drive and all would install fine. However in my situation i wanted to duel boot on a RAID-0 with win7 and Ubuntu.

Windows saw a single drive and installed, when installing Ubuntu it wanted to wipe the entire install of win7 and install so i had to resize the partition in win7 and then install in unallocated space, which it did but GRUB would not install!

So, resetting the BIOS to non-RAID mode i installed win7 on the first HDD (so its not in RAID mode) and used win7 to resize its partition, then using the Ubuntu alternate i configured software RAID-0 the first partition being on the unallocated free space made by win7 on the first disk and the same amount on the second HDD. This leaves me with a free partition on the second disk the same size as the win7 partition on the first disk.

As i'll only use win7 occasionally to run specialist software that WILL NOT run in wine or windows in Virtual Box, I'm not to bothered that its not on a RAID partition.

Hope this helps someone.

---

