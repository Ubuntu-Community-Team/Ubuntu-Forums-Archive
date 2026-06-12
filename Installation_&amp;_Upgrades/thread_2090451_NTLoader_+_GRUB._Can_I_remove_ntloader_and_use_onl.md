---
title: "NTLoader + GRUB. Can I remove ntloader and use only GRUB?"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by avianbc on 2012-12-02
I installed Ubuntu 12.10 via the windows executable (Wubi). After install my boot goes like this:

1) ntloader - Options "Windows" and "Ubuntu"
2) If I select "Ubuntu" it then displays GRUB which only lists my Ubuntu partition.

So ntloader and GRUB2 are both there.

I would like to get ntloader to go away completely and add my Windows partition into GRUB2. Result should be only GRUB2 on boot with Windows in the list but I am afraid I will break something since I am unfamiliar with Wubi.

Here is some info that might help:
> avian@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1904351294   952175616    7  HPFS/NTFS/exFAT
/dev/sda2      1904353278  1953523711    24585217    5  Extended
/dev/sda5      1904353280  1936750591    16198656   83  Linux
/dev/sda6      1936752640  1953523711     8385536   82  Linux swap / Solaris

> avian@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

> avian@ubuntu:~$ sudo update-grub
[sudo] password for avian: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-19-generic
Found initrd image: /boot/initrd.img-3.5.0-19-generic
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
Found Windows 7 (loader) on /dev/sda1
Skipping Windows 7 (loader) on Wubi system
Found Ubuntu 12.04.1 LTS (12.04) on /dev/sda5
done

---

### Post by oldfred on 2012-12-02
Wubi requires the Windows boot loader and wubi is just a file inside the Windows NTFS partition to make it easy to uninstall. It is for those users who want an extended test (over just using liveCD) with essentially the full system. It then is easy to uninstall if you do not like Ubuntu. It also saves the issues of partitioning.

But you are showing a Linux partition and swap? Do you have a full partitioned install of Ubuntu also? Or is that another system?

If you have another system with a full install and its own copy of grub, there may be ways to boot wubi directly, but it really would be better just to do a full install. You can just create another logical partition and install.

I do not think this was intended as an way to boot wubi, but just to show it could be done with grub2.
      
See also this thread, you technically do not need windows to use wubi.
Posts by meierfra. to use grub2 to directly boot wubi
[http://ubuntuforums.org/showthread.php?p=8903013](http://ubuntuforums.org/showthread.php?p=8903013)

---

### Post by avianbc on 2012-12-02
:lolflag:   Ugh, I didnt even know WUBI installed into the windows partition. The ext4 + swap partition was my old Kubuntu partition which is where I expected Wubi to install to.

I guess that completely changes my question. I'll have to sort this out. 

I'm going to look into moving Wubi from the NTFS partition into the existing ext4 partition since I dont use Kubuntu anymore then I can use only GRUB2 as my bootloader.

Thanks for pointing this out.  Hopefully moving it will be easy since I dont want to have to reinstall and customize everything again.

---

### Post by avianbc on 2012-12-02
[https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")

Solved easily using the above link.

1) Used wubi-move-2.3 to move wubi to the ext4 partition.
2) Uninstalled Ubuntu/Wubi from windows
3) Ran sudo update-grub to add Windows onto my Grub2

Thanks for pointing me in the right direction!

---

