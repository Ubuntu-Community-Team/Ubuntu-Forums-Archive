---
title: "Dual boot with Win10, installation fails on Installation type/partition setup"
date: 2018-09-06
forum: Installation &amp; Upgrades
---

### Post by norwe on 2018-09-06
Hi,

I'm trying to installing the Ubuntu 18.04 as a dual boot on my Lenovo Ideapad 720s - Intel Core i7. I followed [this]("https://hackernoon.com/installing-ubuntu-18-04-along-with-windows-10-dual-boot-installation-for-deep-learning-f4cd91b58557") guide, created usb bootable with Rufus from ubuntu-18.04.1-desktop-amd64 iso.

I was expecting to get to this window on installation type to select Something else:

[ATTACH=CONFIG]281000[/ATTACH]


But I get the below instead, and if I press the '+' or change button or anything else, the installation freezes. Eventually the OS starts up in the "test mode".

[IMG]https://drive.google.com/file/d/1Y2gwELX89agJJEqEx0bLXf0WtTRlKlrm/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1Y2gwELX89agJJEqEx0bLXf0WtTRlKlrm/view?usp=sharing[/IMG][ATTACH=CONFIG]280999[/ATTACH]


Any suggestions on why I can't set up the partitions and complete the installation?

---

### Post by westie457 on 2018-09-06
Boot the USB, do you get a four line text menu or do you get a big picture on the screen. If the latter hit 'Esc' to get more options. In either select 'Check Disk for errors', any errors found means you will have to download a fresh .iso and recreate a fresh USB.
Once that is done Boot into try-mode to see what works and then click on the Install icon, click through to the Install screen,select the 'Something Else' option. Now do you see the partitions already on the Hard drive?

---

### Post by lordfrikk on 2018-09-06
Might be it worth to verify your ISO before you even start the installation next time, it will save time!

[https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu)

---

### Post by oldfred on 2018-09-06
Have you updated UEFI from Lenovo, and if SSD the firmware for SSD?

Can you run installer in live mode. Does it show drive?
Post this if it does:
sudo parted -l
sudo gdisk -l /dev/sda
or if NVMe drive:
sudo gdisk -l /dev/nvme0n1

Does it also have nVidia?
You need nomodeset to install & first boot or until you install nVidia driver from Ubuntu repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

