---
title: "Dual monitor not working after &quot;upgrade&quot;"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by sunshinelock on 2014-09-26
My duals aren't working, and the screen resolution has changed.  Silly me, thinking it was fine to click the prompt that the old drivers were unsupported.

I did this

```
[COLOR=#000000][FONT=Ubuntu Mono]tail -n25 /var/log/apt/history.log[/FONT][/COLOR]
```

And got this:

```
Start-Date: 2014-09-26  09:09:54
Commandline: aptdaemon role='role-commit-packages' sender=':1.71'
Upgrade: libnss3:amd64 (3.17-0ubuntu0.12.04.1, 3.17.1-0ubuntu0.12.04.1), thunderbird-locale-en-us:amd64 (31.1.1+build1-0ubuntu0.12.04.1, 31.1.2+build1-0ubuntu0.12.04.1), thunderbird:amd64 (31.1.1+build1-0ubuntu0.12.04.1, 31.1.2+build1-0ubuntu0.12.04.1), firefox-globalmenu:amd64 (32.0+build1-0ubuntu0.12.04.1, 32.0.3+build1-0ubuntu0.12.04.1), bash:amd64 (4.2-2ubuntu2.1, 4.2-2ubuntu2.2), firefox:amd64 (32.0+build1-0ubuntu0.12.04.1, 32.0.3+build1-0ubuntu0.12.04.1), firefox-locale-en:amd64 (32.0+build1-0ubuntu0.12.04.1, 32.0.3+build1-0ubuntu0.12.04.1), thunderbird-globalmenu:amd64 (31.1.1+build1-0ubuntu0.12.04.1, 31.1.2+build1-0ubuntu0.12.04.1), thunderbird-gnome-support:amd64 (31.1.1+build1-0ubuntu0.12.04.1, 31.1.2+build1-0ubuntu0.12.04.1), libnss3-1d:amd64 (3.17-0ubuntu0.12.04.1, 3.17.1-0ubuntu0.12.04.1), thunderbird-locale-en:amd64 (31.1.1+build1-0ubuntu0.12.04.1, 31.1.2+build1-0ubuntu0.12.04.1)
End-Date: 2014-09-26  09:11:13


Start-Date: 2014-09-26  09:12:36
Commandline: aptdaemon role='role-commit-packages' sender=':1.71'
Install: libgl1-mesa-dri-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), libgl1-mesa-dri-lts-trusty:i386 (10.1.3-0ubuntu0.1~precise1, automatic), xserver-xorg-lts-trusty:amd64 (7.7+1ubuntu8~precise1), linux-image-3.13.0-36-generic:amd64 (3.13.0-36.63~precise1), libgbm1-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), xserver-xorg-video-fbdev-lts-trusty:amd64 (0.4.4-1build1~precise1, automatic), xserver-xorg-core-lts-trusty:amd64 (1.15.1-0ubuntu2~precise2, automatic), xserver-xorg-input-vmmouse-lts-trusty:amd64 (13.0.0-1build1~precise1, automatic), libxcb-dri2-0:i386 (1.8.1-1ubuntu0.2, automatic), libegl1-mesa-drivers-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), libtinfo5:i386 (5.9-4, automatic), libwayland-ltst-client0:amd64 (1.4.0-1ubuntu1~precise1, automatic), linux-headers-3.13.0-36-generic:amd64 (3.13.0-36.63~precise1, automatic), xserver-xorg-video-neomagic-lts-trusty:amd64 (1.2.8-1build1~precise1, automatic), xserver-xorg-video-openchrome-lts-trusty:amd64 (0.3.3-1build1~precise1, automatic), xserver-xorg-video-sis-lts-trusty:amd64 (0.10.7-0ubuntu6~precise1, automatic), xserver-xorg-video-glamoregl-lts-trusty:amd64 (0.6.0-0ubuntu4~precise1, automatic), xserver-xorg-video-savage-lts-trusty:amd64 (2.3.7-2ubuntu2~precise1, automatic), libtxc-dxtn-s2tc0:amd64 (0~git20110809-2.1, automatic), xserver-xorg-video-intel-lts-trusty:amd64 (2.99.910-0ubuntu1~precise1, automatic), libglapi-mesa-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), libglapi-mesa-lts-trusty:i386 (10.1.3-0ubuntu0.1~precise1, automatic), xserver-xorg-video-siliconmotion-lts-trusty:amd64 (1.7.7-2build1~precise1, automatic), linux-generic-lts-trusty:amd64 (3.13.0.36.31), xserver-common-lts-trusty:amd64 (1.15.1-0ubuntu2~precise2, automatic), xserver-xorg-input-all-lts-trusty:amd64 (7.7+1ubuntu8~precise1, automatic), xserver-xorg-video-vmware-lts-trusty:amd64 (13.0.2-2ubuntu1~precise1, automatic), linux-headers-3.13.0-36:amd64 (3.13.0-36.63~precise1, automatic), libelf1:i386 (0.152-1ubuntu3, automatic), xserver-xorg-video-modesetting-lts-trusty:amd64 (0.8.1-1build1~precise1, automatic), xserver-xorg-video-ati-lts-trusty:amd64 (7.3.0-1ubuntu3.1~precise1, automatic), xserver-xorg-video-r128-lts-trusty:amd64 (6.9.2-1build1~precise1, automatic), xserver-xorg-video-nouveau-lts-trusty:amd64 (1.0.10-1ubuntu2~precise1, automatic), libglamor-ltst0:amd64 (0.6.0-0ubuntu4~precise1, automatic), xserver-xorg-input-mouse-lts-trusty:amd64 (1.9.0-1build1~precise1, automatic), libxrandr-ltst2:amd64 (1.4.2-1~precise1, automatic), x11-xserver-utils-lts-trusty:amd64 (7.7+2ubuntu1~precise1, automatic), xserver-xorg-input-evdev-lts-trusty:amd64 (2.8.2-1ubuntu2~precise1, automatic), xserver-xorg-video-all-lts-trusty:amd64 (7.7+1ubuntu8~precise1, automatic), libwayland-ltst-server0:amd64 (1.4.0-1ubuntu1~precise1, automatic), xserver-xorg-video-cirrus-lts-trusty:amd64 (1.5.2-1build1~precise1, automatic), xserver-xorg-input-synaptics-lts-trusty:amd64 (1.7.4-0ubuntu1~precise2, automatic), libwayland-egl1-mesa-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), libgl1-mesa-glx-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1), libgl1-mesa-glx-lts-trusty:i386 (10.1.3-0ubuntu0.1~precise1), linux-image-generic-lts-trusty:amd64 (3.13.0.36.31), xserver-xorg-video-mach64-lts-trusty:amd64 (6.9.4-1build1~precise1, automatic), libegl1-mesa-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), libudev0:i386 (175-0ubuntu9.6, automatic), libxatracker2-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), xserver-xorg-video-s3-lts-trusty:amd64 (0.6.5-0ubuntu4~precise1, automatic), xserver-xorg-video-vesa-lts-trusty:amd64 (2.3.3-1build1~precise1, automatic), libxcb-xfixes0:amd64 (1.8.1-1ubuntu0.2, automatic), linux-headers-generic-lts-trusty:amd64 (3.13.0.36.31), xserver-xorg-video-tdfx-lts-trusty:amd64 (1.4.5-1build1~precise1, automatic), xserver-xorg-video-sisusb-lts-trusty:amd64 (0.9.6-2build1~precise1, automatic), xserver-xorg-video-radeon-lts-trusty:amd64 (7.3.0-1ubuntu3.1~precise1, automatic), xserver-xorg-video-trident-lts-trusty:amd64 (1.3.6-0ubuntu5~precise1, automatic), libopenvg1-mesa-lts-trusty:amd64 (10.1.3-0ubuntu0.1~precise1, automatic), xserver-xorg-input-wacom-lts-trusty:amd64 (0.23.0-0ubuntu2~precise1, automatic), xserver-xorg-video-mga-lts-trusty:amd64 (1.6.3-1build1~precise1, automatic), libllvm3.4:amd64 (3.4-1ubuntu3~precise1, automatic), libllvm3.4:i386 (3.4-1ubuntu3~precise1, automatic)
Remove: xserver-xorg-video-mach64-lts-quantal:amd64 (6.9.3-0ubuntu1~precise2), xserver-xorg-video-trident-lts-quantal:amd64 (1.3.6-0ubuntu2~precise1), xserver-xorg-video-sis-lts-quantal:amd64 (0.10.7-0ubuntu1~precise2), x11-xserver-utils-lts-quantal:amd64 (7.7~3ubuntu1~precise1), xserver-common-lts-quantal:amd64 (1.13.0-0ubuntu6.5~precise1), xserver-xorg-video-modesetting-lts-quantal:amd64 (0.5.0-0ubuntu1~precise2), xserver-xorg-input-synaptics-lts-quantal:amd64 (1.6.2-1ubuntu5~precise1), xserver-xorg-input-evdev-lts-quantal:amd64 (2.7.3-0ubuntu2~precise1), nvidia-304-updates:amd64 (304.116-0ubuntu0.0.1), xserver-xorg-video-ati-lts-quantal:amd64 (6.99.99~git20120913.8637f772-0ubuntu1~precise2), libxatracker1-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), libgl1-mesa-glx-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), libgl1-mesa-glx-lts-quantal:i386 (9.0.3-0ubuntu0.4~precise1), xserver-xorg-input-vmmouse-lts-quantal:amd64 (12.9.0-0ubuntu3~precise1), xserver-xorg-video-s3-lts-quantal:amd64 (0.6.5-0ubuntu1~precise1), nvidia-current-updates:amd64 (304.116-0ubuntu0.0.1), xserver-xorg-video-vesa-lts-quantal:amd64 (2.3.2-0ubuntu1~precise1), xserver-xorg-video-tdfx-lts-quantal:amd64 (1.4.5-0ubuntu1~precise2), xserver-xorg-video-fbdev-lts-quantal:amd64 (0.4.3-0ubuntu1~precise1), xserver-xorg-video-nouveau-lts-quantal:amd64 (1.0.2-0ubuntu3~precise2), libglapi-mesa-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), libglapi-mesa-lts-quantal:i386 (9.0.3-0ubuntu0.4~precise1), xserver-xorg-video-mga-lts-quantal:amd64 (1.6.2-0ubuntu1~precise2), xserver-xorg-video-sisusb-lts-quantal:amd64 (0.9.6-0ubuntu1~precise1), xserver-xorg-video-vmware-lts-quantal:amd64 (12.0.2+git.e5ac80d8-0ubuntu1~precise2), xserver-xorg-video-neomagic-lts-quantal:amd64 (1.2.7-0ubuntu1~precise1), xserver-xorg-video-radeon-lts-quantal:amd64 (6.99.99~git20120913.8637f772-0ubuntu1~precise2), xserver-xorg-video-openchrome-lts-quantal:amd64 (0.3.1-0ubuntu1~precise3), xserver-xorg-video-cirrus-lts-quantal:amd64 (1.5.1-0ubuntu2~precise1), xserver-xorg-input-wacom-lts-quantal:amd64 (0.17.0-0ubuntu2~precise1), xserver-xorg-input-mouse-lts-quantal:amd64 (1.7.2-2build1~precise1), xserver-xorg-input-all-lts-quantal:amd64 (7.7+1ubuntu4~precise1), xserver-xorg-video-intel-lts-quantal:amd64 (2.20.9-0ubuntu2.3~precise1), xserver-xorg-video-savage-lts-quantal:amd64 (2.3.6-0ubuntu1~precise1), xserver-xorg-video-all-lts-quantal:amd64 (7.7+1ubuntu4~precise1), libgl1-mesa-dri-lts-quantal:amd64 (9.0.3-0ubuntu0.4~precise1), libgl1-mesa-dri-lts-quantal:i386 (9.0.3-0ubuntu0.4~precise1), xserver-xorg-video-siliconmotion-lts-quantal:amd64 (1.7.7-0ubuntu1~precise1), xserver-xorg-lts-quantal:amd64 (7.7+1ubuntu4~precise1), xserver-xorg-core-lts-quantal:amd64 (1.13.0-0ubuntu6.5~precise1), xserver-xorg-video-r128-lts-quantal:amd64 (6.9.1-0ubuntu1~precise2)
End-Date: 2014-09-26  09:32:05

```

I'm sure it's from something that happened in the 2nd "paragraph" of text.

Help please.

---

### Post by sunshinelock on 2014-09-26
Hold on.... going to "System Settings" "Additional Drivers".  It found a NVIDEA driver that it's installing right now.  I'll update with results.

---

### Post by sunshinelock on 2014-09-26
Fixed. Sorry to raise alarm.

---

