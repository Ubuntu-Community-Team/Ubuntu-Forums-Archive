---
title: "upgrade killed my /etc/fstab"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by keine_ahnung on 2008-04-15
Hi All,

For some reason my system doesn't mount my /boot and secondary hard disk (which should be mounted as an subdir in my home dir /home/user/data/) any more. As I left it upgrading 200 packages over night I assume something changed in there automatically. I have an encrypted root partition...

Here's my current fstab, and I wonder why it doesn't work any more:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/volumegroup-root
UUID=ff7aa211-8a9d-4b90-b0d8-6c33e7c87c45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=b37251d6-a3cd-4b55-b4ea-ea97ca5bb904 /boot           ext3    defaults        0       2
# /dev/sda4
UUID=16FC4EA2FC4E7C4D /media/sda4     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=1c4347ec-54e3-4a7b-9edd-8ec16221696c /home/irrlicht/data     ext3    defaults        0       2
# /dev/mapper/volumegroup-swap
UUID=dc32b24b-e6e0-43ac-a891-7e2559527c1b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

Do you see anything that prevents the lines below #/dev/sda1 and #/dev/sdb1 from working?

Thanks!
Daniel

---

### Post by forestpixie on 2008-04-15
No - looks much the same as mine, but there's nothing to compare it to - can you run these in a terminal and post the outputs please
```
sudo blkid
sudo fdisk -l
```

---

### Post by keine_ahnung on 2008-04-15
Here we go:

```
irrlicht@home:~$ sudo blkid
/dev/mapper/volumegroup-swap: TYPE="swap" UUID="dc32b24b-e6e0-43ac-a891-7e2559527c1b"
/dev/mapper/volumegroup-root: UUID="ff7aa211-8a9d-4b90-b0d8-6c33e7c87c45" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda1: UUID="b37251d6-a3cd-4b55-b4ea-ea97ca5bb904" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda2: UUID="8b6546ac-5f79-41c2-ade0-ddd273d8a4f7" TYPE="crypt_LUKS"
/dev/sda4: UUID="16FC4EA2FC4E7C4D" TYPE="ntfs"
/dev/sdb1: UUID="1c4347ec-54e3-4a7b-9edd-8ec16221696c" SEC_TYPE="ext2" TYPE="ext3"
/dev/mapper/sda2_crypt: UUID="uXjF56-jbmC-6p6e-w0xI-1OMQ-y3al-KV095S" TYPE="lvm2pv"
irrlicht@home:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x019c019c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          24      192748+  83  Linux
/dev/sda2              25       15810   126801045   83  Linux
/dev/sda4   *       15811       19456    29286495    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d13df6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9964    80035798+  83  Linux
```

---

### Post by forestpixie on 2008-04-15
No I can't see anything now either - I don't know about encrypted drives or whether anything changed with that. If the update had actually changed the file I would expect there to be a backup generated - probably with a time stamp. 

Which did you get updates for - gutsy, feisty ?

---

### Post by logos34 on 2008-04-15
fdisk isn't showing swap either

---

### Post by keine_ahnung on 2008-04-15
> **forestpixie said:**
> No I can't see anything now either - I don't know about encrypted drives or whether anything changed with that. If the update had actually changed the file I would expect there to be a backup generated - probably with a time stamp. 
irrlicht@home:~$ ll /etc/*fstab*
-rw-r--r-- 1 root root 823 2008-01-07 22:47 /etc/fstab

> **forestpixie said:**
> Which did you get updates for - gutsy, feisty ?
irrlicht@home:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu hardy (development branch)"

> **logos34 said:**
> fdisk isn't showing swap either
Yes, it's encrypted and probably broken too...

Do you all think /dev/sdb1 _should_ be mounted with this /etc/fstab? Then the problem maybe lcated somewhere else, right?

---

### Post by forestpixie on 2008-04-15
Logos might know about this but I'm afraid I don't :( - best I could do is find this in the Hardy forum for you - > My system will no longer boot from encrypted root after upgrading from 7.10.
[http://ubuntuforums.org/showthread.php?t=737348](http://ubuntuforums.org/showthread.php?t=737348)

---

### Post by keine_ahnung on 2008-04-15
It works again! sudo dpkg --configure -a did the trick. I think I missed an error message saying that there were troubles upgrading. And as I did the upgrade overnight I just shut down my PC when I left... Sorry for bothering you, and thank you for your help!

---

### Post by forestpixie on 2008-04-15
Glad you're ok - will have a look at this whole encrypted drive thing though. Can you mark thread solved now.

---

