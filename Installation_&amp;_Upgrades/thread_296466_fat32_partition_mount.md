---
title: "fat32 partition mount"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by loclei on 2006-11-09
hy, i've tried to mount my d: partition but with no success 

so my hdd setup is like this:
1 hdd 40 gb
first partition is the windows partition and it's primary
then the rest of the drive is logical with the following partitions
the linux / 
the swap
and the d: partition 
during the instalation i should've checked the /media/ha5 or 6 i don't remember ...(the d: partition) so now i wouldn't have troubles mounting it

---

### Post by taurus on 2006-11-09
Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.  Once I understand about your harddrive better, then I can show you exactly how to mount our FAT32 with read and write permissions, if you don't want to search the forum...

```
sudo fdisk -l
```

---

### Post by loclei on 2006-11-09
i've searched... but with no good example
so i have 4 partition on my hdd 
the one i want to mount is the last one and is the biggest
also i have windows xp installed - c and d drive..
and linux is just the / "drive" and the swap
the linux partitions are in between the c and d drive..

---

### Post by taurus on 2006-11-09
Can you please paste the output of the command from my previous post?  I just want to make sure I get the partition table right because I don't want to screw anything up on your machine with the instructions...

---

### Post by sh4dow_strid3r on 2006-11-13
taurus..
i'm also facing the same problem. here's the fdisk output of my hd. i dual-booted kubuntu 6.10 with xp and want to access all the drives from kubuntu if possible. kindly help me...

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1657    13309821    7  HPFS/NTFS
/dev/hda2            1658        4864    25760227+   f  W95 Ext'd (LBA)
/dev/hda5            1658        2677     8193118+   b  W95 FAT32
/dev/hda6            2678        3697     8193118+   b  W95 FAT32
/dev/hda7            3698        4219     4192933+  83  Linux
/dev/hda8            4220        4350     1052226   82  Linux swap / Solaris
/dev/hda9            4351        4864     4128673+   b  W95 FAT32

---

### Post by taurus on 2006-11-13
check out this link.  And if you still have questions after reading it, let me know and I can walk you through it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sh4dow_strid3r on 2006-11-14
taurus...
thanks to you i was able to figure out how to mount the drives but as new to this have stumbled upon another one.
i followed the instructions of the link you gave & mounted one of the drives as a folder naming 'songz' & figured that it was mounted on /root/songz but i didn't want it to be there so edited the fstab again to mount it on /home/strider/songz. i thought that just changing the fstab would unmount the previous one but it's still there.
now how can i unmount the previous one from /root ?
another thing that how can i just mount the drive without creating a separate folder for it?
many thanks in advance...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda7 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid $
/dev/hda5 /home/strider/songz vfat iocharset=utf8,umask=000 0 0
/dev/hda8 none swap sw 0 0
/dev/hdd /media/cdrom0 auto user,atime,auto,rw,dev,exec,suid 0 0

---

### Post by taurus on 2006-11-14
If you want to unmount /root/songz, run this command from a terminal.

```
sudo umount /root/songz
```
And if you now want to mount it to /home/strider/songz as in /etc/fstab, then run

```
sudo mount -a
```
If you want to mount a drive, you need to create a mount point for it.  I don't think there is anyway around it.

---

### Post by sh4dow_strid3r on 2006-11-15
well i already managed it myself, anyway thanks a lot for all your help.

---

