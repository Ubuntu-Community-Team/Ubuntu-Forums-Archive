---
title: "Apt packages have been kept back"
date: 2022-09-05
forum: Installation &amp; Upgrades
---

### Post by oygle on 2022-09-05
I have been encountered this a lot over the last few months ..

```
$ sudo apt update
```

> Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates InRelease              
Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-backports InRelease            
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                                               
Hit:5 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy InRelease                                  
Ign:6 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 InRelease                     
Hit:7 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 Release 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
62 packages can be upgraded. Run 'apt list --upgradable' to see them.

```
$ sudo apt upgrade
```

> Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  breeze breeze-cursor-theme drkonqi kde-config-updates kde-style-breeze kde-style-oxygen-qt5 kdeplasma-addons-data kinfocenter kscreen ksystemstats
  kwin-addons kwin-common kwin-data kwin-style-breeze kwin-x11 libcolorcorrect5 libkf5sysguard-data libkfontinst5 libkfontinstui5 libksgrd9
  libksysguardformatter1 libksysguardsensorfaces1 libksysguardsensors1 libksysguardsystemstats1 libkwaylandserver5 libkwineffects13 libkwinglutils13
  libkwinxrenderutils13 libkworkspace5-5 libnotificationmanager1 liboxygenstyle5-5 liboxygenstyleconfig5-5 libplasma-geolocation-interface5
  libprocesscore9 libprocessui9 libtaskmanager6 libweather-ion7 milou oxygen-sounds plasma-calendar-addons plasma-dataengines-addons plasma-desktop
  plasma-desktop-data plasma-discover plasma-discover-backend-fwupd plasma-discover-common plasma-nm plasma-pa plasma-runners-addons
  plasma-wallpapers-addons plasma-widgets-addons plasma-workspace qml-module-org-kde-ksysguard systemsettings xdg-desktop-portal-kde
The following packages will be upgraded:
  bluedevil firefox kde-config-sddm layer-shell-qt liblayershellqtinterface5 plasma-workspace-data sddm-theme-breeze
7 to upgrade, 0 to newly install, 0 to remove and 55 not to upgrade.
Need to get 72.0 MB of archives.
After this operation, 121 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 bluedevil amd64 4:5.24.6-0ubuntu0.1 [310 kB]
Get:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 liblayershellqtinterface5 amd64 5.24.6-0ubuntu0.1 [16.0 kB]
Get:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 layer-shell-qt amd64 5.24.6-0ubuntu0.1 [5,210 B]
Get:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 plasma-workspace-data all 4:5.24.6-0ubuntu0.1 [6,991 kB]
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 sddm-theme-breeze amd64 4:5.24.6-0ubuntu0.1 [612 kB]
Get:6 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy/main amd64 firefox amd64 104.0.2+build1-0ubuntu0.22.04.1~mt1 [63.9 MB]
Get:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 kde-config-sddm amd64 4:5.24.6-0ubuntu0.1 [110 kB]
Fetched 72.0 MB in 25s (2,851 kB/s)                                                                                                                        
(Reading database ... 240623 files and directories currently installed.)
Preparing to unpack .../0-bluedevil_4%3a5.24.6-0ubuntu0.1_amd64.deb ...
Unpacking bluedevil (4:5.24.6-0ubuntu0.1) over (4:5.24.4-0ubuntu1) ...
Preparing to unpack .../1-firefox_104.0.2+build1-0ubuntu0.22.04.1~mt1_amd64.deb ...
Unpacking firefox (104.0.2+build1-0ubuntu0.22.04.1~mt1) over (104.0.1+build1-0ubuntu0.22.04.1~mt1) ...
Preparing to unpack .../2-liblayershellqtinterface5_5.24.6-0ubuntu0.1_amd64.deb ...
Unpacking liblayershellqtinterface5 (5.24.6-0ubuntu0.1) over (5.24.4-0ubuntu1) ...
Preparing to unpack .../3-layer-shell-qt_5.24.6-0ubuntu0.1_amd64.deb ...
Unpacking layer-shell-qt (5.24.6-0ubuntu0.1) over (5.24.4-0ubuntu1) ...
Preparing to unpack .../4-plasma-workspace-data_4%3a5.24.6-0ubuntu0.1_all.deb ...
Unpacking plasma-workspace-data (4:5.24.6-0ubuntu0.1) over (4:5.24.4-0ubuntu1) ...
Preparing to unpack .../5-sddm-theme-breeze_4%3a5.24.6-0ubuntu0.1_amd64.deb ...
Unpacking sddm-theme-breeze (4:5.24.6-0ubuntu0.1) over (4:5.24.4-0ubuntu1) ...
Preparing to unpack .../6-kde-config-sddm_4%3a5.24.6-0ubuntu0.1_amd64.deb ...
Unpacking kde-config-sddm (4:5.24.6-0ubuntu0.1) over (4:5.24.4-0ubuntu1) ...
Setting up kde-config-sddm (4:5.24.6-0ubuntu0.1) ...
Setting up liblayershellqtinterface5 (5.24.6-0ubuntu0.1) ...
Setting up sddm-theme-breeze (4:5.24.6-0ubuntu0.1) ...
Setting up firefox (104.0.2+build1-0ubuntu0.22.04.1~mt1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up plasma-workspace-data (4:5.24.6-0ubuntu0.1) ...
Setting up layer-shell-qt (5.24.6-0ubuntu0.1) ...
Setting up bluedevil (4:5.24.6-0ubuntu0.1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for dbus (1.12.20-2ubuntu4) ...
Processing triggers for shared-mime-info (2.1-2) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
 
The fix is at [https://itsfoss.com/following-packages-have-been-kept-back/](https://itsfoss.com/following-packages-have-been-kept-back/) . What a waste of time to be individually installing the other 55 packages. Is there a better fix for this please ?

**Edit **- It would seem "cautious solution 1 or cautious solution 2" are good solutions -  [https://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it#602](https://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it#602)

---

### Post by &amp;KyT$0P# on 2022-09-05
It's not broken, so there is no "fix".  Those are phased updates that your system has not been phased into yet.  As long as the phased rollout is not halted, you'll get them eventually.

You can safely just ignore this and leave it be.

More information [here]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345").

---

### Post by oygle on 2022-09-06
> **halogen2 said:**
> You can safely just ignore this and leave it be..

Okay, thanks.

---

