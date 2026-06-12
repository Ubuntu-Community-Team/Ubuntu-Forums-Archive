---
title: "zram - Rebuilding a Dell xps13 L322X developer edition"
date: 2013-07-07
forum: Installation &amp; Upgrades
---

### Post by Byb on 2013-07-07
Hi
I rebuilt my laptop to get rid of the preloaded FAT partitions. At the same time I jumped from 12.04 to 13.04 through a total ssd reformat.
Before I did it I checked some settings I thought would be useful (fstab, /proc/swaps and all installed packages), unfortunately I'm not skilled enough and I forgot some things about the ssd topology and swaps
Please could some one confirm that zram-config is not installed and show me from a same model laptop that is still in factory installation state the outputs of:
sudo hdparm -i /dev/sda
sudo hdparm -I /dev/sda
and 
dmesg | grep zram



Thank you very much

[EDIT]
Well, in the lap time I reloaded the original factory image 3.2.0-30-generic#48+kamal6~DellXPS and found /dev/zram0 is not there. I tried to follow the few steps I walked before I rebuilt to 13.04. To be honest I jumped directly to the biggest step I postponed for some weeks: install the 580 updates proposed by update-manager, which drove me in 3.2.0-49-generic #75-Ubuntu, the one that introduced me to zram - note here that zram-config is NOT installed although I see 1*4GB zram0.
Once I rebuilt my box to 13.04 (kernel 3.8smthing) I noticed zram disappeared and I began to learn things about it. I found zram-config but it made different settings , 4*about~1GB zramX.

I searched the web and read many things but all seem obsolete; Please were shall I read why zram went in then out to figure whether I need it or not. My main concern is about hibernation and SSD health.

Thanks again

---

