---
title: "New Ubuntu Install Boots Only to UEFI Screen"
date: 2017-12-13
forum: Installation &amp; Upgrades
---

### Post by mikenh on 2017-12-13
I installed 16.04 from a USB on my new build, choosing 'Something Else' partitioning. I followed a 'HowToGeek' post for suggested partitioning, and it seemed to go well, but now it just boots directly into the UEFI screen. In researching, it seems I should have designated an EFI boot partition. What are my choices now? Repair or reinstall, and how?

---

### Post by ubfan1 on 2017-12-13
Yes, you will need an EFI partition, 300M FAT32, for the bootloaders to boot UEFI. It doesn't have to be first, but is usually in first or second place. Try shrinking an existing partition and adding it (assuming your are on a GPT partitioned disk, and can easily add partitions).

---

### Post by oldfred on 2017-12-13
Older versions of Asrock have had issues with ASmedia ports. Do not use them. But do not know if your newer version still have them or not.
 Asrock Z170 ASmedia port issue
[https://ubuntuforums.org/showthread.php?t=2345564](https://ubuntuforums.org/showthread.php?t=2345564) 

Some even had DVD plugged into ASmedia port and had issue.

And best to have drives plugged into SATA ports in order, or use SATA0 first, then SATA1, etc.

Lots more info on UEFI boot in link in my signature.

---

### Post by mikenh on 2018-01-23
Thanks ubfan1  Your answer made the solution easy. oldfred thanks for the resources. (Correcting the partition delayed by a bad memory stick in the new build).

---

