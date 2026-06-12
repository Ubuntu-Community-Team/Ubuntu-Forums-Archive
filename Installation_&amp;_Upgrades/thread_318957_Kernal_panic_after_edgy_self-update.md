---
title: "Kernal panic after edgy self-update"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by rexa on 2006-12-14
I have been using edgy for some time now on my core-duo gigabyte-dq6.
Using this motherboard means I have a jmicron controller and a sda type drive.

Today, after the most recent ubuntu self-update, it now will not boot, it says:
"cannot mount root fs on unknown block(0,0)

after chrooting from another linux partition, I re-installed the kernel, and got the same result." At the end of that re-install, grub says it cannot resolve the UUID of my hard drive.
fdisk cannot open the hard drive (there are no sda drives under /dev)
"ls /dev/disk/by-uuid" does nt work. (from chroot console) 

This all appears related to the last self- update today I have had no issues until now. Any ideas?

-Rex
",

---

### Post by FryerFox on 2006-12-14
Try removing the "savedefault" line from the grub menu: When the menu comes up, hit "e" to edit the entry, and then navigate to the "savedefault" line and delete it ("d", I think), then type "b" to boot. This is from memory, so I could be wrong about the shortcut keys

If this works, type:
> sudo gedit /boot/grub/menu.lst
and comment out every line that has a "savedefault" on it.

---

### Post by rexa on 2006-12-14
and then what?

update-grub still says it cannot resolve the UUID

root@XANDROS-DUO:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=a285f3b7-07a5-4176-b01e-c087fb80dc1e'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


grub's assumption of hda1 is wrong

-Rex

---

### Post by FryerFox on 2006-12-14
The HD partition should be specified in the menu.lst file, like so:
> root		(hd0,3)

Is it set correctly? What about in the file /etc/fstab - is the UUID 'a285f3b7-07a5-4176-b01e-c087fb80dc1e' in there? If so, then the comment directly above it (if one exists) may tell you which drive/partition you should be using.

---

### Post by rexa on 2006-12-14
This is not a new install. All I did was use the ubuntu auto-update.
I am using the same ubuntu boot partition I have always used.
fstab has not changed.  It refers to the same partition as before.

I am  using lilo from another linus partition to boot ubuntu and that has not changed either. It has been working fine for months. The same lilo configuration boots other linux partitions just fine.

The problem is mre fundamental than that.
I believe ubuntu no longer recognizes my) sata (scsi/sda) drive. I believe the auto-updater replced my kernel and somehow left out the scsci driver module.
I believe ubuntu update has clobbered all installs with motherboards like mine.

see this link with a similar problem
[http://www.linuxquestions.org/questions/showthread.php?t=313916](http://www.linuxquestions.org/questions/showthread.php?t=313916)

am I wrong  or/ missing something?

-Rex

---

### Post by FryerFox on 2006-12-14
This may be the case, and it seems that way from what you say.

I also have SATA drives in my core-duo laptop and had the 'savedefault' problem during this last kernel update, but not the other issue you mention. It may have to do with the motherboard, as you say.

---

### Post by clean97gti on 2006-12-14
Hey folks, I had a similar problem when I did the auto update. I dual boot XP and Ubuntu, and have support for linux filesystems installed in WIndows.
At any rate, I opened up my menu.lst and discovered that after the update, it was pointing towards hdb1 when before it was pointing towards hda1 (the proper drive)
I simply edited my menu.lst file and corrected it.

I am happily posting from Ubuntu again. Not sure if this helps anyone but I'll keep poking around.

---

