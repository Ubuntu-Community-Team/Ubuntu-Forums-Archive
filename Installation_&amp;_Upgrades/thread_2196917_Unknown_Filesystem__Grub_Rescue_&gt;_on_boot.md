---
title: "Unknown Filesystem : Grub Rescue &gt; on boot"
date: 2014-01-01
forum: Installation &amp; Upgrades
---

### Post by Darce on 2014-01-01
Hi Guys,

Booted to my laptop today to find the boot fail with the following prompt :
------
Unknown filesystem :
GRUB rescue >
-----

My system is dual boot Win7 and Ubuntu 12.10 (?) and has been for quite some time. I'm not sure what has bought on the error, an update in either Win or Ubuntu ? Anyhoo...

Some Googling pointed me to the Boot-Repair-disk which I have burnt and run using the 'Fix Most Common Problems' button and also 'Advanced' with fix filesystem errors selected.
Both fixes failed with the laptop still booting to the above prompt.


Dump of Boot-Repair log is at
[http://paste.ubuntu.com/6673070/](http://paste.ubuntu.com/6673070/)


Any and all help appreciated

---

### Post by Darce on 2014-01-01
I've tried to boot manually from the rescue prompt without success using
```

set root=(hd0,5)
set prefix=(hd0,5)/boot/grub
insmod normal

```

which after a 5 second pause, again brings up 'Unknown filesystem'.

Should I have posted this in the 'Boot-Rescue' thread ?

As a last resort I've started to download the 13.10 iso :/

---

### Post by fantab on 2014-01-01
```
fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x38d9e056

Device Boot      Start         End      Blocks   Id  System
/dev/sda1              [COLOR=#0000ff]63[/COLOR]       80324       40131   de  Dell Utility
[COLOR=#b22222]Partition 1 does not start on physical sector boundary[/COLOR].
/dev/sda2   *       81920    29044735    14481408    7  HPFS/NTFS/exFAT
/dev/sda3        29044736   418846719   194900992    7  HPFS/NTFS/exFAT
/dev/sda4       [COLOR=#0000ff]418848766[/COLOR]  1953523711   767337473    5  Extended
[COLOR=#b22222]Partition 4 does not start on physical sector boundary[/COLOR].
/dev/sda5       418848768  1941209087   761180160   83  Linux
/dev/sda6      1941211136  1953523711     6156288   82  Linux swap / Solaris
```

The numbers in '[COLOR=#0000ff]blue[/COLOR]' should be divisible by 8, or they should be multiples of 8 only.
You should adjust the above numbers to be multiples of 8. '[Fixparts]("http://www.rodsbooks.com/fixparts/")' Utility will help you. 
If it doesn't then you will have to change them manually, for windows partition USE any bootable 'Partition management' tool and for Linux use Gparted.
Run 'Boot-Repair' again and see if it helps. 
NOTE: USE your 12.10 DVD to run 'Boot-Repair'. If the version of GRUB is not same on your 'repair disc' and 12.10 then there could be issues.

Also you have accumulated more than 20 unused kernels, you may want to clean up your system later.

---

