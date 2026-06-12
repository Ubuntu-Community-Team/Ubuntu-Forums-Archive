---
title: "Installer Crash on Ubuntu 16.04 with Radeon r600"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by vittico on 2016-04-23
Hi guys.

Im trying to install the newest Ubuntu Xenial. My laptop is a HP Envy 15 with two video card and automtic switching. One is and Intel and the other one is Radeon r600. 
I cannot get to work, the system hangs when booting.

vmedina@vm-laptop:/opt/ubuntu$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M] [1002:6741]

Any idea of can I do to get it to work?

---

### Post by CalvinK on 2016-04-24
I have the same problem on an HP Pavilion with a radeon video card. At the first try, I had the screen of my desktop but not the use of Unity (nor Gnome when I tried this solution) and at the second the installer crashed . Maybe it relates to this thread 
[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
It seems we haven't the proper configuration for this release. Perhaps a good solution will appear shortly. Meanwhile I have reversed to the 14.04 LTS.

Best regards

PS : We have the confirmation in another thread on this forum and at 
[https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/](https://tjaalton.wordpress.com/2016/03/11/no-catalystfglrx-video-driver-in-ubuntu-16-04/) where it is explained that the fglrx driver is no more supported and that a team is currently working to provide an alternative.

---

