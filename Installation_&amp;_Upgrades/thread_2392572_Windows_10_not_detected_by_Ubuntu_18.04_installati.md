---
title: "Windows 10 not detected by Ubuntu 18.04 installation"
date: 2018-05-22
forum: Installation &amp; Upgrades
---

### Post by Shannon5000 on 2018-05-22
Hello - I am attempting to install Ubuntu 18.04 onto an Asus desktop that has Windows 10 installed.  I would prefer to use dual boot.  I have the space partitioned for Ubuntu and disabled the secure boot in the UEFI settings.  However, I only have the "Erase disk" option come up (picture attached) where there should be an option to install alongside Windows 10.  Any suggestions as to how I can get this machine to dual boot?

---

### Post by Autodave on 2018-05-22
Does the machine still boot to Windows if you remove the installation media?

---

### Post by ubfan1 on 2018-05-22
In what mode is Windows installed?  What partitioning is used on your disk?  What mode have you set the machine to boot (UEFI or legacy, or prefer one over the other)?  Most likely Windows is not seen because it's not installed in the same mode the installer is running.  Maybe your disk is dos partitioned, and no more partitions may be made, so no offer is made other than "wipe".  More information about your hardware is vital to any reasonable suggestions.

---

### Post by yancek on 2018-05-22
Another thing you need to check is that hibernation/fastboot are off as Ubuntu will not mount hibernated partitions and thus they will not show during the install.  The link below is the Ubuntu documentation and dual booting with windows 10 UEFI.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Shannon5000 on 2018-05-23
Thanks for the replies - what worked was setting the UEFI ROM setting to 'use current' instead of the bios option (in addition to making sure that fast boot was off).

---

### Post by amalyshev on 2018-09-14
I had a similar issue with Ubuntu Server 18.04.1 LTS. I have Windows installed on first half of 512 Samsung 970 Pro nvme. Ubuntu Server 18.04.1 LTS setup does not detect this installation. After trying a number of things, I finally installed Ubuntu 16.04.5 LTS then upgraded to 18.04.1 LTS. There seems to be a bug in 18.04.1 LTS setup, because previous version works fine.

---

### Post by adonp on 2019-06-11
Changing the "UEFI/Legacy Boot Priority" parameter to "UEFI First" through BIOS setup (Lenovo thinkpad x240) worked for me.

---

