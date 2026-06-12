---
title: "How to delete Ubuntu?"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by Per M. on 2005-07-13
How do I completely delete Ubuntu from my system? It's not because I don't like it, but because I gave the partition too much space(I'll install another Linux too), and then I'll reinstall Ubuntu. And does anyone know if the GRUB bootloader will be removed along with Ubuntu?

Thank you.

Per M.

---

### Post by javiadip on 2005-07-13
Hello,

you could just boot up with Ubuntu install CD and from there edit/delete/format the partitions, and install ubuntu on your new partition. when you delete that partition, it will automatically remove your old ubuntu.

---

### Post by Per M. on 2005-07-13
Can I format the partition without the Ubuntu Install CD (With SystemRescueCd)? And will that remove the bootloader?

Per M.

---

### Post by rmjokers on 2005-07-13
You can format the partitions you have using other software.  However, you will need fdisk if you want to change their size or type (ntfs / linux / swap).  The GRUB boot loader is installed on the MBR (first sector) of the drive.  The only way to remove it is to install another boot loader in its place.  Without a boot loader, you cant boot anyway so this shouldnt be an issue.

NOTE:

When you partition a drive, the partition table is stored in the MBR along with the boot loader.  You cannot format this part of the disk because it is not part of any partition.  It is outside of the partitioned area.  The only way to completely remove this data is to copy over it or do a low-level format of the drive.

---

### Post by Per M. on 2005-07-13
Maybe I haven't understood it all, but could someone please tell me what I need to do this:

1) Uninstall Ubuntu

2) Make two EXT3 partitions of the one that Ubuntu was previously installed to

3) Install Mandrake 10.1 on one of the EXT3 partitions (I think I know how that is done!)

4) Install Ubuntu to the other EXT3 partition (That one too!)

5) Have a GRUB bootloader to boot WinXP, Ubuntu and Mandrake

Please please please help.

Per M.

---

### Post by skirkpatrick on 2005-07-13
Well, you don't have to uninstall Ubuntu.  If you're going to start over, here's what I'd recommend:

1) Make a bootable DOS floppy disk and put fdisk on it.  Windows XP does not have fdisk but I think this version, [http://www.23cc.com/free-fdisk/](http://www.23cc.com/free-fdisk/), will work just fine.

2) Boot your PC from the floppy.  At the command prompt, enter "fdisk /mbr".  That will erase your MBR (Master Boot Record) since Windows doesn't need it anyway.

3) Install either Ubuntu or Mandrake.  Either will ask you if you want to delete the old Linux partitions.  Say yes and then tell the installation that you only want to use half (or whatever amount) of that partition for that installation.

4) Install the remaining distro to the remaining empty partition space.

5) By this time, GRUB should present you with the ability to boot into either Linux distro or Windows with the default being the last distro you installed, until you change Grub's boot order.

---

