---
title: "No Devices Detected during installation of Ubuntu 8.04"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by pharaohxander on 2008-09-17
I just successfully installed ubuntu 8.04 onto my computer, and a friend asked me to install it onto his computer as well. So I shut down my system, disconnected my hard disk and connected his to perform the install, but the install hangs up on the partitioner, with no devices detected in gparted in live cd. The only difference is the hard disk swap. Both hdd's are western digital IDE, but mine (the one that worked) is a bit newer and 160GB, while the troublesome hdd is only 40GB. All other hardware and the install CD were the same. what gives? also, i booted into the installation on the working drive with both hdd attached, and gparted recognizes the drive there. the problem drive worked fine with the XP install that was on it prior to being formatted to ext3.

---

### Post by kspncr on 2008-09-17
The only things I can think of are:

What is the jumper block configuration on the 40GB drive? Is it set to master when you try to install on it?

---

