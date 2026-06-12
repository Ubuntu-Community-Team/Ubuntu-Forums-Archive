---
title: "noob configures RAID-1 with grub as part of a disk upgrade"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by sheepshearer on 2007-02-20
i have Ubuntu Edgy Eft 6.10 installed on a 40Gb drive (OLD_DISK).

```
/dev/hda1   /home2  19Gb
/dev/hda2   swap     1Gb
/dev/hda3 * /       20Gb
```

* = bootable

a very lazy installation!

i wanted more disk space, and to set up a RAID 1 system and aquired a pair of identical 120Gb disks to play with.

i had 2 options:

1) add in NEW_DISK_1, partition it (properly) rsync everything from OLD_DISK.
   make NEW_DISK_1 bootable
   remove OLD_DISK
   boot from NEW_DISK_1

   i now have more disk space

   add in NEW_DISK_2, partition identically to NEW_DISK_1
   rsync NEW_DISK_1 -> NEW_DISK_2
   change partition types on NEW_DISK_2 to RAID (type 0xfd)
   start up RAID (degraded)
   change partition type on NEW_DISK_1 to RAID (type 0xfd)
   add NEW_DISK_1 to the RAID and let it sync up with NEW_DISK_2

OR...

2) install NEW_DISK_1 and NEW_DISK_2 as the only disks in the system
   run a clean install from the ALTERNATIVE Ubuntu CD image
   partition both disks identically
   set all partitions (apart from swap) as type 0xfd (RAID)
   create my RAID system
   install Ubuntu
   check bootability

   i now have a functional RAID but with none of my original data

   add in OLD_DISK and rsync everything onto the RAIDed partitions.

either option left me with a working and un-touched OLD_DISK that i could always go back to, but i went with option 2 on the basis that it was less prone to me screwing up as i'd be going through the well tested standard install procedure of the ALTERNATE installation disk.

i probably learned less, but system down time is an issue.

step 1)

boot the ALTERNATIVE CD (my cd drive is a slave on /dev/hdd)

partition NEW_DISK_1:

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          16      128488+  fd  Linux raid autodetect
/dev/hda2              17        3663    29294527+  fd  Linux raid autodetect
/dev/hda3            3664       14471    86815260   fd  Linux raid autodetect
/dev/hda4           14472       14593      979965   82  Linux swap / Solaris

/dev/hda1  /boot 128Mb
/dev/hda2  /      30Gb
/dev/hda3  /home  88Gb
/dev/hda4  swap    1Gb
```

and identically for /dev/hdc on the other IDE master

```
/dev/hdc1  /boot 128Mb  
/dev/hdc2  /      30Gb  
/dev/hdc3  /home  88Gb  
/dev/hdc4  swap    1Gb
```

all non-swaps were set to the ext3 file system

create multi disk device /dev/md0 type RAID 1
/dev/md0 = /dev/hda1 + /dev/hdc1

create multi disk device /dev/md0 type RAID 1
/dev/md1 = /dev/hda2 + /dev/hdc2

create multi disk device /dev/md0 type RAID 1
/dev/md2 = /dev/hda3 + /dev/hdc3

install the basic clean system off the CD.

step 2)

add in OLD_DISK on my second IDE slave /dev/hdb 

now here's where the fun started - so one of my first jobs was to make logging in as root legal:

```
$ sudo passwd root
```

for some reason, i couldn't mount /dev/hdb3 (OLD_DISK root mount /) on /mnt. the OS said it was 'busy'. i tried several boots and eventually gave up.

no problem, i **know** /dev/hdb3 is bootable, so i try booting that and then mounting /dev/md1 (my new root) - to do that i'll have to catch grub with an ESC and run from the command line:

```
root (hd1,2)  # /dev/hdb3
kernel /boot/vmlinuz-2.6.20 root=/dev/hdb3 ro single
File not found - WHAT???
initrd /boot/initrd.img-2.6.20
File not found/you need to have a kernel loaded first - HUH???
```

i disconnect both raid drives and boot OLD_DISK off /dev/hdb3 just fine and double-check those ramdisk and kernel paths. all OK!

reconnect the RAIDed drives and try again. this time i systematically go through all partitions:

```
root (hd0,0) # /dev/hda1
root (hd0,1) # /dev/hda2
root (hd0,2) # /dev/hda3

root (hd1,0) # /dev/hdb1
root (hd1,1) # /dev/hdb2
root (hd1,2) # /dev/hdb3

root (hd2,0) # /dev/hdc1
root (hd2,1) # /dev/hdc2
Not valid/does not exist - WTF? this is my mirror to /dev/hda3!
```

... much googling of grub ...

```
# cat /boot/grub/device.map
(hd0)   /dev/hda
(hd1)   /dev/hdc
```

ARRGH! i didn't know about that. kind of explains why hdb and hdc are swapped over though! why can't grub tell me it's read that file in some kind of console message? i wasted hours booting/rebooting and generally fiddling with grub because of this.

i finally boot /dev/hdb3 (grub hd2,2) and mount:
/dev/md0 to /mnt/boot
/dev/md1 to /mnt/root
/dev/md2 to /mnt/home

to keep background tasks to a minimum, i switched to runlevel 1:

init 1

now you can safely rsync -avl /home /mnt/home # OLD_DISK to NEW_DISK_1/2

that's also true of /sbin, /lib, /usr, /bin, /opt

BE VERY CAREFUL with /etc, /var and /boot though

/etc/fstab has UUID disk mounts that will be different for NEW_DISK_1/2
/boot/grub/menu.lst is also important.

you'll need your OLD_DISK /var/lib though and any stuff you may have had in /var/www

finally, i have a RAIDed system that boots and with no loss of any of my original data or apps.

one problem - it only boot from /dev/hda1 - if i disconnect /dev/hda it won't boot. **but we know how to fix that now,** because we know that grub (hd1,0) is really /dev/hdc1 !

```
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```

i then add a listing for hd0 and hd1 in /boot/grub/menu.lst with the second boot option as a fallback:

```
# cat /boot/grub/menu.lst
default         0
fallback        1
timeout         3

title           Ubuntu, kernel 2.6.20
root            (hd0,0)
kernel          /vmlinuz-2.6.20 root=/dev/md1 ro splash
initrd          /initrd.img-2.6.20
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.20 (mirror)
root            (hd1,0)
kernel          /vmlinuz-2.6.20 root=/dev/md1 ro splash
initrd          /initrd.img-2.6.20
quiet
savedefault
boot
```

i hadn't realised that once everything is up and running OK and you start testing by removing one or other disk that you have to add in the out of sync disk manually.

for instance, you remove one disk. boot up. shut down.
add the disk back in, boot up. but it starts with just one disk again so:

```
# mdadm /dev/md0 -a /dev/hda1
# mdadm /dev/md1 -a /dev/hda2
# mdadm /dev/md2 -a /dev/hda3
```

then watch it sync up before your very eyes:

```
# cat /proc/mdstat 
Personalities : [raid1] 
md2 : active raid1 hda3[2] hdc3[1]
      86815168 blocks [2/1] [_U]
        resync=DELAYED
      
md1 : active raid1 hda2[2] hdc2[1]
      29294400 blocks [2/1] [_U]
      [======>..............]  recovery = 33.5% (9834368/29294400) finish=13.0minspeed=24822K/sec
      
md0 : active raid1 hda1[0] hdc1[1]
      128384 blocks [2/2] [UU]
      
unused devices: <none>
```

until finally you're back up to speed...

```
# cat /proc/mdstat 
Personalities : [raid1] 
md2 : active raid1 hda3[0] hdc3[1]
      86815168 blocks [2/2] [UU]
      
md1 : active raid1 hda2[0] hdc2[1]
      29294400 blocks [2/2] [UU]
      
md0 : active raid1 hda1[0] hdc1[1]
      128384 blocks [2/2] [UU]
      
unused devices: <none>
```

i found these links useful:

[http://www.linux-sxs.org/hardware/raid_for_idiots.html](http://www.linux-sxs.org/hardware/raid_for_idiots.html)
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)

good luck

---

### Post by LinuxMum on 2007-02-20
And you call yourself a noob.. lol

---

### Post by sheepshearer on 2007-02-22
> **LinuxMum said:**
> And you call yourself a noob.. lol

well being able to partition a disk, mount an old one and rsync from A to B hardly puts me up there with Ken Thompson, Dennis Ritchie and Linus Torvalds :)

---

