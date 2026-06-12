---
title: "Unable to upgrade Yaru-theme-icon on ubuntu 19.04"
date: 2019-09-14
forum: Installation &amp; Upgrades
---

### Post by viraj.shah on 2019-09-14
i am trying to upgrade the apps but not all applications are being upgraded. triedto use the following commands ```
sudo apt-get clean
``` and the ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` and tried using ```
sudo apt-get upgrade --fix-missing
```

Still I am getting this Error:
[B]sudo apt-get upgrade --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  yaru-theme-icon
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,830 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Ign:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main amd64 yaru-theme-icon all 19.04.3
Err:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) disco-updates/main amd64 yaru-theme-icon all 19.04.3
  Connection failed [IP: 91.189.88.24 80]
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/y/yaru-theme/yaru-theme-icon_19.04.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/y/yaru-theme/yaru-theme-icon_19.04.3_all.deb)  Connection failed [IP: 91.189.88.24 80]

[/B]

---

