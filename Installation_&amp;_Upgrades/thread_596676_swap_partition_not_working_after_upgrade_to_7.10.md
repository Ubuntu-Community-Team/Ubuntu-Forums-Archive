---
title: "swap partition not working after upgrade to 7.10"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by ijkn on 2007-10-29
hello, I cannot make the swap partition to work after upgrading to 7.10.:( Does anyone have any ideas?

----------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda4
UUID=c0e755e2-52b4-438c-8315-54f8a4974fa0 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
#UUID=07D6-090C /media/sda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda2
UUID=18C0AD96C0AD7B20 /media/sda2 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda3
#UUID=528C448A8C446B15 /media/sda3 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
#/dev/sda5
/dev/scd0 /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
#/dev/sda5 <mount\040point> swap noauto 0 0
/dev/sda5 none swap sw 0 0

-------------------------------------------------------------------------------------
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-090C" TYPE="vfat"
/dev/sda2: TYPE="ntfs" UUID="18C0AD96C0AD7B20"
/dev/sda3: TYPE="ntfs"
/dev/sda4: UUID="c0e755e2-52b4-438c-8315-54f8a4974fa0" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: TYPE="swap" UUID="f732bd1f-4ad0-4ffc-bef8-9d44de54552a"
/dev/sda6: TYPE="ntfs" UUID="5AFC3432FC340B31"

-------------------------------------------------------------------------------------
Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Utility
/dev/sda2   *           6        3406    27318532+   7  HPFS/NTFS
/dev/sda3            4623        4864     1943865    f  W95 Ext'd (LBA)
/dev/sda4            3407        4622     9767520   83  Linux
/dev/sda5            4623        4688      530113+  82  Linux swap / Solaris
/dev/sda6            4689        4864     1413688+   7  HPFS/NTFS


any help would be much appreciated.:)

---

### Post by taurus on 2007-10-29
Try

```
sudo mkswap /dev/sda5
sudo swapon /dev/sda5
free
```

---

### Post by 5-HT on 2007-10-29
Looks like you swap parition is alright, but your fstab entry is off a bit.
If   'swapon /dev/sda5'  works, modifying your fstab to read:
```
/dev/sda5 swap swap defaults 0 0
``` for your swap partition should  get it to automagically mount properly at boot.

cheers,

---

### Post by ijkn on 2007-10-29
> **taurus said:**
> Try

```
sudo mkswap /dev/sda5
sudo swapon /dev/sda5
free
```

total       used       free     shared    buffers     cached
Mem:       1026312     610748     415564          0      14384     276720
-/+ buffers/cache:     319644     706668
Swap:       530104          0     530104


Thanks taurus for the quick respond. It is working right now. :)

---

### Post by taurus on 2007-10-29
> **5-HT said:**
> In addition to taurus' post, you may also consider modifying your swap entry in your fstab to read:
```
/dev/sda5 swap swap defaults 0 0
```
to get it to automatically mount properly at boot.

cheers,

Actually, what he has is right.

```
/dev/sda5 **none** swap sw 0 0
```

---

### Post by taurus on 2007-10-29
> **ijkn said:**
> total       used       free     shared    buffers     cached
Mem:       1026312     610748     415564          0      14384     276720
-/+ buffers/cache:     319644     706668
Swap:       530104          0     530104

Thanks taurus for the quick respond. It is working right now. :)

Reboot and see if your swap is activated or on now.

```
free
```

---

### Post by ijkn on 2007-10-29
> **taurus said:**
> Reboot and see if your swap is activated or on now.

```
free
```

the swap is activated before and also after rebooting. thanks again. :):)

---

### Post by ijkn on 2007-10-29
> **5-HT said:**
> Looks like you swap parition is alright, but your fstab entry is off a bit.
If   'swapon /dev/sda5'  works, modifying your fstab to read:
```
/dev/sda5 swap swap defaults 0 0
``` for your swap partition should  get it to automagically mount properly at boot.

cheers,

thanks 5-HT too.

I am not sure the difference between "/dev/sda5 none swap sw 0 0" and "/dev/sda5 swap swap defaults 0 0".

Since the original one works after rebooting, so I haven't tried the other one.
Anyway, thanks your help too.:)

---

### Post by A_Lyle on 2008-02-08
Thanks from me too - I was worried I had broken something whilst trying to configure suspend, but it turned out to be those pesky upgrades! Next time I'll double-check the list before installing important system updates, if I want to be able to use my box without interruption!

=D>

---

