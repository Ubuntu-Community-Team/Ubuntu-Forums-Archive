---
title: "Hard drive during install is sdc, but becomes sda on reboot"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by barukba on 2006-10-28
I have a Shuttle XPC SB86i (product link: [http://global.shuttle.com/Product/Barebone/SB86i.asp]("http://global.shuttle.com/Product/Barebone/SB86i.asp")). This unit comes with built-in SD and CF card readers.

During the Edgy Alternate installation, the card readers are /dev/sda and /dev/sdb and my only hard drive (SATA) becomes /dev/sdc. I made an ext3 parition for root, lib, bin, etc, sbin, and I made an LVM volume group for ext3 partitions for tmp, home, var, and usr.

On reboot, however, the hard drive became /dev/sda. Nothing would start. I  started the machine with the Desktop CD, mounted the /dev/sda2 (my root partition), changed any instance of "sdc" with "sda" /etc/fstab, and grub's menu.lst.

Everything worked beautifully until I started playing with my Plextor ConvertX PVR. I didn't know what I was doing and I think I caused the Kernel to panic. A bunch of hex codes appeared and things were generally unresponsive.

When I rebooted, only the root partition was there and the entries for my LVM partitions disappeared from /dev/mapper. I've been playing with different things, but I couldn't get them back. I don't think I altered the LVM backups to reflect the change from sdc to sda.

The lvm paritions are still there. vgscan, vgck, etc display all the details about them. 

I would like to re-install, but I want to tell the Kernel to treat the hard drive as sda or ignore the CF/SD card readers during installation (leaving sda the first available name for the drive.) Are there any special boot parameters I can pass to the Kernel during the Installation?

Thanks,

B

---

