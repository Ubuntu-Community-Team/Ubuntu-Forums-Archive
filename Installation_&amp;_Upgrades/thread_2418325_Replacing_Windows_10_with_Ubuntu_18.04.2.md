---
title: "Replacing Windows 10 with Ubuntu 18.04.2"
date: 2019-05-05
forum: Installation &amp; Upgrades
---

### Post by kpapakon on 2019-05-05
Hi, i'm a total beginner in the Linux world and installations in general. I have a brand new Asus laptop that came with preinstalled Win 10. I tried for a few days to have Ubuntu by its side with a dual boot. However during the installation of Ubuntu, at various times, the screen would freeze. I eventually realized that this was an Nvidia problem. I managed to follow this [solution]("https://askubuntu.com/questions/1034469/dual-boot-windows-10-and-ubuntu-freezing-after-installation") to continue with the installation. When I was asked whether to erase the disk or not, I went forward with erasing, as the 'something else' option was too technical for me. The installation went ahead and lasted quite some time. Then I was asked to reboot the machine. After I did I got what you see in the pictures. This is ongoing for a couple of hours now. Any suggestions? Shall I just wait or attempt a new installation?

---

### Post by oldfred on 2019-05-05
You may need to update UEFI from Asus and if SSD update firmware for SSD. Often easier from Windows for many Windows systems. A few now are starting to support update from Linux.

Until you install nVidia driver you still need nomodeset boot parameter.
But if you only have Ubuntu and are not dual booting grub will not normally show as you only have one system to boot. 
If UEFI (which is what you should have installed), you have to press escape between UEFI/vendor logo & before grub (normally) loads. May have to press several times.
If BIOS install (UEFI emulates the 35 year old BIOS type boot), you have to press and hold the shift key from UEFI/BIOS until grub menu appears.

Many Asus also need pci=nomsi in addition to nomodeset if nVidia card/chip.

You did backup Windows before install, just in case? Or if later you want to sell system and buyer wants Windows. Or if you find one program or game that only runs in Windows?

Issues are often common across various models by brand. Bigger differences if AMD or Intel based.
Asus x541ua Update of UEFI & SSD firmware solved issues
[https://ubuntuforums.org/showthread.php?t=2414431](https://ubuntuforums.org/showthread.php?t=2414431)
How to install Ubuntu on ASUS F556U, JournalError error?  add pci=nomsi 
[https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221](https://askubuntu.com/questions/1079540/how-to-install-ubuntu-on-asus-f556u-journalerror-error/1081221#1081221)

---

