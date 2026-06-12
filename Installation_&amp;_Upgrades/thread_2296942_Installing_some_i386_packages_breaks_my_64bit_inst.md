---
title: "Installing some i386 packages breaks my 64bit install"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by Xavier_Vachon on 2015-09-30
I'm a tester for the WINE project and I need to compile WINE from Git to run regression testing. My setup is a shared WoW64 install per the instructions in [http://wiki.winehq.org/BuildingWine?action=show&redirect=WineOn64bit](http://wiki.winehq.org/BuildingWine?action=show&redirect=WineOn64bit)

I need to install some dependencies for the 32-bit version to work. The packages below are causing problems because they force me to uninstall 64bit components. I wish them to run side-by-side

libpng-dev:i386
libjpeg-dev:i386
libgl1-mesa-dev:i386
libfreetype6-dev:i386

The terminal output shows :


```
root@xavier-pc:~# apt-get install libpng12-dev:i386 libjpeg-dev:i386 libgl1-mesa-dev:i386 libfreetype6-dev:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libasan0:i386 libatomic1:i386 libcloog-isl4:i386 libdrm-dev
  libgcc-4.8-dev:i386 libgmp10:i386 libgomp1:i386 libisl10:i386 libitm1:i386
  libmpc3:i386 libmpfr4:i386 libquadmath0:i386 libx11-xcb-dev
  libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-present-dev
  libxcb-randr0-dev libxcb-render0-dev libxcb-shape0-dev libxcb-sync-dev
  libxcb-xfixes0-dev libxdamage-dev libxext-dev libxfixes-dev libxshmfence-dev
  libxxf86vm-dev zlib1g-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6-dev:i386 libdrm-dev:i386 libjpeg-turbo8-dev:i386 libjpeg8-dev:i386
  libx11-xcb-dev:i386 libxcb-dri2-0-dev:i386 libxcb-dri3-dev:i386
  libxcb-glx0-dev:i386 libxcb-present-dev:i386 libxcb-randr0:i386
  libxcb-randr0-dev:i386 libxcb-render0-dev:i386 libxcb-shape0:i386
  libxcb-shape0-dev:i386 libxcb-sync-dev:i386 libxcb-xfixes0:i386
  libxcb-xfixes0-dev:i386 libxdamage-dev:i386 libxext-dev:i386
  libxfixes-dev:i386 libxshmfence-dev:i386 libxxf86vm-dev:i386
  linux-libc-dev:i386 mesa-common-dev:i386 zlib1g-dev:i386
Suggested packages:
  glibc-doc:i386 manpages-dev:i386 libxext-doc:i386
Recommended packages:
  gcc:i386 c-compiler:i386
The following packages will be REMOVED:
  bbswitch-dkms dkms gcc gcc-multilib libfreetype6-dev libgl1-mesa-dev
  libpng12-dev mesa-common-dev nvidia-346 nvidia-prime
The following NEW packages will be installed:
  libc6-dev:i386 libdrm-dev:i386 libfreetype6-dev:i386 libgl1-mesa-dev:i386
  libjpeg-dev:i386 libjpeg-turbo8-dev:i386 libjpeg8-dev:i386 libpng12-dev:i386
  libx11-xcb-dev:i386 libxcb-dri2-0-dev:i386 libxcb-dri3-dev:i386
  libxcb-glx0-dev:i386 libxcb-present-dev:i386 libxcb-randr0:i386
  libxcb-randr0-dev:i386 libxcb-render0-dev:i386 libxcb-shape0:i386
  libxcb-shape0-dev:i386 libxcb-sync-dev:i386 libxcb-xfixes0:i386
  libxcb-xfixes0-dev:i386 libxdamage-dev:i386 libxext-dev:i386
  libxfixes-dev:i386 libxshmfence-dev:i386 libxxf86vm-dev:i386
  linux-libc-dev:i386 mesa-common-dev:i386 zlib1g-dev:i386
0 upgraded, 29 newly installed, 10 to remove and 0 not upgraded.
Need to get 4,283 kB of archives.
After this operation, 265 MB disk space will be freed.
Do you want to continue? [Y/n]

```

I noticed that there are some longstanding bugs about similar problems

[https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/990982](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/990982)
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/949606)

What's the current status for them? Is there any active effort to solve this?

Thank you.

---

### Post by dino99 on 2015-09-30
there are still known issues not solved
[http://wiki.winehq.org/WineMultiArch](http://wiki.winehq.org/WineMultiArch)

---

### Post by Xavier_Vachon on 2015-09-30
Thank you for the information. Are there any workarounds for these? The most important library package I would need to work is [COLOR=#000000]libgl1-mesa-dev[/COLOR], as without it OpenGL and Direct3D are not supported.

---

