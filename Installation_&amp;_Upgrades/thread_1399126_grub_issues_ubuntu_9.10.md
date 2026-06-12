---
title: "grub issues ubuntu 9.10"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by ambiogas on 2010-02-05
I recently installed ubuntu 9.10 32 bit using live cd onto a recently new Dell machine with windows7.

Everything was fine for a couple of weeks, but last night I got the error:

Grub loading.
the symbol `    fil?
not found
Aborted

Looking into the forums, I see that maybe I need to re-install grub 2.  When I started probing using fdisk, I saw that the boot partition was my windows partition.  So, I thought I would ask to find out if this looks right before I start making things worse:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca6eeadf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1918       41471   317711636    7  HPFS/NTFS
/dev/sda4           41472       77825   292013505    5  Extended
/dev/sda5           41472       76605   282213823+  83  Linux
/dev/sda6           76606       77825     9799618+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.6G   49M  1.6G   3% /
udev         tmpfs    1.6G  280K  1.6G   1% /dev
/dev/sr0   iso9660    690M  690M     0 100% /cdrom
/dev/loop0
          squashfs    668M  668M     0 100% /rofs
none         tmpfs    1.6G  100K  1.6G   1% /dev/shm
tmpfs        tmpfs    1.6G   20K  1.6G   1% /tmp
none         tmpfs    1.6G   88K  1.6G   1% /var/run
none         tmpfs    1.6G     0  1.6G   0% /var/lock
none         tmpfs    1.6G     0  1.6G   0% /lib/init/rw
ubuntu@ubuntu:~$ 

If the boot partition is wrong, I have no idea how this could have happened...?

Thanks in advance for any advice.
Andy

---

