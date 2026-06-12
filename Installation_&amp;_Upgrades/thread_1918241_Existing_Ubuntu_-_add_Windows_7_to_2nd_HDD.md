---
title: "Existing Ubuntu - add Windows 7 to 2nd HDD"
date: 2012-01-31
forum: Installation &amp; Upgrades
---

### Post by VanceVEP72 on 2012-01-31
I can find COUNTLESS posts on how to install Ubuntu AFTER an existing Windows install, but not the reverse. My situation is this... I have an existing Ubuntu 11.10 install and I want to add a second HDD to my PC and install Windows 7 on it. How do I go about this so that I can boot into either OS using Grub. I don't want to have to change the boot order on my PC in BIOS everytime I want to switch OSs.

---

### Post by oldfred on 2012-01-31
Windows is a lot happier is it is sda. I would make it the first drive or sda from Ubuntu. Safest way to install would be to totally unplug the Ubuntu drive during install and then Windows will be totally seen as sda. Then plug the Ubuntu drive back into a higher port number on the motherboard.

Some have installed Windows to sdb and it installed its 100MB boot/repair partition and MBR to sda.

After Windows install, set BIOS to boot Ubuntu drive and run this to find the Windows install. Then you should be able to boot Windows from grub2's menu, but if in an emergency also be able to use BIOS to directly boot it.

---

