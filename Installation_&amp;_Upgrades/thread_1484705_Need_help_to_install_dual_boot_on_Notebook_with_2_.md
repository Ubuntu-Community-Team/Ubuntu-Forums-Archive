---
title: "Need help to install dual boot on Notebook with 2 internal HDs"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by bemmy on 2010-05-16
Hi,
This is my first try on Linux platform. I would like to get some help on installing Ubuntu 10.04 on my notebook. Currently, I am using IBM Thinkpad X31 with docking that has swappable 2nd HD. The 1st internal HD has WIN XP on it. I had successfully installed Ubuntu 10.04 on the 2nd HD and everything work properly with GRUB menu asking which OS to boot when start the computer. However, when I have to swap 2nd HD out with DVD-Drive or undock, it won't allow me to boot into Windows XP -> showing device is not found and prompt to "Grub Rescue" command. It will only boot if I retain 2nd HD in the dock. So I will like to know how to make Window XP boot without 2nd HD, and still able to get in Ubuntu when I insert 2nd HD into the dock? Is it possible? 

Thank you for all your assistance.

---

### Post by rjcroy on 2010-05-16
Yes, I think it is possible. I don't know enough to give precise help. But I think the answer will be to do with how the OS locations are specified in the Grub config file. I hink they can be specified in two ways (similar to the filesystem table /etc/fstab):

1) by device, e.g. /dev/sda1, or
2) by UUID, which is a unique ID for a piece of hardware.

The problem could be that grub cannot find the UUID of the HDD you have removed.

Can you post your /boot/grub/grub.cfg?

---

### Post by wilee-nilee on 2010-05-16
This might help, just remember that you never put the grub bootlader in windows, and generally only in the mbr of the hd you install to.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by bemmy on 2010-05-16
Thank you. Problem Solved. I just install GRUB on 2nd HD and it works fine now.

---

