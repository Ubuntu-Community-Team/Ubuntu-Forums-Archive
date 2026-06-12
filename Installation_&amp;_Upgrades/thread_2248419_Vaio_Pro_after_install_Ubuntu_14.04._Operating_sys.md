---
title: "Vaio Pro after install Ubuntu 14.04. Operating system not found"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by marekf on 2014-10-14
Hi,

I reinstalled my Vaio Pro from windows 8.1 to Ubuntu 14.04. (Live version works perfect).
I removed all partitions and ubuntu installation create it again.
After final reboot I see message: Operating system not found.

I tried to switch boot from UEFI to Legacy and disable Secure boot. It didn't work.

Then I tried to install boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but there was a problem with 14.04.

So I installed ubuntu 13.10 (I tried it with LVM) and run successfully boot repair.
It didn't work too :/

Here is output from boot repair - [http://paste.ubuntu.com/8561024/](http://paste.ubuntu.com/8561024/).

Do you have any ideas?
This is my working notebook :/

---

### Post by yancek on 2014-10-14
There is no reason you should not be able to install Ubuntu in UEFI and you also do not need to disable Secure Boot.  Your first partition (sda1) is an EFI partition with the Ubuntu efi files but you also have Grub in the master boot record of that drive which causes problems.  I don't use UEFI and am not familiar with LVM so can't make any suggestions but I'm sure someone else will be along shortly.

---

### Post by marekf on 2014-10-15
I finally solved my issue.

I copy ubuntu EFI files to Microsoft/Boot directory based on this article - [http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)

---

