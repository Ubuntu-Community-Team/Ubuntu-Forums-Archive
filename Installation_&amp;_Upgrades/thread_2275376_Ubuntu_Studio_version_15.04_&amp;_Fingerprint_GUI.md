---
title: "Ubuntu Studio version 15.04 &amp; Fingerprint GUI"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by neb8 on 2015-04-25
Hello,

After installing Ubuntu Studio 15.04 32-bit, my fingerprint reader  (Fingerprint GUI) won't install. The 15.04 Studio version installation  lacks certain dependencies. I tried compiling the fingerprint gui driver  for version 15.04 but the os install lacks necessary development  packages.

Ubuntu version 14.04 there were no problems with the Fingerprint GUI installation.

Is this something relative to Ubuntu version 15.04 Studio installation?

---

### Post by neb8 on 2015-04-26
Installing the Desktop packages and libraries, the Fingerprint Gui installed ok.

Studio omits some of the packages and libraries installed with the Desktop version, required to install some applications.

To add the Desktop packages and libraries to Studio, I used the command  "  sudo apt-get install ubuntu-desktop "

[https://help.ubuntu.com/community/UbuntuStudio/FAQ](https://help.ubuntu.com/community/UbuntuStudio/FAQ)

From a Desktop installation you can add Studio packages by using the command: 

 sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video

for more information: [https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu](https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu)

---

