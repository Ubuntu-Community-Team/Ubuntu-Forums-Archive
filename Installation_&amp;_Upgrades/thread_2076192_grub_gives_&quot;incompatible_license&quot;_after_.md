---
title: "grub gives &quot;incompatible license&quot; after 12.10 upgrade"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by adenbley on 2012-10-25
i did an upgrade to 12.10 and now i get an "incompatible license" error  at boot and it drops me into grub repair.  the system is installed on a  mdadm raid1 device.  i have tried changing the boot order in bios.  i  have tried boot-repair using default settings and here is the log  [http://paste.ubuntu.com/1303696/](http://paste.ubuntu.com/1303696/) .

i will only be supporting this  machine for about 1 more year, so if fixing it will make my  replacement's job more difficult i would prefer to do a fresh install to  12.04 server since this computer is only used headless, and doesn't run  anything that requires x (right now it is running desktop).

---

### Post by dino99 on 2012-10-25
thats is due to the newest grub 2.0 which conflict with the previous grub 1.99 before upgrading . So the solution is to purge then reinstall grub-pc to only get a pure grub 2.0 installation.

so:

sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc

it will ask you where to install the bootloader (usually /dev/sda , but in your case it might be something like /dev/mda)

---

### Post by adenbley on 2012-10-25
i tried your commands from a live-usb and it will not do it because it says failed to get canonical path of /cow and path /boot/grub is not readable by grub on boot.  there is an option in boot-repair that reads "update to latest version" (or something like that) but when i tried it it complained that the repository for grub2 wasn't included.  i added universe and ran apt-get update, but that didn't change it (i think it is talking about the sources on the md1).  

is there a way to remove and reinstall grub without using apt-get or boot-repair on the drives?

---

### Post by YannBuntu on 2012-10-25
Hello

> **adenbley said:**
> i did an upgrade to 12.10 and now i get an "incompatible license" error  at boot and it drops me into grub repair.  the system is installed on a  mdadm raid1 device.  i have tried changing the boot order in bios.  i  have tried boot-repair using default settings and here is the log  [http://paste.ubuntu.com/1303696/](http://paste.ubuntu.com/1303696/) .

According to this log, your upgrade has failed, because you only have:
11.04 on /dev/sda3
11.10 on /dev/sdb3
11.10 on /dev/md1

so if i were you, i would reinstall the 11.10 which failed to upgrade, this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

**@dino99:** please would you have any link talking about such conflict?

---

