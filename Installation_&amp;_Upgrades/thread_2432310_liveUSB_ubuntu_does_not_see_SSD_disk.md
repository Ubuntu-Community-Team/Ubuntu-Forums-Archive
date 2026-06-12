---
title: "liveUSB ubuntu does not see SSD disk"
date: 2019-11-30
forum: Installation &amp; Upgrades
---

### Post by altan1 on 2019-11-30
[FONT=arial]Hello everyone!
I've bought Dell inspiron 14 7490 recently and I'm stack with Ubuntu installation. It appears that there is no option in BIOS/UEFI to set SATA to ahci instead of Intel Raid on. I searched in the Internet and learned that linux has troubles with fake raid support but I don't have any option other then try to make in work. I tried to install Ubuntu 19.10 and 20.04 and Manjaro KDE Plasma 18.1.3 but neither of them were able to assess the main SSD drive installed in my laptop. I have updated to the last version of BIOS and updated SSD driver. I tried mdadm --assemble --scan but the output was no arrays found in config file or automatically. gparted sees only my flash drive with Ubuntu. Actually in lspci -v I see the position named RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode], but I don't no how to make other programs to notice it. I really need linux and don't need Windows yet, as far as I understand, even if I delete Windows, Bios will remain the same and it won't solve the problem. 
Is there any options to make linux notice the SSD drive? Please help me ;)
[/FONT]

---

### Post by CatKiller on 2019-11-30
If Windows is already on there, then it won't have shut down properly. It hibernates instead, to mask its boot-up time. When it does that it marks all the NTFS partitions as dirty; Ubuntu won't touch them because any change would break your Windows install. In Windows the setting is called Fast Startup or similar. You'll need to turn that off (note that Windows will turn it on again silently with updates) and shut Windows down properly. Then Ubuntu will show those partitions.

---

### Post by oldfred on 2019-11-30
Do not know details on 7490, these with 7390 & 7590 have it working.

       Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
[https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-7390-More-Options)
[https://ubuntuforums.org/showthread.php?t=2431791](https://ubuntuforums.org/showthread.php?t=2431791)
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)

---

