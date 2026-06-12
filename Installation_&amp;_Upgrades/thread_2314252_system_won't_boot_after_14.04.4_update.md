---
title: "system won't boot after 14.04.4 update"
date: 2016-02-19
forum: Installation &amp; Upgrades
---

### Post by joeedit on 2016-02-19
Hello,

I've just installed update for Trusty by > [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

After reboot the system can fully bootup only in recovery mode...

Can you help me to fix it or to revert changes? 

Can I just remove the installed packages by:

> sudo apt-get -r [COLOR=#333333][FONT=monospace]linux-generic-lts-wily xserver-xorg-core-lts-wily xserver-xorg-lts-wily xserver-xorg-video-all-lts-wily xserver-xorg-input-all-lts-wily libwayland-egl1-mesa-lts-wily libgl1-mesa-glx-lts-wily libgl1-mesa-glx-lts-wily:i386 libglapi-mesa-lts-wily:i386[/FONT][/COLOR]

Thanks in advance!

---

### Post by joeedit on 2016-02-19
solved - I've changed display manager using:

sudo dpkg-reconfigure lightdmnow the system boots up

---

