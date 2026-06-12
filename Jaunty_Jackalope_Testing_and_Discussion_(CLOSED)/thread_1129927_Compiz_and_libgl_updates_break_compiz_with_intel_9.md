---
title: "Compiz and libgl updates break compiz with intel 965 card"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hexion on 2009-04-19
Compiz broken with last libgl and compiz updates. At least with a 965 intel card.

Reason here:
> compiz (1:0.8.2-0ubuntu-8 ) jaunty; urgency=low

  * debian/patches/028_compiz_manager_blacklist:
    - blacklist GM965 (8086:2a02) until the freeze with the intel
      driver is fixed (LP: #359392)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

**Of course if you're suffering from the bug above you might not want to reenable compiz. Otherwise follow the instructions below to reenable compiz:**



$ lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

Guilty upgrade (from /var/log/aptitude)
===============================================================================
[UPGRADE] compiz 1:0.8.2-0ubuntu7 -> 1:0.8.2-0ubuntu8
[UPGRADE] compiz-core 1:0.8.2-0ubuntu7 -> 1:0.8.2-0ubuntu8
[UPGRADE] compiz-gnome 1:0.8.2-0ubuntu7 -> 1:0.8.2-0ubuntu8
[UPGRADE] compiz-plugins 1:0.8.2-0ubuntu7 -> 1:0.8.2-0ubuntu8
[UPGRADE] compiz-wrapper 1:0.8.2-0ubuntu7 -> 1:0.8.2-0ubuntu8
[UPGRADE] libdecoration0 1:0.8.2-0ubuntu7 -> 1:0.8.2-0ubuntu8
[UPGRADE] libgl1-mesa-dri 7.4-0ubuntu2 -> 7.4-0ubuntu3
[UPGRADE] libgl1-mesa-glx 7.4-0ubuntu2 -> 7.4-0ubuntu3
[UPGRADE] libglu1-mesa 7.4-0ubuntu2 -> 7.4-0ubuntu3
[UPGRADE] mesa-utils 7.4-0ubuntu2 -> 7.4-0ubuntu3
===============================================================================




Temporary solution: downgrade to the previous version:

```
cd /var/cache/apt/archives
sudo dpkg -i *7.4-0ubuntu2*
sudo dpkg -i *0.8.2-0ubuntu7*
reboot
```P.S.: First make sure with only the compiz and libgl packages are listed by this command:

```
ls *7.4-0ubuntu2*  *0.8.2-0ubuntu7*
compiz_1%3a0.8.2-0ubuntu7_all.deb            compiz-wrapper_1%3a0.8.2-0ubuntu7_amd64.deb  libglu1-mesa_7.4-0ubuntu2_amd64.deb
compiz-core_1%3a0.8.2-0ubuntu7_amd64.deb     libdecoration0_1%3a0.8.2-0ubuntu7_amd64.deb  mesa-utils_7.4-0ubuntu2_amd64.deb
compiz-gnome_1%3a0.8.2-0ubuntu7_amd64.deb    libgl1-mesa-dri_7.4-0ubuntu2_amd64.deb
compiz-plugins_1%3a0.8.2-0ubuntu7_amd64.deb  libgl1-mesa-glx_7.4-0ubuntu2_amd64.deb
```

---

