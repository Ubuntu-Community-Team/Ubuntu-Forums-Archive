---
title: "Hardy hda  now sda - Please help"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by leo123 on 2008-04-27
Hi,

First time Ubuntu user here with 2 hard drives. After installing Hardy Ubuntu I cannot boot to Kubuntu (7.04). For the last five hours I've ran across very good tutorials dealing with GRUB, hda vs sda, but to no avail am I able to make the right changes to both fstabs and menu.lsts.

Ubuntu - sda
Kubuntu - sdb

Someone, please point me in the right direction so that I can boot to Kubuntu. I finally got sound working on Ubuntu and am excited about learning it, but need to still boot into Kubuntu in the meantime.
 

**ls -l /dev/disk/by-uuid**
lrwxrwxrwx 1 root root 10 2008-04-27 16:02 35eb2dec-c94f-41ed-9f7a-501295dda8b4 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-04-27 16:02 5bb61d2d-aa51-4ae8-9335-52fce967faed -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-04-27 16:02 baacd3b8-f063-4156-a923-064f151e1000 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-04-27 16:02 d470633e-8c2b-4dbe-a144-910257af1c26 -> ../../sdb3
lrwxrwxrwx 1 root root 10 2008-04-27 16:02 facfc3ef-a7c8-4b3a-b71f-78352831260e -> ../../sdb1

**********************************************************************
**blkid**
/dev/sda1: UUID="35eb2dec-c94f-41ed-9f7a-501295dda8b4" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="baacd3b8-f063-4156-a923-064f151e1000" 
/dev/sdb1: TYPE="swap" UUID="facfc3ef-a7c8-4b3a-b71f-78352831260e" 
/dev/sdb2: UUID="5bb61d2d-aa51-4ae8-9335-52fce967faed" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="d470633e-8c2b-4dbe-a144-910257af1c26" SEC_TYPE="ext2" TYPE="ext3"
**********************************************************************
**Ubuntu menu.lst**
 title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=35eb2dec-c94f-41ed-9f7a-501295dda8b4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=35eb2dec-c94f-41ed-9f7a-501295dda8b4 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Kubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb2)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5bb61d2d-aa51-4ae8-9335-52fce967faed ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot
************************************************************************

**Ubuntu fstab**
# /dev/sda1
UUID=35eb2dec-c94f-41ed-9f7a-501295dda8b4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=baacd3b8-f063-4156-a923-064f151e1000 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**************************************************************************


**Kubuntu menu.lst**
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=35eb2dec-c94f-41ed-9f7a-501295dda8b4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5bb61d2d-aa51-4ae8-9335-52fce967faed ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5bb61d2d-aa51-4ae8-9335-52fce967faed ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title		linux (on /dev/hda3)
root		(hd0,2)
kernel		/boot/vmlinuz BOOT_IMAGE=linux root=/dev/hda3 acpi=on resume=/dev/hda1 splash=silent vga=788 
initrd		(hd0,2)/boot/initrd.img
savedefault
boot

title 		PCLINUX OS 2.6.22.17.tex2
root		(hd0,2)	
kernel 		/boot/vmlinuz-2.6.22.17.tex2 BOOT_IMAGE=2.6.22.17.tex2 root=/dev/hda3 acpi=on resume=/dev/hda1 splash=silent vga=788
initrd 		(hd0,2)/boot/initrd-2.6.22.17.tex2.img
*************************************************************************

**Kubuntu fstab**

# /dev/hdd2
UUID=5bb61d2d-aa51-4ae8-9335-52fce967faed /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd3
UUID=d470633e-8c2b-4dbe-a144-910257af1c26 /home           ext3    defaults        0       2
# /dev/hda1
UUID=35eb2dec-c94f-41ed-9f7a-501295dda8b4 /media/hda1     ext3    defaults        0       2
# /dev/hda5
UUID=baacd3b8-f063-4156-a923-064f151e1000 none            swap    sw              0       0
# /dev/hdd1
UUID=facfc3ef-a7c8-4b3a-b71f-78352831260e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  vfat rw,user,noauto 0       0
/dev/sdb2	/media/ipod	vfat	rw,user,	0 0
************************************************************************

Thank you,

leo123

---

### Post by Rallg on 2008-04-27
Seems like you know what you are doing, so I cannot discern the problem. Are you booting from removable media (such as USB)? If, so, does the media think it is hd0, and that your hard drive is hd1? Also, if you reformatted anything during install, its UUID changed, so be sure that the menu.lst has the correct UUID values.

---

### Post by Cresho on 2008-04-27
Here read this

[http://ubuntuforums.org/showthread.php?t=726841&highlight=grub](http://ubuntuforums.org/showthread.php?t=726841&highlight=grub)

specifically the second to the last post.  that is my post.  it talks about the hardrives.

---

### Post by lemming465 on 2008-04-27
More details on exactly what happens when you try to boot kubuntu would help.  I find that identifying fixed disk partitions by UUID is a nuisance on systems which have multiple installs, because every time I reformat a partition the UUID changes, and that can mess up mounting and cause boot problems.

In this case, I'm guessing that your MBR is now owned by ubuntu 8.04; the corresponding kubuntu boot should make the kubuntu /boot/grub/menu.lst irrelevant.  I don't remember if 7.10 was before or after the hd -> sd conversion; if after, the
```
/dev/sdb2 /media/ipod vfat rw,user, 0 0
```
would tend to conflict with the root partition.

---

### Post by leo123 on 2008-04-27
Cresho & Rallg, thank you both for your posts.

lemming465, thank you. When I try to boot to Kubuntu, it seems as though it is going to boot and then it goes to the command prompt. It says something about the UUID's also.


Yes, MBR is owned by ubuntu 8.04. I didn't even realize that sdb2 was already there for ipod.

You're right it's probably a conflict with the root partition. How can it be fixed?

Thank you,

leo123

---

### Post by lemming465 on 2008-04-28
Once a kernel is loaded, /sbin/init is started (from the initial ram disk) to get the system live.  This is where upstart or the legacy /etc/init.d scripts come into the game.  Very early in the boot process it tries to mount file systems.  If that fails, instead of *going multiuser* it drops you into a single-user root shell.  Probably also off the ramdisk, and not necessarily as big as bash; it could be something like ash, dash, or busybox (I'd have to research it to get the exact answer).

Try typing "more /proc/partitions" and "more /proc/mounts" to see what the disks look like and what got mounted.  If you can fix the problems, exiting the root shell might go multiuser instead of rebooting, but only if the root filesystem got mounted.

You can also strip down the kubuntu fstab to only have the lines for root and home; the rest of the stuff isn't needed to boot and log in, just to make life pleasant. You can temporarily run without swap space, for example, long enough to get in and fix things. 

You could also try using device names in fstab instead of UUID's.  The thing the UUID's are most helpful for is hot-pluggable firewire or USB drives, which won't necessarily show up with the same name each time, because it depends on what else is plugged in and turned on, and what order they were added.

E.g. if /proc/partitions shows hda and hdd, try an fstab of
```
/dev/hdd2 / ext3 defaults 0 1
/dev/hdd3 /home ext3 defaults 0 2
```
Or if /proc/partitions shows sda and sdb, try
```
/dev/sdb2 / ext3 defaults 0 1
/dev/sdb3 /home ext3 defaults 0 2
```

You can also try commenting out the lines in the kubuntu /etc/fstab one at a time, (insert a leading '#'), starting with the ipod line.  That
requires having the kubuntu root partition mounted read-write; if the kubuntu boot doesn't get that far do it from ubuntu instead.

---

### Post by leo123 on 2008-04-28
lemming465,

Thank you!!! :)

> You can also try commenting out the lines in the kubuntu /etc/fstab one at a time, (insert a leading '#'), starting with the ipod line.

Did everything you said in last post and this is what made Kubuntu bootable again.

Once again, thank you for taking the time and for giving step-by-step directions, and helping me learn more about Ubuntu.

Haven't used Gnome in years, but I have a feeling that is changing now.

leo123

---

### Post by lemming465 on 2008-04-28
> Haven't used Gnome in years, but I have a feeling that is changing now.

Ubuntu and Kubuntu are not mutually exclusive.  One of the first things I do with Ubuntu installs is add the *kubuntu-desktop* package ...

---

### Post by leo123 on 2008-04-28
lemming456'

Thanks, it's installing now.

leo123

---

