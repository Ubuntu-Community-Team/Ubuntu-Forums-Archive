---
title: "Help with upgrade to 9.10"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by Scoff on 2010-04-08
Hey, I'm currently running on 9.04 32bit, and I want to know if there's a way to upgrade to 9.10 64bit.

That's 'bout it, thanks in advance :D

---

### Post by lisati on 2010-04-08
Is your /home directory on its own partition?

---

### Post by dominiquec on 2010-04-08
I don't believe you can switch from 32-bit to 64-bit via upgrade.  You'll need to reinstall.

---

### Post by Scoff on 2010-04-08
> **lisati said:**
> Is your /home directory on its own partition?

Errr... how do i check that?

---

### Post by whoop on 2010-04-08
> **Scoff said:**
> Errr... how do i check that?

```

cat /etc/fstab

```

---

### Post by Scoff on 2010-04-08
> **whoop said:**
> ```

cat /etc/fstab

```
```

scoff@scoff-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3e48588e-9d99-4315-951f-3314d38ab302 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a5c53054-fdc7-43f2-be97-7176858fbf16 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by oldfred on 2010-04-08
How much space do you have on your hard drive?

Further discussion on 32 to 64.
[http://ubuntuforums.org/showthread.php?t=1448571&highlight=home](http://ubuntuforums.org/showthread.php?t=1448571&highlight=home)

Moving /home.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

If you have room it may be worthwhile to just add another 20GB partition for your 64 bit install and then after you have copied everything you want use the existing partition as a data partition.

---

### Post by Scoff on 2010-04-09
Thank you oldfred :D *goes and clicks solved*

---

