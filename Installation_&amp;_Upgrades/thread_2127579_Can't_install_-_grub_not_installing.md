---
title: "Can't install - grub not installing"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by AnalBeard on 2013-03-20
Ok, so this issue is reproduceable on both 12.10 and Mint 14 (after upgrading Ubiquity in Mint). I have a Dell XPS14 which has a 500GB hdd (sda) and a 32GB ssd (sdb).

I want to install Mint or Ubuntu on sdb, however at the end of the installer it complains that it cannot install grub on sda - i don't want to install it on sda, i want it on sdb. This is using the guided installer with full disk encryption enabled.

Can anyone shed any light on this?

---

### Post by oldfred on 2013-03-20
I really do not know about encryption, but got involved with this thread. I think he wanted grub on external flash drive.
[http://ubuntuforums.org/showthread.php?t=2124271](http://ubuntuforums.org/showthread.php?t=2124271)

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by sudodus on 2013-03-20
If you are installing from the desktop iso with the GUI: at the partitioning page of the installer, select ***Something else***, and select to ***install grub to ***[SIZE=3]**[FONT=courier new]/dev/sdb[/FONT]**[/SIZE] (not sda, not any number sdb1 etc). There is a corresponding page in the alternate installer (text based).

---

### Post by darkod on 2013-03-20
Is this a laptop with combo hdd+ssd? Usually they come configured as a sort of raid, or Intel RST. Even if you break the IRST thee is still meta data remains on the disks which confuses linux whether you are using raid or not. This is the most often cause why grub2 install fails.

If you did break the IRST, try removing meta data from live mode with:
```
sudo dmraid -Er /dev/sda
sudo dmraid -Er /dev/sdb
```

But if you are still using IRST don't run the commands since I'm not sure what it will do.

Also, if you want grub2 to be on sdb you can't use the guided installer since I think by default it will try to install to the first disk, sda. You have to use the manual install for more control.

---

