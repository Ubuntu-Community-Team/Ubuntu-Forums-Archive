---
title: "messed up windows 7 boot loader"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by poldie on 2010-07-19
At least, I think that's what I've done. Certainly it doesn't boot and I get a grub recovery prompt.

I'm trying to install ubuntu 10.04 to a usb key, and the install completes normally, but I think the default option must be to edit the local hard drive's boot system to boot from the usb key - a spectacularly stupid thing to do, given that the whole point of installing an OS to a usb key is that you'll be using it on other PCs.  Perhaps this isn't what happened, but I'm now on the same laptop (dell lattitude e6400) using a live ubuntu 10.04 so the laptop is working fine; I can see files on the hard drive.

I've done fdisk -l and I get:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x117d3f32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9730    78046208    7  HPFS/NTFS


I don't seem to be able to boot from my windows 7 disk.

A lot of the help on the net seems to refer to earlier versions of grub than is supplied with ubuntu 10.04, so the help doesn't work.

Is there anything I can do to get windows 7 to boot?  I don't mind using grub to boot windows.

---

### Post by Sticky_Bit on 2010-07-19
I ran into a similar issue. You are going to want to use your Win 7 disk to do a repair and fix the boot loader using fixboot and fixmbr. 

The following article may help. [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by poldie on 2010-07-19
> **Sticky_Bit said:**
> I ran into a similar issue. You are going to want to use your Win 7 disk to do a repair and fix the boot loader using fixboot and fixmbr. 

The following article may help. [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

I don't seem to be able to boot from my win 7 disk though.

---

### Post by oldfred on 2010-07-19
Lilo boot loader works the same way as windows and will boot windows from the MBR. You installed grub to sda when you wanted it installed to the USB drive. You should use the advance button on the last partition screen where it says ready to install. 

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

---

### Post by Sticky_Bit on 2010-07-19
> **poldie said:**
> I don't seem to be able to boot from my win 7 disk though.

I mean you need to boot from the Win 7 installation media, not the hard drive. If you can't boot the installation media. You need to enable booting from cd/dvd in your bios.

---

### Post by poldie on 2010-07-21
> **oldfred said:**
> Lilo boot loader works the same way as windows and will boot windows from the MBR. You installed grub to sda when you wanted it installed to the USB drive. You should use the advance button on the last partition screen where it says ready to install. 

[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

per kansasnoob Note: If I use Lilo to restore a Windows MBR using my "installed" Ubuntu I always like to remove the package "lilo" when done just to prevent some later "conflict" with grub updates, this of course is as easy as "sudo apt-get remove lilo".

Thanks, that did the trick.

---

