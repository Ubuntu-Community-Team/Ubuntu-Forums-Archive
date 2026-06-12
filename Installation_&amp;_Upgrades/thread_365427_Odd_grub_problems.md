---
title: "Odd grub problems"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by BatteryCell on 2007-02-19
Ok so yesterday I totally hosed my a64 system, so I figured eh ... I always wanted i386 anyways, so I stuck in a 6.10 cd and reformatted.  Everything with the install goes fine.  However, when I go to boot grub loads but every time I try to boot one of the options I get:
```
Error 22: No such partition
```
and if I try booting windows:
```
Error 13: Invalid or unsupported executable format
```

So I'm going like ... crap ... so I go back into the livecd and pick "Boot from First Hard disc" and I get grub but this time it boots fine ..... :-|

Attached are my menu.lst, and device.map. 

Heres the fdisk -l:
```
fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       19140    19535040   83  Linux
/dev/sda3           19141       19457     2546302+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        3649    29310561   83  Linux

```

/dev/sda2 is the root directory (/)

I can boot to the livecd every time but if someone could tell me how to fix this it would be greatly appreciated. :-)

---

### Post by Dylnuge on 2007-02-19
Sounds like a problem in your fstab file.

Can you post the contents of /etc/fstab please?

Wait a minute, what is your boot partition? These are referencing /dev/sda2 as the partition /boot is mounting too, is this correct? If so, you should separate your boot and root partitions.

Experimenting will not be a a problem: we can access your drive from the LiveCD environment through a few basic mounting tricks.

---

### Post by BatteryCell on 2007-02-19
Fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=9e17bbd9-46ea-4172-b7ce-4bf94c07327d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc1
UUID=251071b6-528f-419c-909d-6c0cb99ad34d /data1     ext3    defaults        0       2
# /dev/sda1
UUID=E6E857CBE857991F /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=2606a28d-c584-49bc-a788-18477667e422 /beast     ext3    defaults        0       2
# /dev/sda3
/dev/sda3 none  swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```
Note that I changed the swap back to a non UUID because swap wasn't working.

Um when it comes to grub and booting I really am quite clueless :-/  Sorry

All I know is that grub was installed to hd(0,0) which google tells me is the mbr

And by I can boot to the livecd I meant I can boot through the livecd to my hard-drive just not staight to my hard-drive... 

Thanks for the quick reply :-)

---

### Post by Dylnuge on 2007-02-19
I understand what you ment by booting through the LiveCD. I mean that if that fails because we were wrong about the /boot partition, then we can fix it by booting to the LiveCD, and not through it.

Now, what realy throughs me off is this line in your fstab:
```
UUID=2606a28d-c584-49bc-a788-18477667e422 /beast     ext3    defaults        0       2
```

It looks like sdb1 is mounting to /beast. Sounds weird, but I need to know if that even exists. Post the results of a ls / command and an ls /beast command.

I don't see a boot partition. Looks like that could be the problem.

Post those results and I will take a look at it. Worst case scenario we can save all of your data to a CD or Jump Drive.

After running those commands I want you to run the following:
```
 umount /dev/sdb1
mkdir /media/unknown
mount /dev/sdb1 /media/unknown
ls /media/unknown 
```

Please note that the command is Umount and not UNmount. (all lower case, though).

Awaiting the results.

---

### Post by BatteryCell on 2007-02-19
Lol I'm sorry /beast and /data1 both exist I created them specifically for those two hard-drives (beast is just an inside joke ...).  Anyways ls /:
```

# ls /
beast  boot   data1  etc   initrd      initrd.img.old  lost+found  mnt  proc  sbin  sys  usr  vmlinuz
bin    cdrom  dev    home  initrd.img  lib             media       opt  root  srv   tmp  var  vmlinuz.old


```

and the beast directory (the 500 gig hd)
```

# ls /beast
BackUpForReFormat  DVDs  kubuntu-6.10-desktop-i386.iso  lost+found  MISCMusic  Music  StarWarsIIBloopers  try  unnamed  UNPLAYABLE  Videos

```

---

### Post by Dylnuge on 2007-02-19
Ok then. It would seem that you do not have a special partition for /boot. If possible, please create one. I will walk you through making it a boot partition in the fstab file.

Also, you should probably mount your hard drives in the /media folder, i.e, /media/beast, instead of in the root.

---

### Post by BatteryCell on 2007-02-21
Alright I fixed it :-D  Aparently, the device.map was wrong and sda was not hd1 it was hd0 (at least in bios), so I just change all the (hd1,1) in menu.lst to 0,1 and change (hd1,0) to (hd0,0) and take away the maps.  Now everything boots fine.

Thanks alot :-D

---

