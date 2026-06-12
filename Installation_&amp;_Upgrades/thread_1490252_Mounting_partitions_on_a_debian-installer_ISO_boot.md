---
title: "Mounting partitions on a debian-installer ISO booted via grub2 copied to tmpfs"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by deepclutch on 2010-05-22
[SIZE=3][FONT=Tahoma]Hello,
I am trying to install Debian using Netinstall ISO(Similar to Ubuntu Alternate CD) by booting from GRUB2 of My Lucid Ubuntu already in the System.

I use below menuentry to boot debian-netinst-iso(Which is in /dev/sdb7/debian -directory),by adding these lines to /etc/grub.d/40_custom and "sudo update-grub":
[/FONT][/SIZE]```
[FONT=Tahoma][SIZE=3][B]menuentry "Debian ISO on /dev/sdb7" {
insmod ext2
set root=(hd0,7)
loopback loop /debian/debian-testing-amd64-netinst.iso
linux (loop)/install.amd/vmlinuz boot=install.amd iso-scan/filename=/debian/debian-testing-amd64-netinst.iso noeject noprompt 
initrd (loop)/install.amd/initrd.gz
}[/B][/SIZE][/FONT]

```

[SIZE=3][FONT=Tahoma]The debian ISO Boots Directly triggering debian-installer-Which asks for where to search for "CD" containing debian-testing-amd64-netinst.iso .This is where the Problem Starts.

I installed Ubuntu Earlier by Symlinking the Ubuntu ISO to CDROM device file /dev/sr0 and install went Fine.
--
But ,with Debian ISO Booted as Live CD,I cannot Mount Hard Disk Partition(/dev/sdb7) which contains the "debian-testing-netinst-amd64.iso" image.
If I try to Mount ,it Errors Out :
[/FONT][/SIZE]```
[FONT=Tahoma][SIZE=3]mount:mounting /dev/sdb7 on /debian failed: No such device[/SIZE][/FONT]
```
[FONT=Tahoma][SIZE=3]
But ,If I search /proc/partitions, I can see hard disk partitions.

AND:
the Debian Live CD is operating from tmpfs completely.If I try "df -H" ,It shows tmpfs as mounted.

How Can I mount the hadr disk partitions When the Livecd is booting from tmpfs(ramdisk)?


OR ,Is there a way,I can copy debian-testing-amd64-netinst.iso Which is ~160MB only to RAM ?

Thanks[/SIZE][/FONT]

---

### Post by deepclutch on 2010-05-23
[FONT=Tahoma][SIZE=3]Hello,

Installed Debian testing using **[debian-testing-amd64-netinst.iso]("http://cdimage.debian.org/cdimage/daily-builds/")** daily built snapshot on to a ext4 partition. :D 
Here is How I installed from CD ISO:
1) download **vmlinuz** and **initrd.gz** for hard disk boot provided by Debian team here:
For Mine ,**64-bit OS** ,I downloaded from amd64 folder:
[http://ftp.debian.org/debian/dists/sid/main/installer-amd64/current/images/hd-media/](http://ftp.debian.org/debian/dists/sid/main/installer-amd64/current/images/hd-media/)
I downloaded the "capable"(supports more filesystems,specifically for hard disk iso booting) Linux and initrd.gz to /dev/sdb7 /debian folder,Where "debian-testing-amd64-netinst.iso" iso also resides.

2)I'm having Ubuntu 10.04 Lucid  already on another partition with Grub2 Bootloader.
I added below entry to boot the debian iso from grub2(for booting iso which is in "debian" folder on /dev/sdb7):
```
[B]menuentry "Debian ISO on /dev/sdb7" {
insmod ext2
set root=(hd0,7)
loopback loop /debian/debian-testing-amd64-netinst.iso
linux  /debian/vmlinuz boot=/debian iso-scan/filename=/debian/debian-testing-amd64-netinst.iso noeject noprompt INSTALL_MEDIA_DEV=/dev/sdb7
initrd /debian/initrd.gz
}[/B]

```^I don't think "INSTALL_MEDIA_DEV=/dev/sdb7" has any effect on debian-installer searching for debian ISO.But ,that's how I booted with ISO.

3) When Debian ISO Boots, It starts debian-installer(it's also a command,once booted)  with ncurses based User Interface.
the installer offers to search for debian compatible isos on different hard disk partitions.It cannot search on ext4 partitions(that's what I experienced).
Knowing this ,I copied debian-testing-amd64-netinst.iso to a ext3 partition at /dev/sdb8 .
Installer searched and mounted debian-testing-amd64-netinst.iso as a loop device /dev/loop1
and install proceeds as usual.I ended up with a network enabled system also grub2 installed from the Debian.
**PS:***I don't know ,but when I tried loop mount or even mount ext3,ext4 partition it never worked with debian netinst cd iso!when boots it supports only a couple of file system formats like isofs,vfat(fat32).. .no ext3 also.I think ,later on ,debian-udebs(kernel modules are stored as *.udeb)  containing the necessary modules has to be extracted and installed,thus ext3 and ext4 supported!*

I have to install Gnome and apt-pinning selections(for testing+unstable) later on as It needs to download a lot of packages which I will do later tonight.

Thank You All For the Support. :)
[/SIZE][/FONT]

---

