---
title: "install ubuntu with amd radeon HD 6480G"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by tuguix on 2012-04-22
Hi all, im trying to install ubuntu 64bits on the machine below but i always get a blank screen on it i have tried to boot with nomodeset and xforcevesa but no joy does anyone got the same problem??? :(
 
Thanks to all in advance.
 
 
 
LAPTOP:
Toshiba Satellite L755D - 128
Processador : AMD A4-3300M APU with graphics Radeon HD 1.90GHz
Graphics: AMD RADEON HD 6480 G
Ram: 6Gb
HDD: 350Gb

---

### Post by marinara on 2012-04-22
have you tried an old ubuntu like 10.04?

---

### Post by MonkeyPaw on 2012-04-22
It sounds like it's your A4 CPU. Can you hook your laptop up to an HDMI display? If so, you will likely get through install. From there, you can install the AMD proprietary drivers, and you should be all set to run on the notebook panel.

---

### Post by tuguix on 2012-04-23
yes the old versions work, funny seems that on fedora 16 will install, cant understand why cant distros use generic drivers for installations and them give people choice to install whatever they want.:mad::(

---

### Post by MonkeyPaw on 2012-04-23
As far as I know, the distro ISOs only use open source drivers, which are "generic" of sorts. The issue for you is that your hardware is still relatively new for those open source drivers to properly set up. I'm sure in time it won't be an issue.

---

### Post by tuguix on 2012-04-24
Well you need to check that as far as know gnome 3 (shell) dont work with generic drivers, distros load ATI/AMD FGLRX drivers and my issue i found out is a bug on KERNEL 3.0. Still think normal vesa drivers would be better for installing distros now i know why people run from linux, in my point of view a newbie wants everythings to work out of the box and not spend hours on google and my best friend command line.:(:shock::evil:

---

