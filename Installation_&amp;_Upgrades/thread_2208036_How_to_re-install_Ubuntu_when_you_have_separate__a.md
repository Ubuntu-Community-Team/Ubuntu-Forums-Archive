---
title: "How to re-install Ubuntu when you have separate / and /home partitions"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by desconocido on 2014-02-26
I installed the amd64 version of Ubuntu 12.04.3 a new Toshiba laptop (that had Windows on it). This instalation formatted and used the whole of the hard disk.

After various problems, I needed to re-install. So I decided to put my /home directory on a separate partition first. Using Gpartd, I shrank the main partition, created a new one, juggled my data onto the new partition, reinstalled Ubuntu on the old partition, restarted, edited /etc/fstab thus:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=16866923-a89d-4c9f-8222-e809b3985709 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=136D-0C69  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=3620fc8f-cfa8-4aa7-9438-43dcd827efb4 none            swap    sw              0       0
# extra second data partition on /dev/sda4 created 8-Feb-2014
UUID=c8e24e24-36ff-4a99-99b7-ce032cabda77 /home               ext4    errors=remount-ro 0       2
```

and restarted. All ok.

After more problems, I needed to re-install again! Ran the DVD again but this time I got a bit confused, because the options were different.
I'm not sure exactly what I chose, but I think I chose to put the bootloader on /dev/sda instead of /dev/sda1 or not format /dev/sda2 or both. I think that the installer offering me /dev/sda as the first option as location for the boot loader misled me.

Booting gave me:

```
An error occured while mounting /boot/efi
Press S to skip mounting or M for manual recovery.
```

and when I could finally get to see /var/log/installer/syslog
it was full of Fatal errors to do with efi, grub etc.

I installed again, putting the bootloader on /dev/sda1 and installing and **formatting** /dev/sda2 and not mentioning /dev/sda4 at all.

This worked fine and I could edit /etc/fstab again to mount /home on /dev/sda4.
The username I specified was the same each time I installed.

I was scared to specify /home as a mount point for /dev/sda4 at install time, even with "format" off because I didn't know whether it would
a) respect all my existing data
b) replace /home with a virgin set of data or
c) leave my existing data unless it needed to be overwritten by virgin data.

Hope this is useful.

---

### Post by zvacet on 2014-02-26
> I was scared to specify /home as a mount point for /dev/sda4 at install time, even with "format" off 

Thaat was right thing to do.Select that you will use partition as ext4 an **do not format it**.That way your data and files will be safe.Just to remind you; nothing is 100 % sure. ;)

---

### Post by desconocido on 2014-03-01
> **zvacet said:**
> ...use partition as ext4 an **do not format it**...

So if I selected /dev/sda4 as ext4, no format and mount as /home, the Ubuntu installer would not write to it at all?

---

### Post by oldfred on 2014-03-01
I would still have a good backup of /home, but it should preserve the settings and all data you have for all your installed apps. But it may install some new settings.

I have seen it ask if you want to preserve your settings or use defaults from installer. And sometimes either choice is wrong. Or your old settings  may not work or not be needed if a new version install, or new settings totally overwrite your custom settings which were really needed to make system work. So I always accept changes, but have backups in case I need the custom settings I have made.

You have a UEFI boot install, but need to be sure to always install in UEFI mode. And how you boot installer either BIOS or UEFI is how it installs.
With UEFI or BIOS you install grub to sda, but with UEFI it always puts the grub2 efi files in the efi partition. 

If reinstalling you always want to use Something Else or manual install so you can choose / (root) partition and /home partition during install. It should find swap automatically.

---

### Post by desconocido on 2014-03-01
> **oldfred said:**
> Thanks. This thread is getting quite close to being finished, unless anyone else wants to make a comment?

---

### Post by desconocido on 2014-03-04
> **oldfred said:**
> I would still have a good backup of /home, but it should preserve the settings and all data you have for all your installed apps. But it may install some new settings.
If reinstalling you always want to use Something Else or manual install so you can choose / (root) partition and /home partition during install. It should find swap automatically.

I took the plunge, backed up my home directory, ran the live DVD, deleted all . files/folders in ~ except the ones I needed:
	.gtk-bookmarks
	.mozilla/
	.thunderbird/
	.themes/
and re-installed Ubuntu 12.04 (amd64) using 
/dev/sda1 (type efi) as "Device for boot loader installation",
/dev/sda2 (type ext4) mount as / with format option, 
/dev/sda4 (type ext4) mount as /home - *NO format option*

This worked fine. The above files/folders were untouched (or at least work just as they used to) and new hidden stuff was put in my home folder.

This had the added advantage that I have finally been able to install Skype and Wine on the computer - maybe there was a lot of cruft from repeated installs that was kept in my home folder? Certainly Ubuntu Software Centre's history knew about everything I did through four installs where / was formatted each time. Now history begins today!

---

