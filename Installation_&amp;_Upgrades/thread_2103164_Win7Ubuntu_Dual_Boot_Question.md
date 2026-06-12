---
title: "Win7/Ubuntu Dual Boot Question"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by shvman on 2013-01-09
I installed Ubuntu 12.04 on a single disc which  already had Windows 7 x64 on it.  Windows was on two primary partitions, a very large partition C: and a small 100 mb partition.  I've been using this computer for the past year with no problems.  

During the installation of Ubuntu, I made four partitions: 1) /boot, 2)/(root), 3)/home and 4) SWAP.   After doing some reading, I decided to install grub in the /boot partition, rather than in the MBR to avoid problems.  As a result, I boot to the Windows bootloader and if I select Ubuntu 12.04 rather then Window,  I see the Grub boot screen.  

How do I delete Windows 7 on this system  leaving a functional Ubuntu in place?  I assume I delete the main Windows partition (C), somehow delete reference to the Windows 7 bootloader in the MBR and then move or copy Grub from its present location to the MBR.  

Any help would be appreciated.  I've been reading about this for two days and at this point, I'm confused.  

Thanks.

---

### Post by darkod on 2013-01-09
It's very easy, but do it BEFORE deleting the windows partitions.

If you have only one hdd, it will be called /dev/sda. If you have more than one, you might need to use another device name like /dev/sdb, /dev/sdc, etc.

Boot your ubuntu installation and open terminal. Under the above assumption you want the grub2 bootloader on the MBR of the /dev/sda disk, execute the command:
```
sudo grub-install /dev/sda
```

That will install it on /dev/sda which is the MBR of the disk. After that you can test if you get the grub2 menu at boot instead of the windows bootloader, and if it works fine delete the windows partitions.

---

### Post by shvman on 2013-01-09
Thank you very much.

---

