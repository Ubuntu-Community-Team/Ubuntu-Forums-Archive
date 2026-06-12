---
title: "How safe is apt-get autoremove?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by Xavier Oddmon on 2009-12-07
Okay, strage things:
Last night, I installed lmms, galan, hydrogen, (and jackd, don't remember if that was manual). Played around with galan and hydrogen, didn't really understand lmms, that's for a later date. Then I turned off my laptop.

This morning, I boot my computer, only to find that instead of getting the normal log in manager, I got a terminal login prompt, which was blinking rapidly. Not the cursor, the whole screen. Kind of alarming. So, I boot to recovery mode, select dpkg, and let it run its course. Among packages to be installed were nvidia-glx-185, and **ubuntu-desktop**. (There were a good number of files, I don't remember most of them, but there were only a few I recognized. Mostly libs of various types.) Then, it told me that there were unneeded packages to be removed, but I skipped this step, since I *did* recognize many of these. 

So, ubuntu starts in low graphics mode, I manually downloaded and enabled nvidia-glx-180. Reboot, everything looks fine. Now, after logging in, and enabling my nvidia drivers, i've got the desktop I know and love. 

Here's the thing: apt-get still suggests I autoremove some packages. Here's the output:
```
chris@chris-laptop:~$ sudo apt-get -s autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libaa1-dev libasound2-dev libaudio-dev libaudiofile-dev libcaca-dev
  libdirectfb-dev libdirectfb-extra libesd0-dev libfakekey0 libfreetype6-dev
  libice-dev libjpeg62-dev libmysqlclient15off libncurses5-dev libosmesa6
  libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libslang2-dev libsm-dev
  libsysfs-dev libtidy-0.99-0 libx11-dev libxau-dev libxcb1-dev libxdmcp-dev
  libxext-dev libxt-dev mesa-common-dev python-chardet python-feedparser
  python-gtkmozembed python-utidylib x11proto-core-dev x11proto-input-dev
  x11proto-kb-dev x11proto-xext-dev xtrans-dev zlib1g-dev
0 upgraded, 0 newly installed, 39 to remove and 0 not upgraded.
Remv libaa1-dev [1.4p5-38]
Remv libasound2-dev [1.0.20-3ubuntu6]
Remv libaudio-dev [1.9.2-1]
Remv libesd0-dev [0.2.41-5]
Remv libaudiofile-dev [0.2.6-7ubuntu2]
Remv libcaca-dev [0.99.beta16-1]
Remv libdirectfb-dev [1.2.7-2ubuntu1]
Remv libdirectfb-extra [1.2.7-2ubuntu1]
Remv libfakekey0 [0.1-1]
Remv libfreetype6-dev [2.3.9-5]
Remv libxt-dev [1:1.0.5-3ubuntu1]
Remv libsm-dev [2:1.1.0-2]
Remv libice-dev [2:1.0.5-1]
Remv libjpeg62-dev [6b-14build1]
Remv libmysqlclient15off [5.1.30really5.0.83-0ubuntu3]
Remv libncurses5-dev [5.7+20090803-2ubuntu2]
Remv libosmesa6 [7.6.0-1ubuntu4]
Remv libslang2-dev [2.1.4-3]
Remv libpng12-dev [1.2.37-1]
Remv mesa-common-dev [7.6.0-1ubuntu4]
Remv libxext-dev [2:1.0.99.1-0ubuntu4]
Remv libx11-dev [2:1.2.2-1ubuntu1]
Remv libxcb1-dev [1.4-1]
Remv libpthread-stubs0-dev [0.1-2]
Remv libpthread-stubs0 [0.1-2]
Remv libsysfs-dev [2.1.0-5]
Remv python-utidylib [0.2-3.2ubuntu1]
Remv libtidy-0.99-0 [20081224cvs-1]
Remv x11proto-xext-dev [7.0.4-2]
Remv libxau-dev [1:1.0.4-2]
Remv libxdmcp-dev [1:1.0.2-3]
Remv python-chardet [1.0.1-1.1]
Remv python-feedparser [4.1-14]
Remv python-gtkmozembed [2.25.3-3ubuntu1]
Remv x11proto-core-dev [7.0.15-1]
Remv x11proto-input-dev [1.5.0-2ubuntu1]
Remv x11proto-kb-dev [1.0.3-3ubuntu1]
Remv xtrans-dev [1.2.4-1]
Remv zlib1g-dev [1:1.2.3.3.dfsg-13ubuntu3]
chris@chris-laptop:~$ 

```

Can / should I do this? Will it break anything? And if uninstalling them causes major issues, could I just re-install those packages, or would something else fail?

This sudden failure in the first place kind of takes me by surprise, as I have *absolutely no idea* what triggered it.

Oh, other (possibly) useful information:
Ubuntu 9.10 64bit
linux:2.6.31-16-generic
gnome,
compiz fusion, nvidia-glx-185

---

### Post by darkod on 2009-12-07
As far as I understand autoremove does NOT remove packages that are installed or at least not completely. What it removes is the downloaded files and with that freeing space on the hdd. It should not remove the package completely. You only do that with remove.

---

### Post by Xavier Oddmon on 2009-12-07
Thanks for the quick response! I did the autoremove, rebooted, everything is okay! Now if only I knew what happened in the first place!

---

### Post by oldos2er on 2009-12-07
From man: autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.

---

