---
title: "Can't install ubuntu 9.1 but 8.04 installs just fine"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by jediamir on 2010-02-01
Hello everyone,
I am running into difficulties trying to install the newest version of Ubuntu 32 bit.  After choosing 'Install Ubuntu' it takes me to a black screen with the cursor blinking and after a while the notebook goes into a "sleep" mode.  This only happens when I try to install kubuntu or ubuntu 9.1.  I figured it would be the video support so I chose the lowest resolutions such as vga=771 or vga=769 but it still did not work.  However, I am able to go through the complete installation of 8.04.  Any suggestions?  I would love to slap a copy of kubuntu 9.1 on my ancient laptop but I haven't had any luck.  By the way, it is a pentium 4 1.7GHz with 512 MB of ram, the model number is dell Inspiron 2650 if it helps any.  Thank you in advance!!

---

### Post by kansasnoob on 2010-02-01
I've been using Ubuntu since 7.10, and 9.10 (aka: Karmic) was never stable on my machine.

IMHO if you can run 8.04 (aka: Hardy) with no problems just do so and wait for the upgrade to Lucid in April. I'm testing Lucid right now and it looks very promising :D

---

### Post by kellemes on 2010-02-02
Had the same issue with Karmic on my machine, at least with the Live-installer.. Never could finish for some reason.
I chose the [Alternate-installer]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") and that works fine.
Hope it works for you also..

---

### Post by Mark Phelps on 2010-02-02
Be aware that Ubuntu versions newer than 8.10 do not support restricted ATI drivers with the "legacy" cards anymore.  So, if you have an ATI video chipset, and it's not one of the newer HD 3x/4x/5x series, you will be relegated to the open source drivers in Ubuntu versions newer than 8.10.

---

### Post by afrodeity on 2010-02-17
The secret is to turn off acpi. You will need to add acpi=off to the grub config as shown in this thread [http://ubuntuforums.org/showthread.php?t=1348427](http://ubuntuforums.org/showthread.php?t=1348427)

My Dell Inspiron 2650 worked just fine with Karmic. I also got Compiz running. The onboard Nvidia card works. All my keys work which didn't with Hardy. The only downside is hibernate mode isn't available unless acpi is on. So one can only hope somebody will add support for acpi via ppa in future.

Oh and before I forget, you need to turn off simulmode in the bios to avoid half screen going black with seperate instance of x.

Ubuntu Magic.

---

