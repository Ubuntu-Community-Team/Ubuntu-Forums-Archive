---
title: "Boot alert"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by oxman on 2008-06-23
I am dual booting Dapper and Hardy.

I can boot Hardy

When I seek to boot Dapper I get:

Mounting Root File System
Waiting for Root File System

ALERT! /dev/disk/by-uuid/<number string>/ does not exist. 

I am using an amd 64 but the Hardy kernel is generic and the Dapper kernel is 64 bit. 

I have looked at the menu list in both distros and the uuid number designated for Dapper is the same in both of them. 

Any help is appreciated.

---

### Post by sisco311 on 2008-06-23
The uuid in menu.lst must be the uuid of your "/" (root) partition (not the uuid of the /boot partition).

To get the uuid of the partitions type:
```
sudo blkid
```in a terminal

Also check the uuid in the /etc/fstab and the uuid of the swap partition in /etc/initramfs-tools/conf.d/resume .

---

### Post by oxman on 2008-06-23
That was exactly the problem sir. I am very grateful to you for your kind assistance. May you receive many in return. 

I wasn't sure what to do but took a shot in the dark. My Hardy partition had a specific uuid string for the entire sata drive. It has 4 kernel versions on it and lists the safe mode also. I simply cp the number onto every requested uuid under the assumption that all of them were in the same directory. 

Joy!

Thanks again.

---

