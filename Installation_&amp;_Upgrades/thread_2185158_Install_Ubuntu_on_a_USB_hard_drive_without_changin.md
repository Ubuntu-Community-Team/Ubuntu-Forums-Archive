---
title: "Install Ubuntu on a USB hard drive without changing the MBR"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by aadpors on 2013-11-01
I have downloaded an ISO file containing the installation disk for Ubuntu 12.04. I burnt this onto a disk and am hoping to be able to boot from it. Now what I want is kind of a plug-and-play system. I want to install Ubuntu on an external USB HDD, such that my computer automatically boots Ubuntu when the USB drive is connected during PC startup. To me it is no problem if I get a GRUB-like screen to pick my OS, but I want to see that only when my USB drive is connected. Is this possible, and if so, how?

---

### Post by Dennis N on 2013-11-01
The bios setting determines the order for boot devices. Set USB device first in the order. Then if bios sees a bootable USB device on startup, it would boot from that. If none is present, it would try the next device. Seems that should work.

(In ancient times, when computers had floppy disk drives, the computer always checked for a bootable floppy before booting the hard disk.)

---

### Post by Dennis N on 2013-11-01
Just be sure when installing on the USB, the GRUB bootloader is installed to the USB's MBR, not the hard disk!

---

### Post by oldfred on 2013-11-01
And the only way you get a choice on where to install the grub2 boot loader is with Something else or manual install. All the auto installs, install grub to sda which in most systems will be the internal drive. That can be fixed, but better to install it correctly.

       Install to external drive. Also any second drive.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)


 Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

You can partition in advance or partition during install. But you have to click on the change button and chose to create or use partition, what format (ext4), and mount point ( / ) for root. You need swap also but it is not formatted, and /home or data partitions. If sharing with Windows you may want a NTFS data partition and can leave room for that to format and mount later.
And on the bottom of that screen is a combo box on where to install grub2's boot loader. Choose the drive that is the external. My example still shows sda.

---

