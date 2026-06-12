---
title: "Installation fails on Grub (Read only EFI partition?)"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by pblanco-t on 2016-05-27
[COLOR=#111111][FONT=Ubuntu]I have a brand new Dell Inspiron 5000 with Windows 10. I've shrunk the windows partition and tried to install an Ubuntu 16.04 TLS to have a dual boot.
The installation (sda8 for / and sda9 for /home) runs well until it tries to install grub. At this point it fails with a "critical error" and I'm not able to boot Ubuntu.
Trying to repair grub with boot-repair I have the same error. I've tried installing Ubuntu 14.04 TLS with the same result.
Investigating a little I've seen that if I try to mount sda1, this partition is always read only. Is this normal? Any idea on how can I complete my dual boot? 
This is the paste bin from boot-repair:

[/FONT][/COLOR][INDENT][http://paste2.org/gCPyJFvg](http://paste2.org/gCPyJFvg)

[/INDENT]
[COLOR=#111111][FONT=Ubuntu]
By the way, I've turned off the fast boot option in Windows 10.
Thanks for your help.[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-05-27
sda1 is where Windows puts its efi boot files and it is where the Ubuntu installer needs to put the Ubuntu efi boot files. And it cannot do that if sda1 is read only. Has Dell/Microsoft found an effective way of blocking the install of Linux on machines with Windows 10 pre-installed?

Regards.

---

### Post by oldfred on 2016-05-27
I may have mentioned this elsewhere.

But we have seen corrupted ESP - efi system partitions. 
Sometimes either chkdsk from Windows or dosfsck from Ubuntu live installer may work.

              Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)
or:

 sudo fsck.vfat -t -a /dev/sda1
man dosfsck 

But in some cases we have had to copy all files from ESP - efi system partition. It is not large so easy to backup. And a good idea to have a backup anyway.
Delete partition with gparted & recreate FAT32, with boot flag to make it ESP. Restore backup.
You may have to add new entries in UEFI NVRAM as partition has changed or make other repairs, so best not to have to do this unless last resort.

---

### Post by pblanco-t on 2016-05-27
Solved here: [http://askubuntu.com/questions/778117/installation-fails-on-grub-read-only-efi-partition](http://askubuntu.com/questions/778117/installation-fails-on-grub-read-only-efi-partition)
Thanks.

---

