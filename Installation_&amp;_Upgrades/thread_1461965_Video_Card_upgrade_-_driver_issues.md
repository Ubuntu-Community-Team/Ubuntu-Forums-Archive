---
title: "Video Card upgrade - driver issues"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by taurolyon on 2010-04-24
I recently upgraded my ATI HD4670 to an HD5870. I then attempted to reinstall my ATI fglrx drivers to accommodate for my new device. 

Every time I try to activate the driver using the Hardware Drivers GUI - I get "SystemError: installArchives() failed"

I checked Synapic and it informed me I had a broken package: **flgrx-amdcccle**

Attempting to reinstall this package: **E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb: subprocess new pre-installation script returned error exit status 1**

```

(Reading database ... 189870 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu3_amd64.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-amdcccle

```

I think something in my old driver installation is causing issues here. Any ideas?

---

### Post by sissn on 2010-05-03
You should check this out.

[http://swiss.ubuntuforums.org/showthread.php?t=1450040&page=3](http://swiss.ubuntuforums.org/showthread.php?t=1450040&page=3)

Good luck!

---

### Post by Foxbat250 on 2010-05-18
Hi, 

You just need to install the driver form the ATI website, it works also!!

Good luck

---

### Post by lfis492a on 2010-06-08
Hello all,

Hope someone can help me out.  I read in this thread that the drivers from the manufacture works good. I went to nvidia and downloaded the linux drivers and... I'm new to linux/ubuntu and don't know how to run the installation. when i click the file it asks for a program to run it. I believe i have to go to a prompt of some sort and punch in a code to tell linux to install the file i downloaded??? I'm very new to this, I Love it, but need to master it before i start pushing linux to everyone. (I already do though! lol)  

any help would be appreciated as the screen resolution to this gateway LE500 monitor is only giving me 800x600. linux can't I'd the monitor. i guess i need this emachine's video card  updated??? (NVIDIA GEFORCE 6100) 

Thanks

---

### Post by Chaster on 2010-06-12
I followed this and it worked for me: [https://lists.launchpad.net/ubuntu-x-swat/msg74710.html](https://lists.launchpad.net/ubuntu-x-swat/msg74710.html)

just delete the usr/share/ati folder and rerun apt-get

---

### Post by lfis492a on 2010-06-22
I don't have an ATI folder. any other suggestions????

---

### Post by lfis492a on 2010-07-01
I finally got it. i think an update did it. i then was able to go to the ADMIN then HARDWARE DRIVERS and it finally accepted the videocard drivers that were available. Thanks for your help!!!!

---

