---
title: "System Stuck when trying to work with NMNe disk"
date: 2018-12-04
forum: Installation &amp; Upgrades
---

### Post by konorws on 2018-12-04
I encountered the following problem.


I have a laptop Acer Nitro5 AN515-31
CP: Inter core i5 8th
Graphic: Nvidia MX150
HDD: TOSHIBA 1TB.

I installed SSD M.2 PCIe Express on 250 GB.
I will say right away that Windows works fine on it without a single problem.

The problem appears when you start recording and mount the disk.  The system gets stuck and just pressing the Power button helps restart. The same situation when installing ubuntu to disk. Ubuntu displays the disk and its partitions. But when you start the installation it gets stuck on "Detection file system".
 [IMG]http://dl3.joxi.net/drive/2018/12/04/0026/0440/1753528/28/23afb10019.jpg[/IMG]

I tried to use different settings UEFI/Legacy, GPT/MBR, EXT3/EXT4. Default image and DD image. But the result is the same. 16.04/18.04

 Once I managed to install ubuntu on this disk and it worked fine with the disk. (used DD image and Boot UEFI)

---

### Post by QIII on 2018-12-04
Have you been mounting this device while running Windows?

---

### Post by konorws on 2018-12-05
I do not think I understood your question correctly. 
Installing the device beeline with power off.
But Windows works with this device correctly. And Debian also works without problems.

---

