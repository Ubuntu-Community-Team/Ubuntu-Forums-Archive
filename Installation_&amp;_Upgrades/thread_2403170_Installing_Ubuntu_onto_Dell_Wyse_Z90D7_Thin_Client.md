---
title: "Installing Ubuntu onto Dell Wyse Z90D7 Thin Client - GRUB Issues"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by webzoid on 2018-10-08
I have recently acquired a Dell Wyse Z90D7 Thin Client from eBay. 

I've upgraded the RAM from 4GB to 8GB and replaced the original SATA 16GB flash drive with a 500GB SSD, with a view to installing Ubuntu on the thing.

Having downloaded the latest Ubuntu 18.04.1 LTS release onto a USB pen drive, I can get the Thin Client to boot into the Ubuntu Live mode. This all works really well and am able to see the 500GB SSD from GPARTED as well as connect to a wireless network, etc.

However, when I then try to install Ubuntu to the system, things fall over when GRUB2 is installed with the installer first reporting that the system will not be bootable and then that the installation has crashed.

When I reboot the system, I have access to the GRUB shell and I can browse the SSD file system. I know that on (hd0,2) the Linux rootfs is present but if I attempt to boot through GRUB to the rootfs, the system hangs when booting around the USB enumeration/driver loading phase.

I appreciate that the above information is quite vague (I'm not in front of the system at the moment) but as far as I see things, what with the increase in RAM, a large SSD and a 64bit AMD processor, the installer should just work?

Can anyone offer any suggestions on how I can get up and running? For reference, I have also tried a couple of older Ubuntu installers and the end result is the same. I've also tried lubuntu but this failed.

---

### Post by kebabbert on 2018-10-08
You are not interested in using it as a thin client? Your PC could serve several thin clients. Silently. And as they run VM images, it is easy to back up the VM images.

---

### Post by webzoid on 2018-10-08
I'm more interested in using it as an extremely light-weight PC, rather than a thin client.

I only have a laptop which I don't really want to run VMs on.

Any suggestions regarding the issue I'm seeing would be greatly appreciated.

---

### Post by oldfred on 2018-10-08
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Most Dell systems have needed UEFI update (is yours UEFI or older BIOS?) and many SSD have needed firmware update.

---

### Post by webzoid on 2018-10-08
The Wyse system only has BIOS, no UEFI. 

I have read somewhere that the system may be limited to a maximum of 16GB for storage but I don't know whether this is related to the issues I am seeing.

Other sources have said that a firmware update may help. Seems odd that when running Ubuntu Live, I can fully access the SSD and there are zero issues.

---

