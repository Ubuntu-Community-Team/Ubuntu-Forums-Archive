---
title: "updating grub-pc overwrites MBR"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by astron on 2009-11-14
Hello,

A few weeks ago I installed the Ubuntu 9.10RC and during the installation process, I choosed to install GRUB2 in the MBR. Now I have changed my mind. I have other linux/BSD systems on that machine and I want another OS bootloader to perform the chainloading of my Ubuntu.
Thus I ran grub-install /dev/sda3 to install to the boot sector of my partition and overwrote the MBR with the bootloader of the other OS.
That worked fine...
But of course when grub-pc package gets updated, it overwrites the MBR.
Now I have searched where the information on the grub install is stored and the only place I have found is the debconf database.
Running dpkg-reconfigure grub-pc, I only get one choice for the installation : /dev/sda , the MBR. So I tried to manually edit the debconf database in /var/cache/apt/config.dat changing the value of the key grub-pc/install_devices to /dev/sda3 but when I update the grub-pc package via apt the value is reset to /dev/sda and the MBR is overwritten.

Anyone know how to make this config persistent?
thanks a lot.

---

### Post by astron on 2009-11-16
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

