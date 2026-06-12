---
title: "[SOLVED] HDDs"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Rwild on 2008-01-14
Hi Ubuntu enthusiasts!

  I am looking to make the switch back to linux.  Previously, I use Linspire 5.0.  I didn't really do anything with it.  My friend configured it for me and I never "played" with it so I really am not too savvy.  I am looking to go back to linux due to the incompatibility of hardware with Vista. 

  I recently purchased a new SATA drive for my system and cannot get it to function properly in Vista.  I can however, pick it up in GNOME Partitioner in Ubuntu's live disk.  I am running the live disk right now, and the only drive I can browse the files of is the external drive I have connected via USB 2.0.  

  So, my question is, if I can view all 3 of my internal drives in the Partitioner, will I be able to view them once Ubuntu is installed after "finding them"?  Can I try finding them on the live disk now?

---

### Post by meindian523 on 2008-01-14
Yes.
To "find" your drives in the Live disk,just do ```
sudo mount -a
``` in Applications>Accessories>>Terminal

---

### Post by meindian523 on 2008-01-14
That will mount "all" your partitions on all your HDDs and you will get icons for each of them on your desktop.

---

### Post by Rwild on 2008-01-14
OK.  Thank you for the quick response!

This can only be done once Ubuntu is fully installed correct?  As when I do it, nothing happens while running the live disk.

---

### Post by Rwild on 2008-01-14
Shoot, I know how to do this, I think...
What is the root's password on the live disk?  Anyone know?

---

### Post by meindian523 on 2008-01-14
You don't need a root password for the Live CD.
Just login as root in the terminal with ```
sudo -i
```

---

### Post by Rwild on 2008-01-14
Okay.  I can login as root now.  Thank you.  

However, I must be doing something wrong.  I have attempted a few different variants of what you suggested I do and I get nothing.... for the most part.  Does this code make any sense???

> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# sudo mount -a
root@ubuntu:~# mount -a
root@ubuntu:~# mount
unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/WILD type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)


That smiley is really supposed to be 8 )  This is starting to turn out to be more of a hardware issue than anything... Sorry for the wrong forum.  I just want to make sure I can view all of my devices before I wipe out Vista.

---

### Post by meindian523 on 2008-01-14
Please post ```
fdisk -l
``` from your root terminal.

---

### Post by Rwild on 2008-01-14
> root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       60801   488384001    5  Extended
/dev/sda5               1       60801   488383969+   7  HPFS/NTFS

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19930   160083968    7  HPFS/NTFS


I unplugged the third IDE drive in hopes that would make a difference, but no.  So, here it is with two for you while I reconnect and reboot.

---

### Post by meindian523 on 2008-01-14
Well,both your drives are being recognized.Which Ubuntu version are you trying to install?

---

### Post by Rwild on 2008-01-14
This disk is 6.10.  I will probably download the most recent if I can get this to work now...  


The other day, I formatted my 500 gig and after teh format, all of the drives appeared on teh system.  Now I have data on the 500 because once it appeared, I transfered some files to it.

> root@ubuntu:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       60801   488384001    5  Extended
/dev/sda5               1       60801   488383969+   7  HPFS/NTFS

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19930   160083968    7  HPFS/NTFS

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19930   160084940+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    b  W95 FAT32


---

### Post by Rwild on 2008-01-14
I remember I had to do something with "fstab" to get my drives to mount is Linspire...  Any idea of that that could be?

---

### Post by meindian523 on 2008-01-14
Ah,that's why.All your partitions are in the NTFS file system and therefore 6.10 cannot read/write to them because it doesn't have the necessary drivers.If they had been FAT/FAT32 there would have been no problem.The latest version(7.10) has those drivers by default,so there would be no problem with the latest version.In 6.10,after you install you can install the ntfs drivers to access,read and write to your NTFS partitions by using 

```
sudo apt-get install ntfs-3g
```

---

### Post by Rwild on 2008-01-14
Okay... I am going to download and see what we can do on the live disk.  Thanks for you help and hopefully you'll be around in a half an hour or so. :D

Wow.  You are so very right... Ubuntu sees the external as it is FAT.

---

### Post by meindian523 on 2008-01-14
Probably not. :(It's night here and I got to sleep for college tomorrow.But there will be plenty of other helpful personalities to guide you.

See this for a good guide to installing:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by Rwild on 2008-01-14
Up and running the live disk for 7.10.  Everything was found on boot-up.  Thanks so much for your help!  I am making room on my boot drive and am going to dual boot Ubuntu and Vista as I need Windows for a few classes.  But, if Wine works well maybe I can go strictly Ubuntu. ;)

---

### Post by meindian523 on 2008-01-14
cool,please mark the thread as solved.

---

