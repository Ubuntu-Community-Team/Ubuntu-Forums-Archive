---
title: "Not booting struck at GRUB"
date: 2020-06-21
forum: Installation &amp; Upgrades
---

### Post by amarbharti on 2020-06-21
My laptop Lenovo ThinkPad e14 is running on ubuntu 20.04. 
Cursor was struck and nothing was working so I rebooted the system few times in succession. 
Cursor problem was not fixed after reboot. 
Then it reboot into busybox. Thereafter it is now stuck at GRUB. I've got this file from running boot repair using bootable USB. 
[https://paste.ubuntu.com/p/DjPf5mhBYm/](https://paste.ubuntu.com/p/DjPf5mhBYm/)
Please help!!!

---

### Post by oldfred on 2020-06-21
Forced reboot can further corrupt system which then needs repairs before you can even figure out what original issue was.
Did you use this or just power down.
Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)


You show a second unknown partition p2.
Do you have good backups? If partition is gone, it may not be recoverable.

I would first try testdisk.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you do not have good backups & testdisk's deeper search shows files, immediately copy those to another drive. You may not get them after repairs.

---

### Post by amarbharti on 2020-06-22
Thanks for reply!!
I've installed Ubuntu afresh by deleting all files.

Can you tell me how to make partitions now so that I don't lose data if I reinstall OS?

---

### Post by CelticWarrior on 2020-06-22
Partitions are already made if you actually installed.
Partitions can be reused for reinstallations. Now, to not loose data the important thing to think about is backups! If you have good and current backups you can delete all partitions and start over. The next best things - but risky so you should have backuos ANYWAY - is to store your personal files in a separated data partitions that latter you don't select to format during a reinstallation.

---

### Post by oldfred on 2020-06-22
If you just used a default install, it does not create separate partitions, just one larger / (root) partition.
And if a  newer user and drive not real large that is ok. 

But often better as you get more experienced and understand partitions and amount of space you use, then you can think about having separate partitions. 

Post this:
sudo parted -l
and/or
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

