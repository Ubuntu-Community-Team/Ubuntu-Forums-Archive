---
title: "dualboot question"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by peter203 on 2015-08-04
Hi if I decide to make dualboot, is it possible to regain back the space if I do not like the results? If so, how is that possible? Thanks alot

---

### Post by oldfred on 2015-08-04
You can use partition editing tools like gparted to delete Linux partitions and Windows own disk tools to expand the NTFS partition.
And you have to restore Windows own boot loader before deleting Ubuntu partitions. You should have a Windows repairCD or flash drive, anyway.

Before install you should use Windows disk tools to shrink the NTFS partition and reboot immediately so it can run chkdsk and make repairs for its new size. Any size change needs a chkdsk.

But you can try Ubuntu from the live installer. That will make no changes to your system.
It is a live system that is fully functional. It just will not be as fast as flash drives & USB ports are not as quick as SATA ports and internal drives. If a newer system with USB3 & USB3 ports it works pretty good. But live system is not updateable. If you want you can install other software to test, but it is gone when you reboot. You can add persistence to save some of your data if flash drive is a bit larger.

Is system newer UEFI or older BIOS?
Depending on specs of system and if an older system then other flavors of Ubuntu may be better.

---

### Post by howefield on 2015-08-04
Asking the question probably means you aren't ready to implement the answer ;)

Assuming that you currently have a Windows machine and want to dual boot with Ubuntu but then later wish to revert back to single booting Windows would simply mean reallocating the ubuntu space to where it came from with the Windows disk management tool, but before you could do that you would probably have to fix the Windows boot loader. All easy enough stuff if you feel confident.

Do ensure that you have a backup of all the data you wouldn't want to lose and have made recovery disks of your windows installation.

---

### Post by peter203 on 2015-08-06
Thank you very much for your help guys! :)

---

