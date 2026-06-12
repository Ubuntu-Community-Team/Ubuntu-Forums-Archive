---
title: "Cannot get Lucid running! Help needed..."
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by lordfkiller on 2010-07-19
Tonight I installed Lucid(10.04) on my laptop, which is a VAIO VPCCW.
The first problem I faced was the blank screen when trying to install Ubuntu. That was solved by pressing F6 and activating "nomodeset"
Afterwards, I had to edit Grub, removing splash and quiet and adding nomodeset, to get it running.

Because of the low resolution and lack of support for effects, I intalled the proprietary driver for nvidia and restarted.
Now I'm getting a message saying the display cannot be found etc and it is running is low graphics mode. When trying to open nvidia-settings, I get "You do not appear to be using nvidia X driver. Please edit your X configuration file(just run nvidia-xconfig as root) ... "
And obviously, running nvidia-xconfig as root didn't change anything.

Any idea what's going on? I was forced to move to Windows a month ago as a result of this issue(bought a new laptop) and now I see the problem is not resolved yet. Please help!

Btw, OS: 10.04 64bit  Graphics Card: NVIDIA

---

### Post by dino99 on 2010-07-19
remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf

into synaptic repo tab, add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then update, upgrade and reboot

related thread: [http://ubuntuforums.org/showthread.php?t=1445212](http://ubuntuforums.org/showthread.php?t=1445212)  [http://ubuntuforums.org/showthread.php?t=1501227](http://ubuntuforums.org/showthread.php?t=1501227)

---

### Post by lordfkiller on 2010-07-20
That changed nothing. I got a low resolution screen after restart, with the same error in nvidia-settings. Running nvidia-xonfig, it's running low graphics mode again.

---

### Post by whych on 2010-07-20
I'm not the ubuntu expert, but you need to install the nvidia driver. From memory, synaptics normally pops upo a message that there are proprietory drivers available and installs them.
Look in the package management settings and enable the non-free repos.

---

### Post by lordfkiller on 2010-07-20
Please read the question again:

> **lordfkiller said:**
> ...Because of the low resolution and lack of support for effects, I intalled the proprietary driver for nvidia and restarted....

---

