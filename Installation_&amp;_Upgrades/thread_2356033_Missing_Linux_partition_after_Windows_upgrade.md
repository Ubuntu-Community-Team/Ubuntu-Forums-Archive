---
title: "Missing Linux partition after Windows upgrade"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by aruninterval on 2017-03-19
Hi,

My computer had dual boot option. Windows 10 and Ubunto 16.04.

But after some upgrade,it wont dual boot. I used livecd and opened gparted. Now the ubuntu partiton is shown as unallocated.

This is the gparted output:

[ATTACH=CONFIG]274218[/ATTACH]

Also, the fdisk output is shown below:

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 487422149 487420102 232.4G  7 HPFS/NTFS/exFAT
/dev/sda2       487424000 488345599    921600   450M 27 Hidden NTFS WinRE
/dev/sda3       488347646 976771071 488423426 232.9G  f W95 Ext'd (LBA)
/dev/sda5       968583168 976771071   8187904   3.9G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.




Disk /dev/sdb: 14.6 GiB, 15631122432 bytes, 30529536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002252c

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 30529535 30527488 14.6G  c W95 FAT32 (LBA)

I would appreciate any help in this case.

Regards 
Arun

---

### Post by oldfred on 2017-03-19
Moved to your own thread as your issue is different than original solved thread. Issue is that Windows update forgets to write the Linux partition back into partition table. Some are able to just recover partition and system works, most do have to use Boot-Repair or manually reinstall grub to MBR.

       [http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

