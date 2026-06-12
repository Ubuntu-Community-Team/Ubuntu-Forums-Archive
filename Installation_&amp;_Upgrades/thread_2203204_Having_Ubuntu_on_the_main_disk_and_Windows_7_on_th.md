---
title: "Having Ubuntu on the main disk and Windows 7 on the mSATA?"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by Antoine_PURNELLE on 2014-02-02
I the Dell Inspiron 17R SE laptop with 3 disks :

[LIST]
[*]sda : 128 GB SSD SATA III
[*]sdb : 750 GB HDD SATA III
[*]sdc : 240 GB SSD mSATA III
[/LIST]

I want to have Windows 7 on sbc because it needs a lot of space. I managed to do that but since the mSATA isn't recognized by the BIOS as a boot device, the 100MB system partition has been placed on sda. After that, I wanted to install Ubuntu on sda. I used gparted to create the necessary partitions without touching the 100MB one and installed the system. After that, my computer loops on the BIOS. I tried several things that I found on the internet but nothing worked. Actually, I didn't seem to find someone who was trying to do something like this.
I have used Windows Repair to be able to boot Windows but I really want to be able to do this configuration.
I don't have a problem with erasing Windows to start with a perfectly clean computer. I don't really know what do to here. Should I install Ubuntu first then Windows, is there something to do with a live CD (other than just installing Ubuntu)?
Thank you for the help. It will be much appreciated. :)

PS : I hope that I posted my thread at the right place and respected the rules. I also hope that I am clear enough.

---

### Post by fantab on 2014-02-02
Boot with Ubuntu Live DVD, then 'Try Ubuntu without Installation'. Open Terminal [ctrl+alt+T], run the following commands and post their output here.

```
sudo parted -l
sudo fdisk -l
```

---

### Post by oldfred on 2014-02-02
Did you install Windows 7 in BIOS or UEFI mode. DVD only installs in BIOS, but you can convert flash drive to UEFI if desired.
Windows 7 in BIOS mode will default to another 100MB boot partition and put that on the drive that BIOS is set to boot from. Can you not boot at all from msata drive? Most systems seem to just see it as another drive. Or did mdata still have RAID meta-data left over from Intel SRT that caused boot issues?

some other Dell threads.
 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

---

### Post by Antoine_PURNELLE on 2014-02-02
Hi. Thank you both for your answers.

Here are the two outputs :
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA OCZ-VERTEX4 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      107MB   128GB  128GB   extended
 6      107MB   119GB  119GB   logical   ext4
 5      119GB   128GB  8589MB  logical   linux-swap(v1)
 
 
Model: ATA INTEL SSDMCEAC24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  240GB  240GB  primary  ntfs
 
 
Model: ATA ST9750420AS (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
 
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  750GB  750GB  primary  ntfs
 2      750GB   750GB  105MB  primary  ntfs
 
 
Model: PLDS DVDRWBD DS-6E2SH (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
 
Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      3669MB  3678MB  9306kB               EFI

```

```
ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002c62b
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          208894   250068991   124930049    5  Extended
/dev/sda5       233293824   250068991     8387584   82  Linux swap / Solaris
/dev/sda6          208896   233293823   116542464   83  Linux
 
Partition table entries are not in disk order
 
Disk /dev/sdb: 240.1 GB, 240057409536 bytes
255 heads, 63 sectors/track, 29185 cylinders, total 468862128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x003d975b
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   468860927   234429440    7  HPFS/NTFS/exFAT
 
Disk /dev/sdc: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd00a002d
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1464842239   732420096    7  HPFS/NTFS/exFAT
/dev/sdc2      1464842240  1465047039      102400    7  HPFS/NTFS/exFAT

```


@oldfred, using the Windows Repair Tool and the "bootrec /fixmbr" command, I can boot from the mSATA as I did before installing Ubuntu. Sadly, it only allows to boot on Windows (which is quite obvious).

---

### Post by oldfred on 2014-02-02
Did you install grub2's boot loader to the MBR of the Ubuntu drive? Then in BIOS choose to boot from that?

You can change where grub is installed only if you use Something Else or manual install. Or you can use Boot-Repair, but do not run auto fix as that just installs grub2's boot loader to every MBR. You want to use advanced, choose Ubuntu install partition and choose to install to the MBR of the ubuntu drive.

---

### Post by fantab on 2014-02-02
If you have fixed Windows boot (and had Ubuntu installed during this) then Windows would have messed with Grub boot files. You will need to [reinstall Grub]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd").

---

### Post by Antoine_PURNELLE on 2014-02-03
It doesn't seem to be enough...

Here's what I did and the output :
```
ubuntu@ubuntu:~$ sudo mount /dev/sda6
mount: can't find /dev/sda6 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# 
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# 
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sdc2
done
root@ubuntu:/# exit && sudo umount /mnt/dev && sudo umount /mnt/dev/pts && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
exit
```

After that, same problem as before :  the computer is stuck in a loop displaying the Dell logo then rebooting. Any idea please?

---

### Post by fantab on 2014-02-03
Install [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") on Ubuntu DVD/USB, create and post the 'Bootinfo Summary', just post the LINK.

---

### Post by Antoine_PURNELLE on 2014-02-03
Here's my Bootinfo Summary : [http://paste.ubuntu.com/6866858/](http://paste.ubuntu.com/6866858/)
By the way, what's on sdb is copy of the Windows MBR partition that I made.

I don't think it is needed but here's my Bootinfo Summary before reinstalling grub : [http://paste.ubuntu.com/6866848/](http://paste.ubuntu.com/6866848/)

---

### Post by oldfred on 2014-02-03
You had Windows boot files in sda1 or 128GB drive in first BootInfo, but second does not show any. Did you delete them or did BootInfo report just not show them?

Are you Booting in BIOS boot mode from your UEFI/BIOS? The other 17R we have seen are UEFI systems, but you can boot in UEFI or BIOS mode. You also must have UEFI secure boot off as with secure boot on only secure boot systems will be allowed to boot. And no BIOS boot is secure boot.

The way Windows shows in first link, is that you installed Windows to sdb, but had BIOS set to boot from sda, so Windows put its boot partition on sda. Windows defaults boot to drive set as default in BIOS and  then every  install of Windows put boot files into the one primary partition with the boot flag or active partition as Windows calls it.

---

### Post by Antoine_PURNELLE on 2014-02-04
Okay it is solved.

I deleted the 100MB Windows partition that I had in backup on the sdb, I completely erased the sda, even the Windows partition and created 2 primary partitions for Ubuntu : / and swap. Then, I reinstalled Ubuntu and now everything works perfectly. The grub found Windows on sdb and I can dual-boot without any problem.

Thank you very much fantab and oldfred. You helped me to better understand how it works. :D

---

