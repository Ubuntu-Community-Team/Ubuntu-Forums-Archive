---
title: "Installation trouble"
date: 2018-04-27
forum: Installation &amp; Upgrades
---

### Post by miistermajor on 2018-04-27
Hey guys,
I installed Ubuntu this evening with a USB drive. I used the last version (18.04 LTS) but at the end of the installation when the computer needs to be rebooted to complete the installation, it crashes and after several minutes I get these errors:
[https://www.zupimages.net/up/18/17/ivl9.jpg](https://www.zupimages.net/up/18/17/ivl9.jpg)

I tried to clean my drives and to install ubuntu a second time and same problem...
I own this computer: 
[https://www.ldlc.be/fiche/PB00213591.html](https://www.ldlc.be/fiche/PB00213591.html)

Someone have an idea to help me ?
Thanks :)

---

### Post by oldfred on 2018-04-27
Does computer have nVidia?
If so you may need nomodeset boot parameter.
If installed in UEFI boot mode, you can press escape between UEFI screen & grub loading. If UEFI fast boot is on, you may not have time to press any key and have to cold boot not warm reboot.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some similar model Asus also needed another boot parameter, not sure about yours.

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

