---
title: "GRUB Error On Software RAID system after upgrade"
date: 2007-06-05
forum: Installation &amp; Upgrades
---

### Post by SupaRice on 2007-06-05
Hi,

I recently tried to upgrade...

Now Grub is giving me "Error 2", which after reading means that it doesn't like the drive letter that it has in the config.  I have a somewhat strange setup though.  I have 4 drives, acting as two seperate software RAIDs.  The first pair of drives are partitioned such that the root is on one, and the second has my swap partition.  The rest of those two drives are put into a RAID0.  The other two drives (SATA) are put into a seperate RAID1.  I know enough to be dangerous about linux (obviously :lol:), and don't know what to do to fix the problem.

This is the only thing I know to include in my post, if there is anything else that will be helpful info let me know.

I got this from booting to the live CD:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12158    97659103+  fd  Linux raid autodetect
/dev/hda2           12159       14593    19559137+  83  Linux

Disk /dev/hdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1         365     2931831   82  Linux swap / Solaris
/dev/hdc2             366       12523    97659135   fd  Linux raid autodetect
/dev/hdc3           12524       14946    19462747+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

```

---

### Post by SupaRice on 2007-06-07
*bump*

Anyone?  Buller?

---

### Post by SupaRice on 2007-06-07
So I've been trying the instructions in this thread:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

But it doesn't work for me.  Specifically when I chroot into my drive I get an error

```

root@ubuntu:/home/ubuntu# mkdir /mnt/root
root@ubuntu:/home/ubuntu# mount -t ext3 /dev/hda2 /mnt/root/
root@ubuntu:/home/ubuntu# mount -t proc none /mnt/root/proc
root@ubuntu:/home/ubuntu# mount -o bind /dev /mnt/root/dev
root@ubuntu:/home/ubuntu# chroot /mnt/root /bin/bash
[COLOR="Red"]bash: groups: command not found
bash: dircolors: command not found
[/COLOR]root@ubuntu:/# 




grub> find /boot/grub/stage1

Error 15: File not found


root@ubuntu:/# ls -la /
total 124
drwxr-xr-x  21 root root  4096 Jun  7 18:22 .
drwxr-xr-x  21 root root  4096 Jun  7 18:22 ..
-rw-------   1 root root  1024 Mar  6 14:57 .rnd
[COLOR="Red"]?---------   ? ?    ?        ?            ? /boot[/COLOR]


```

I think this might have something to do with me installing /boot on a different partition of another drive, but I can't remember if that's how I did it.

I also get this problem:
```

root@ubuntu:/# grub-install /dev/hda
mkdir: cannot create directory `/boot': File exists

```

Help please...

---

### Post by SupaRice on 2007-06-10
Can anyone help me figure out how to mount my /boot?

I know my system has a strange drive arrangement, but I built it with the software RAID this way to avoid losing data.  Is there a way to bring up the RAID and mount it in the live CD?  That way I could at least get my data off the system before reloading.

---

### Post by SupaRice on 2007-06-11
*bump*

Anyone?

---

### Post by skoenman on 2007-08-22
Hey there i had the same problem as you .... my setup was as follows

/boot raid 1
/        raid0
swap raid 1
/var raid1

you need to split the drives so that the partitions are all the same ...thats the only way i could get it working.if you have any questions you can let me know on [email]skoenman@officetechsupplies.com[/email].

---

