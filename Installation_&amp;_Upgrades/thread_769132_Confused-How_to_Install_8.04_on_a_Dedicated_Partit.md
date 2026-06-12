---
title: "Confused-How to Install 8.04 on a Dedicated Partition on a Windows Machine"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by dragonfly2008 on 2008-04-26
hi, i'm a bit confused on the best way to install Ubuntu 8.04 desktop on a machine which has a Windows install.  i have an unallocated partition i'd like to use, but when i run the install CD i'm not sure whether or not Ubuntu will modify the boot loader to allow a boot into either Windows or Unbuntu.  i say this because it doesn't give any indication that it detected my Windows installation, and the default install was Guided, using the entire hard drive.  if i select Guided, using free space only or manual and select the partition i want, will it modify the boot loader properly?

i'm aware that it can be installed using Wubi from within Windows, but my understanding is that it would be on an existing NTFS partition being used by Windows, and that moving that install to a dedicated partition is not yet supported using LVPM for the 8.04 release (according to the Wubi wiki).

i haven't been able to find an answer posted anywhere so i thought i'd ask here.  any thoughts or suggestions would be greatly appreciated.

---

### Post by Pumalite on 2008-04-26
Install Ubuntu, go Manual and make 3 'New' partitions in the unallocated space:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home
Then press 'Forward'. The installer will do the rest. Let Grub install to the MBR and you'll have dual boot.

---

### Post by dragonfly2008 on 2008-04-26
wow, that was a fast response, thank you very much for the feedback.  i'm going to try the install later today or tomorrow, i'll post a reply and let you know how it went.

---

### Post by Pumalite on 2008-04-26
Good luck.

---

