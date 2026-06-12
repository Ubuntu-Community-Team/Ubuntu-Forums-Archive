---
title: "Help installing printer driver :S"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by Hamslicepeanutbutter on 2010-03-25
I'm trying to install the driver for a phaser 750, I've downloaded the files, extracted them, but im not shure about the terminal code o_O some one please tell me step by step, this is as far as i've gotten:
 sudo /home/sandra/Documents/XeroxLinuxi386XpxxInstall/setup install_/xerox

it's telling me: error cant open file, Xeroxinstall/disks

---

### Post by silvermask on 2011-02-10
**Any Updates on this i am facing same problem now in my office**


:confused::confused::confused::confused::confused:

---

### Post by anglican on 2011-02-10
> **silvermask said:**
> **Any Updates on this i am facing same problem now in my office**


:confused::confused::confused::confused::confused:You should just need to download the drivers from [www.xerox.com](www.xerox.com) which should get you a file called LinuxCupsPrinterPkg.tar.gz in your Downloads folder. Extract it with ```
tar xvfz LinuxCupsPrinterPkg.tar.gz
```which will create a directory called LinuxCupsPrinterPkg in your Downloads directory. Move this somewhere suitable e.g. ```
sudo mv LinuxCupsPrinterPkg /usr/share/ppd/Xerox_Phaser
```Then install the printer choosing to browse to the appropriate ppd file - which will be called xrx750[xy].ppd where [xy] will depend on your exact model. Post back if you need more specific instructions for this.

H

---

