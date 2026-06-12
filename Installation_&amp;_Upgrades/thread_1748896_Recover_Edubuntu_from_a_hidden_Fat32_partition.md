---
title: "Recover Edubuntu from a hidden Fat32 partition"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by Ilias83 on 2011-05-04
Hello,
I own a Acer AO751h Netbook.
When I bought it there was a dual boot Windows and Edubuntu (9.04 I think)
Both systems were loading for Windows boot.ini and I had 3 options on startup:
Windows XP
Edubuntu
Restore Edubuntu

For anyone owning this Netbook is clear that it's hopeless to make it work with Windows as it's toooooo slow and Ubuntu is the only choice but there are many problems with drivers.

Unfortunately when I tried to upgrade Edubuntu to a newer version everything screw up and I had to install Ubuntu 9.10 form a USB.
The fact is that whatever I do I cannot manage to make Netbook work as smooth as with Acer's installation.

So I try to restore it.

I find out that Acer have 4 partitions.
First partition is a hidden protected NTFS 12GB to restore Windows.
Second partition is Windows NTFS partition
Third partition is a hidden FAT32 5GB that I thing is to restore Edubuntu
Forth partition is Ubuntu partition
(It's strange but they don't seem to use swap)

I managed to see files on third partition and there are many files and folder all for Ubuntu (Maybe an Ubuntu iso extracted?)

There are these folders on root directory:
.disk
casper
dists
extra
install
pool
syslinux
And two files:
ldlinux
md5sum

I erased ubuntu installation in order to install them again, I restored Windows hopping that "Restore Edubuntu" option will appear again and now I'm booting using boot.ini

Is there any way to change boot.ini in order to make it possible to install Ubuntu from HDD FAT32?

And if I manage to do this is ther any way not to mess up with grub again in order to have restore Edubuntu option available any time?

Thanks in advance

---

### Post by Ilias83 on 2011-05-05
To help out?
Is there any way to install Ubuntu through Windows but using the existing files?
Something like offline wubi...

---

