---
title: "ubuntu to replace fedora"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by geotri314 on 2011-02-03
hello guys.
i ve installed fedora 14 a few days ago, but i m not at all happy with it. i also have on the same disk, a windows xp partition, and another disk with data. i am a newbie, so i wanna know if there is a guide, or tutorial, or some guidelines if possible, on how to replace fedora with ubuntu 10.10. i ve tried to initiate the installation, but i only got the options to use free space, or erase entire disk. well, to be honest, there is a third option, prompting me to manually decide the partitions, but i know nothing about it. can you offer me any help here? please?

---

### Post by drdos2006 on 2011-02-03
If you have two disks, then disconnect your data disk.
Decide whether you want to dual-boot XP or run XP under Ubuntu with virtualbox virtual software.

Use the live Ubuntu CD and select try Ubuntu, do not install.
Use gparted from the live CD to set up the partition areas you want on your bootable harddrive. 

When Ubuntu is installed after XP in a dual boot system, Ubuntu will show a menu to select XP or Ubuntu to boot.

After installation, reconnect your data drive.

regards

---

### Post by coffeecat on 2011-02-03
> **geotri314 said:**
> there is a third option, prompting me to manually decide the partitions, but i know nothing about it.

The manual/advanced option is probably what you need. Make sure you know which is your Fedora root partition and tell the Ubuntu installer to reformat that to ext4 and set its mountpoint as '/', i.e. the root partition. The installer will pick up the swap partition automatically. One complication is that the Fedora installer probably set you up with a separate small boot partition. I suggest you abandon it - it doesn't take up much space - and let the Ubuntu installer use the root partition for the boot files. It will if you don't choose a separate boot partition for Ubuntu.

Did you have a separate home partition in Fedora?

---

