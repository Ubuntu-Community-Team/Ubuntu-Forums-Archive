---
title: "Grub (0.97) don't install correctly"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by malako on 2010-02-01
I am trying to install 64bit Ubuntu 9.10 from a USB stick on a laptop with Intel Matrix Storage fakeRAID (RAID 0). I get no error messages during installation. 

The problem is when i restart the computer Windows boots and there is no sign of Grub.

I have tried to change the grub installation device to other partitions but it doesn't work.

isw_ebbhhahejd_RAID  (default)
isw_ebbhhahejd_RAID1 (ntfs, windows 7 loader)
isw_ebbhhahejd_RAID3 (ntfs, windows 7)
isw_ebbhhahejd_RAID2 (swap)
isw_ebbhhahejd_RAID4 (ext4, root)

I then tried to install grub manually (with help from [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)) but i get the following error:

root@ubuntu:/# grub-install /dev/mapper/isw_ebbhhahejd_RAID
expr: non-numeric argument
/dev/mapper/isw_ebbhhahejd_RAID4 does not have any corresponding BIOS drive.

When starting grub prompt i see this:
Unknown partition table signature

When checking geometry i get this:
geometry (hd0)
drive 0x80: C/H/S = 24321/255/63, The number of sectors = 390721968, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 2, 
Error 18: Selected cylinder exceeds maximum supported by BIOS
   Partition num: 3, 
Error 18: Selected cylinder exceeds maximum supported by BIOS

I don't know where to go from here. I guess grub has problems finding the file systems on the fakeRAID.

I also followed the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto#Install%20the%20Bootloader%20Package") instructions but got stuck at when setting root to hd0,3.

root (hd0,3)

Error 18: Selected cylinder exceeds maximum supported by BIOS

Please help. I have been pulling my hair for 3 days.
Don't want to ditch the RAID and reinstall Windows.

Thanks in Advance

Malako

---

### Post by presence1960 on 2010-02-01
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Error 18 means your files needed to boot are beyond the limit on the hard disk readable by your BIOS. There are 2 ways to fix this: check for a BIOS update that fixes that issue or create a separate boot partition within the limit that your BIOS can read, like at the very beginning of the hard disk. 150-200 MB should be enough room for the separate boot partition.

---

