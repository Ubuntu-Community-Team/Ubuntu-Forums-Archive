---
title: "Linux Kernel Update"
date: 2017-06-29
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2017-06-29
Trying to update the Linux Kernel to 4.8.4 on Ubuntu 16.04.2.
Using 'Updater' give Linux 4.4 version
Using commands in terminal : 
sudo apt update
sudo apt full-upgrade

still only gives Linux 4.4 version.

Searching the net I found the following link but the number of commands seem excessive [https://websetnet.com/kernel-4-8-released-install-linux-kernel-4-8-ubuntu-16-04/](https://websetnet.com/kernel-4-8-released-install-linux-kernel-4-8-ubuntu-16-04/)
. Is there a better set of commands?

---

### Post by johndough2 on 2017-06-29
Hi

I use
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Impavidus on 2017-06-29
sudo apt full-upgrade (or sudo apt-get dist-upgrade, which is almost identical) will install the latest patches to your 4.4 kernel. It will not upgrade your system to the 4.8 kernel. The 4.4 kernel is fully supported, so if you have no problems with hardware support, there's probably no reason to upgrade the kernel to 4.8. If you want the 4.8 kernel, the best way to go is installing the HWE. See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by angel mike on 2017-06-29
Thanks Johndough2 and Impavidus for the speedy and informative responses - that has answered by question -will mark solved !

---

