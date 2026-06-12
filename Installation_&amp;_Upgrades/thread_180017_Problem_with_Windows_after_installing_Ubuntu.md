---
title: "Problem with Windows after installing Ubuntu"
date: 2006-05-21
forum: Installation &amp; Upgrades
---

### Post by Why Wont You on 2006-05-21
Hi, I am new to linux and decided I would try with Ubuntu (I have previously tried Mandrake but it did not go so well). I used the free space that I created for Mandrake so the Windows partition has not been changed. The install was fine, it detected that Windows was installed and is an option on the boot loader. However, when I try to start Windows XP Home I get a black screen (which is right because I have the graphic startup disabled) but there is no way it should take 10 minutes to start up.

I have been talking to a friend who knows a lot more about linux than me (but with another distro) and he told me a few commands. The results of which are as follows:

```
matt@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         319     2562336   12  Compaq diagnostics
/dev/hda2   *         320        7069    54219375    7  HPFS/NTFS
/dev/hda3            7070        9616    20458777+  83  Linux
/dev/hda4            9617        9729      907672+   5  Extended
/dev/hda5            9617        9729      907641   82  Linux swap / Solaris

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19929   160079661    7  HPFS/NTFS
matt@ubuntu:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-k7/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
```

hda1 is a reload disk for Windows which does not work ether (goes ultimately to a blue screen of death). hda2 is Windows and I am sure you know what the rest are.

This is my boot/grub/menu.lst file

```

default		0

timeout		10


title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-k7
boot

title		Ubuntu, kernel 2.6.12-9-k7 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-k7 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-k7 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-k7 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-k7
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot


title		Other operating systems:
root


title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by glotz on 2006-05-21
I'm double booting with win 2000 and sometimes when I boot windoze, it takes for ever and then complains that there's no swap file. (I have a 400 megs swap file. It's located on a fat32 disk I share between the OSes. Resetting swap file size and then rebooting ](*,) solves the issue for me.) Dunno if this is related but sympthoms sounded similar.

---

### Post by Ocxic on 2006-05-21
just for the hell of it, cause I'm not sure if this will work, try:

```

title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
boot


title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
boot


```

---

