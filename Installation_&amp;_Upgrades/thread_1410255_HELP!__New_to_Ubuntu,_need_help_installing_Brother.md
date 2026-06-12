---
title: "HELP!  New to Ubuntu, need help installing Brother Printer driver"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by longocondo on 2010-02-18
I do not know much about Ubintu...My bro put it on my computer.  I'm trying to connect a new Brother MFC-7340 to the computer but cannot get the drivers to install, as I do not understand how to even check the version of Ubuntu that I have.  Please can someone help me?  Thanks!

---

### Post by plucky on 2010-02-19
> **longocondo said:**
> I do not know much about Ubintu...My bro put it on my computer.  I'm trying to connect a new Brother MFC-7340 to the computer but cannot get the drivers to install, as I do not understand how to even check the version of Ubuntu that I have.  Please can someone help me?  Thanks!

From a terminal ```
sudo lsb_release -a
``` should tell you what release you are using.

Go [here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7340) to find the deb driver packages for your printer and the installation instructions.Install both the cupswrapper and lpr drivers.


Good Luck

---

