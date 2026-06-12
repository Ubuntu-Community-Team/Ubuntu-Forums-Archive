---
title: "drivers/flickering"
date: 2021-08-13
forum: Installation &amp; Upgrades
---

### Post by beefleaf on 2021-08-13
Hi guys, Ive been use apt update/upgrade as usually and everything was perfecly fine until last few days. So I got messege that there is new update and I click to install, after that my display started flickering abnormal. I had to use Time Shift to rollback system to stop that. Im pretty new to linux and i dont know in deep trubleshooting. Could someone let me know please what to do as I cant use apt-get upgrade cos it will install again those drivers and couse again flickering. Thank you 

```
alsa-ucm-conf/focal-updates,focal-updates 1.2.2-1ubuntu0.9 all [upgradable from: 1.2.2-1ubuntu0.8]
firefox-locale-en/focal-updates,focal-security 91.0+build2-0ubuntu0.20.04.1 amd64 [upgradable from: 90.0.2+build1-0ubuntu0.20.04.1]
firefox/focal-updates,focal-security 91.0+build2-0ubuntu0.20.04.1 amd64 [upgradable from: 90.0.2+build1-0ubuntu0.20.04.1]
fwupd-signed/focal-updates 1.27.1ubuntu5+1.5.11-0ubuntu1~20.04.2 amd64 [upgradable from: 1.27.1ubuntu2+1.3.11-1~focal1]
fwupd/focal-updates 1.5.11-0ubuntu1~20.04.2 amd64 [upgradable from: 1.3.11-1~focal1]
gnome-maps/focal-updates 3.36.1-1ubuntu1 amd64 [upgradable from: 3.36.1-1]
libegl-mesa0/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libfwupd2/focal-updates 1.5.11-0ubuntu1~20.04.2 amd64 [upgradable from: 1.3.11-1~focal1]
libfwupdplugin1/focal-updates 1.5.11-0ubuntu1~20.04.2 amd64 [upgradable from: 1.3.11-1~focal1]
libgbm1/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libgl1-mesa-dri/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libgl1-mesa-dri/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libglapi-mesa/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libglapi-mesa/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libglx-mesa0/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libglx-mesa0/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libosmesa6/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libosmesa6/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
libxatracker2/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
linux-generic-hwe-20.04/focal-updates,focal-security 5.11.0.25.27~20.04.10 amd64 [upgradable from: 5.8.0.63.71~20.04.45]
linux-headers-generic-hwe-20.04/focal-updates,focal-security 5.11.0.25.27~20.04.10 amd64 [upgradable from: 5.8.0.63.71~20.04.45]
linux-image-generic-hwe-20.04/focal-updates,focal-security 5.11.0.25.27~20.04.10 amd64 [upgradable from: 5.8.0.63.71~20.04.45]
linux-libc-dev/focal-updates 5.4.0-81.91 amd64 [upgradable from: 5.4.0-80.90]
mesa-va-drivers/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
mesa-va-drivers/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
mesa-vdpau-drivers/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
mesa-vdpau-drivers/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
mesa-vulkan-drivers/focal-updates 21.0.3-0ubuntu0.2~20.04.1 amd64 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
mesa-vulkan-drivers/focal-updates 21.0.3-0ubuntu0.2~20.04.1 i386 [upgradable from: 20.2.6-0ubuntu0.20.04.1]
python3-distupgrade/focal-updates,focal-updates 1:20.04.36 all [upgradable from: 1:20.04.35]
ubuntu-release-upgrader-core/focal-updates,focal-updates 1:20.04.36 all [upgradable from: 1:20.04.35]
ubuntu-release-upgrader-gtk/focal-updates,focal-updates 1:20.04.36 all [upgradable from: 1:20.04.35]
```

---

### Post by mikewhatever on 2021-08-13
Have you checked if this flickering is a known problem with your hardware? I'd search for something like "ubuntu flicker you-graphics".

---

### Post by MAFoElffen on 2021-08-14
What the last poster was referring to: 
[Forum > The Ubuntu Forum Community > Ubuntu Official Flavours Support > Installation & Upgrades > [COLOR=#980101]**[ubuntu]**[/COLOR] drivers/flickering]("https://ubuntuforums.org/showthread.php?t=2465569&highlight=flickering")


If that is what is happening to you: Go near the last post, where the Original Poster notes a link to where the bug report is at Launchpad and add yourself as that it affects you also...

---

