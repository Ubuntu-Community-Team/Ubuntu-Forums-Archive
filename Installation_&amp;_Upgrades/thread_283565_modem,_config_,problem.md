---
title: "modem, config ,problem"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by Wilky on 2006-10-24
Just installed Ubuntu 2.6.8.1-3-386 but modem not recognized.
Modem is PCTELmicromodem56 with PCT789 chipset. I downloaded file Pctel-0.9.6 and have managed to put it on the desktop.

How do I install and/or configure the modem? I have no idea from the DOCs what a kernel-source-version is or how to navigate in terminal mode. When I try, it looks like I'm in the DESKTOP file.

most commands I type are "NOT found"

Thanks to all for any help.
:(

---

### Post by helmut_hed on 2006-11-02
Hi Wilky,

You have a very old version of Ubuntu, but it should probably work anyway.  The correct driver is located here:

[http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-6.tar.gz](http://linmodems.technion.ac.il/pctel-linux/pctel-0.9.7-9-rht-6.tar.gz)

The steps to use it are:

tar xvzf pctel-0.9.7-9-rht-6.tar.gz
cd pctel-0.9.7-9-rht-6
sudo ./setup

There are a number of problems you *might* run into, depending on what this old Ubuntu contains.  You will need "kernel headers" and "gcc", among other things, which you can usually download or find on your install disk somewhere.

If you're willing to upgrade to a modern version of Ubuntu (I would suggest "Dapper") you can find detailed instructions, including how to get kernel headers and other required packages, [here]("http://ubuntuforums.org/showthread.php?t=171163").

---

