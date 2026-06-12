---
title: "ubuntu 11.10 install on a Dell 420 with a sata drive"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2011-12-26
I have an old Dell Precision 420 that is currently running Fedora 6 on a 300M IDE disk. I want to install Ubuntu but keep the old fedora. So I installed a Seagate SATA disk (2T) and a PCI sata adapter made by "CMD Technologies" that uses the Silicon Image chip set (3114). The problem is that when I insert the installation CD it runs for a few minutes and gets stuck. By pressing the ESC key I was able to verify the integrity of the CD and also saw a quick message related to the non-availability of /dev/sdb and another device (/dev/sdc?). So apparently the PCI adapter (with the BIOS updated) does not "show" the HD to the installer. In the past I was able to do this with a Promise card, but I understand that it uses a different chip set than the SI.

My question is if anybody had any success in installing Ubuntu in a machine using these type of SATA adapters.

Thanks.

Daniel

---

