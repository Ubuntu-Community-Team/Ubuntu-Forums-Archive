---
title: "can't mount hard drive"
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by veritas366 on 2005-04-20
This is a repeat of some things in another thread, but I ended up wandering so far afield that I wanted to start fresh.  I installed ubuntu, on my hda even knowing that it wanted to install a new grub and that it couldnt' recognize my fc3 os on the hdb drive.  I figured I would just hop over to my grub.conf file from fc3 and paste it into the new grub file.  Well, now I can't access my hdb2 and I'm sure I'm missing something.  I should mention that I also have a Windows xp on that drive, but I don't think that's relevant.  It does pop up in the grub menu, however.


hdb2 (or any hdb) is not listed as one of the mounted devices when I run the "mount" command.

When I try to mount it (specifically hdb2, where fc3 lives) into a directory I created called /mnt/fc3 it says that "/dev/hdb2 is already mounted or /mnt/fc3 is busy. If I try to unmount it...it says...you guessed it...device not mounted.

I tried the same thing by adding it to the fstab with this:


> /dev/hdb2 /mnt/fc3 ext3 defaults 0 2


Then I hit "mount -a" and it once again told me that /dev/hdb2 was already busy.

I know I'm missing something here. If I look in the devices, I see all the hdb drives there, but I can't open them from there.

I rebooted with the new fstab and I got a message during startup ( I'm not sure where the boot log is in Ubunut) about needing to run fsck manually.  I just control-d'ed past it.  

Why can't I access my other hard drive?  What evils in my past life am I paying for now?  :-x 

Please help...it's the last thing I need to do to get all this set up!

---

### Post by pietro_spina on 2005-04-20
being sure your mount point exists of course

```
$ sudo mkdir /mnt/fc3
```

did you try 

```
$ mount -t ext3 /dev/hdb2 /mnt/fc3
and this...
$ cat /proc/devices
might be helpful
```
It shows me (among other things) that I have 2 ide drives... one referred to as ide0 and the other as ide1...

But on the other hand I could be entirely wrong...

---

### Post by veritas366 on 2005-04-20
Here is what happens with the mount command as well as the cat.  Also results of "mount" and results of fdisk -l  

> 
ty@ubuntu:~ $ sudo mount -t ext3 /dev/hdb2 /mnt/fc3
Password:
mount: /dev/hdb2 already mounted or /mnt/fc3 busy
ty@ubuntu:~ $ cat /proc/devices
Character devices:
  1 mem
  2 pty
  3 ttyp
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  6 lp
  7 vcs
 10 misc
 13 input
 14 sound
 29 fb
116 alsa
128 ptm
136 pts
180 usb
254 devfs

Block devices:
  1 ramdisk
  2 fd
  3 ide0

  9 md
 22 ide1
253 mdp
254 device-mapper
ty@ubuntu:~ $ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
ty@ubuntu:~ $ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       20321    10241406    7  HPFS/NTFS
/dev/hda2           20321       42625    11241531+   f  W95 Ext'd (LBA)
/dev/hda3           42626       77545    17599680   83  Linux
/dev/hda5           20321       40641    10241406    b  W95 FAT32
/dev/hda6           40642       41633      499936+  82  Linux swap
/dev/hda7           41634       42625      499936+  82  Linux swap

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14       14593   117113850   83  Linux

---

### Post by veritas366 on 2005-04-20
I want to add that this may be a problem with the fact that fc3 by default sets up files with the logical volume manager.  No one in the universe, apparently, has any idea how to work with these.  I see that in /dev there is a file for volgroup00 and inside that is a link to /dev/mapper/volgroup00-logvol01.  This is the correct information but I couldn't mount it either.  No one at the Fedora forum seems to get logical volumes which is odd, because FC3 uses them by default.  Never again, might I add, will I partition with lvm.  The other issue I had was that I couldnt' figure out how to shrink it so even with over 100 g of space on my other harddrive, I couldn't put Ubuntu there, which is what I wanted to do in the first place.

---

### Post by pietro_spina on 2005-04-20
sorry man, I never got along with RedHat/FedoraCore. I've only used Debian based. (with a short diversion into gentoo land...)way beyond my abilities

p

---

### Post by veritas366 on 2005-04-20
I just realized i CAN mount the /boot partition on the hdb hard drive.  That being so, can someone tell me how to take what I find there and create appropriate entries in grub to start up fc3?

---

### Post by veritas366 on 2005-04-21
Well, not like people are rushing to help with this post (it was an fc3 problem after all.)  Just reporting that I got it sorted out.  For anyone arriving here by searching...Definitely go into your bios and turn the hard disk from "auto" to LBA...that was a simple fix to Windows refusing to boot.  If it looks like Ubuntu isn't recognizing another LInux distro and will omit it from your grub menu...and you still want to try it, back out of the install and go get the info from you grub menu.  Two places so far that I've seen that it lives:  in fc3 it is /etc/menu.lst and for Ubuntu it (more logically) is in /boot/grub/menu.lst.  It's really a simple matter of adding those entries to Ubuntu's grub menu to get your other distro booting again.   :grin:   (I swear, I learn much more by breaking things than I do when things work right.)

---

