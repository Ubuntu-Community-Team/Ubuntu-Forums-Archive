---
title: "Ubuntu 12.04.3 QT4-Designer install"
date: 2013-10-22
forum: Installation &amp; Upgrades
---

### Post by vladimirse on 2013-10-22
Hello, dear!
Trying to install on Ubuntu 12.04.3 Qt4-designer. 
```

[COLOR=#000000][FONT=dejavu sans mono]sudo apt-get install qt4-dev-tools qt4-designer[/FONT][/COLOR]

```

Proposes to remove:
```

[COLOR=#000000][FONT=dejavu sans mono]libgl1-mesa-dri-lts-quantal libgl1-mesa-dri-lts-quantal:i386[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libgl1-mesa-glx-lts-quantal libgl1-mesa-glx-lts-quantal:i386[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libglapi-mesa-lts-quantal libglapi-mesa-lts-quantal:i386 libosmesa6:i386[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]libxatracker1-lts-quantal ubuntu-desktop x11-xserver-utils-lts-quantal xorg[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-common-lts-quantal xserver-xorg-core-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-input-all-lts-quantal xserver-xorg-input-evdev-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-input-mouse-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-input-synaptics-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-input-vmmouse-lts-quantal xserver-xorg-input-wacom-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-lts-quantal xserver-xorg-video-all-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-ati-lts-quantal xserver-xorg-video-cirrus-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-fbdev-lts-quantal xserver-xorg-video-intel-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-mach64-lts-quantal xserver-xorg-video-mga-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-modesetting-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-neomagic-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-nouveau-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-openchrome-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-r128-lts-quantal xserver-xorg-video-radeon-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-s3-lts-quantal xserver-xorg-video-savage-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-siliconmotion-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-sis-lts-quantal xserver-xorg-video-sisusb-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-tdfx-lts-quantal xserver-xorg-video-trident-lts-quantal[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]xserver-xorg-video-vesa-lts-quantal xserver-xorg-video-vmware-lts-quantal[/FONT][/COLOR]

```



I understand this is not normal, because touchpad no longer work and intel-vga. Please tell me how to fix?

P.S.
```

[COLOR=#000000][FONT=dejavu sans mono]cat /etc/lsb-release[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]DISTRIB_ID=Ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]DISTRIB_RELEASE=12.04[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]DISTRIB_CODENAME=precise[/FONT][/COLOR]
[COLOR=#000000][FONT=dejavu sans mono]DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"[/FONT][/COLOR]

```

---

### Post by Favux on 2013-10-22
Hi vladimirse,

Welcome to Ubuntu forums!


Ordinarily I would not respond to your post because I don't work with QT4-Designer.  However I just finished working with AussiePozzie who ran into a very similar problem trying to compile input-wacom for its wacom.ko.

For his Precise 12.04.3 it was libraries and xserver drivers ending with the -lts-raring suffix that were the issue.  This appears to be a bug in the package management of both 12.04.2 which has the Quantal 3.5 kernel and 1.12 X Server and 12.04.3 which should have the Raring 3.8 kernel and 1.13 X Server.  I believe he is planning on filing a Launchpad bug report.  See this bug report on using fglrx build-depends in 12.04.2:  [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1137247](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1137247)  I am wondering if the root cause is related to this bug report:  [https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-raring/+bug/1190148](https://bugs.launchpad.net/ubuntu/+source/linux-meta-lts-raring/+bug/1190148)

I do not know how to get back the drivers you need.  I assume they should have the lts-quantal suffix from your posted output.  If you do not see the lts-quantal suffix with apt-get I would be careful.  But I am puzzled because I would have expected lts-raring.  AussiePozzie reinstalled in order to fix his 12.04.3.

---

### Post by vladimirse on 2013-10-22
Thanks for the answer! Surf for another forum, if that does not try to find something to reinstall 12.04.3.

---

### Post by coldraven on 2013-10-23
This bug does not seem to happen using Synaptic. My details below:
```
uname -a
Linux snappy 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:19:35 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"

```

---

### Post by vladimirse on 2013-10-23
You mean do not use Apt-get?

---

### Post by coldraven on 2013-10-24
> **vladimirse said:**
> You mean do not use Apt-get?
Yes. Using Synaptic , when I added the two packges and clicked "Apply" it only showed packages to install and none to remove.

---

