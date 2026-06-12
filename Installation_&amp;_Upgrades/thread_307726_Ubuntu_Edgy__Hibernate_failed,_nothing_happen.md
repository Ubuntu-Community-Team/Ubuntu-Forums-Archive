---
title: "Ubuntu Edgy : Hibernate failed, nothing happen"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by tomcheng76 on 2006-11-27
Hi everyone
When i press hibernate, it will shutdown.
However, if i power on the pc again. It is just the same as normal startup
,except in the fcsk stage. it shows last block write in the furture, fixed (due to abnormal shutdown ?)
Is it due to my swap which is a LVM partition?
i have read [here]("http://ubuntuforums.org/showthread.php?p=1683612") and [here]("http://www.columbia.edu/~ariel/acpi/acpi_howto.txt")
but i still not sure how to do
my fstab: 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9 -- converted during upgrade to edgy
UUID=e7db6e08-4d90-4dc3-87cb-498e425e02bb / ext3 defaults,errors=remount-ro 0 1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,ro,umask=222,noauto,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,ro,umask=222,noauto,gid=46 0       1
# /dev/hda3 -- converted during upgrade to edgy
UUID=9b643074-0359-4cc9-92ab-fb7cab2d9dee /media/Text ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=ACC02009C01FD902 /media/hda6 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
# /dev/hda7 -- converted during upgrade to edgy
UUID=185D-2502 /media/hda7 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda8 -- converted during upgrade to edgy
UUID=98FC471CFC46F452 /media/hda8 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
# /dev/hdb1 -- converted during upgrade to edgy
UUID=3E78D44878D40097 /media/hdb1 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
/dev/mapper/VolGroup00-LogVol00 /media/LinuxData ext3    defaults        0       2
/dev/mapper/VolGroup00-LogVol01 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda10	/media/hda10 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1
/dev/hda11	/media/hda11 ntfs defaults,nls=utf8,ro,umask=222,gid=46 0 1

```

any help would be appreciate :-D

---

### Post by tomcheng76 on 2006-11-27
after i type swapoff -va, it seems that i dont have any swap
and swapon have error
swapon: /dev/mapper/VolGroup00-LogVol01: Invalid argument
even i restart the pc....
Mem:    515888k total,   468556k used,    47332k free,    14444k buffers
Swap:        0k total,        0k used,        0k free,   246200k cached

---

### Post by tomcheng76 on 2006-11-27
Bump
[[IMG]http://img224.imageshack.us/img224/5830/evmsvs6.th.png[/IMG]](http://img224.imageshack.us/my.php?image=evmsvs6.png)

---

### Post by tomcheng76 on 2006-11-27
I solved the swap problem.
By using mkswap <device>
Remaining problem - Hibernate

---

