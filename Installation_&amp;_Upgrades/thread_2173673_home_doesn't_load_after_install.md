---
title: "/home doesn't load after install"
date: 2013-09-10
forum: Installation &amp; Upgrades
---

### Post by barraclm on 2013-09-10
[COLOR=#333333][FONT=UbuntuRegular]My PC has 6 drives.[/FONT][/COLOR]

[LIST]
[*]/dev/sda, /dev/sdb, /dev/sdc and /dev/sdd are 750Gb SATA drives. Each drive has one partition filling the complete drive (/dev/sda1, /dev/sdb1, /dev/sdc1, and /dev/sdd1). These partitions have data on from my previous installation of Ubuntu 12.04.

[*]/dev/sdj is a 73GB SAS drive. It has 2 partitions: /dev/sdj1 for the OS and /dev/sdj2 for swap.

[*]/dev/sdi is a 73GB SAS drive which is currently unused but will eventually be a RAID1 array with/dev/sdj.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]All partitions are EXT4 (except for the swap).[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I am trying to install 13.04 from a Live CD. It boots and I select Try Ubuntu. I then get a terminal window and install mdadm. I follow this with mdadm --assemble --scan which creates /dev/md1 from/dev/sda1, /dev/sdb1, /dev/sdc1, and /dev/sdd1.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**[Gparted now shows an array called /dev/md1 with a single partition called /dev/md1p1 and I can mount/dev/md1 on /mnt and see my data (after which I umount it). However when I am installing (see below) the partition on array /dev/md1 is shown as /dev/md1.]**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**I then close the terminal window and run the install. When I get to the choice of what I want to do I chose "Something Else". I change /dev/md1 (the partition) to EXT4, mount point /home and *NO format*. I change /dev/sdj1 to EXT4, mount point / and *format*. I select /dev/sdj for boot loader.**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**All appears to work fine and I reboot when asked. However, all is not fine! Ubuntu starts to load but gives me the message the disk drive for /home is not ready yet or not present. My options are to Continue to Wait (for ever), Skip mounting (which brings up a login prompt but when I login it returns me to the login prompt) or Manual recovery (which drops me into a shell where I try to install/load mdadm but can't as mdadm, and postfix cannot be authenticated and if I press on regardless it fails saying"Something wicked happened resolving 'us.archive.ubuntu.com:http' (-11 - System Error)"**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**Help Please!**[/FONT][/COLOR]

---

### Post by steeldriver on 2013-09-10
It sounds like you just need to get a working internet connection so that you can proceed with the mdadm install - do you have wired ethernet? You may find it easiest to boot to the grub menu, and then choose 'recovery mode with networking' and do it from there. Once mdadm is installed and you have assembled the array, remember to run 'update-initramfs -u' to make the initial RAM image aware of the array.

---

