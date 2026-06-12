---
title: "How to unmount &quot;/home&quot; from external hard disk"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by premchand21 on 2011-09-12
Hello gurus,
I installed a new external hard drive as I wanted to mount the new hard drive to "/var/www" folder. But unfortunately I mounted to "/home" by mistake while testing something. I am banging my head to unmount the new hard drive from "/home" but it is not allowing me to do so. I also tried logging in as root and tried to unmont but I had no success.
I really appreciate if somebody could help me unmount "/home" from my the newly installed hard drive.

FYI: The main hard drive is mounted to "/" folder and the newly installed hard disk is installed to "/home" directory.

Thanks in advance!!!

---

### Post by sanderd17 on 2011-09-12
Use a live CD.

How did you mount to /home? by editing the fstab file?

---

### Post by premchand21 on 2011-09-12
> **sanderd17 said:**
> Use a live CD.

How did you mount to /home? by editing the fstab file?

I mounted it by using "mount /dev/sdb2 /home"
I did not change anything in fstab file.

---

### Post by sanderd17 on 2011-09-12
> **premchand21 said:**
> I mounted it by using "mount /dev/sdb2 /home"
I did not change anything in fstab file.

If you reboot it should be ok.

---

### Post by premchand21 on 2011-09-12
> **sanderd17 said:**
> If you reboot it should be ok.
I already rebooted it couple of times and the new hard drive is mounted to "/home" by default after the reboot.  :(

---

### Post by sanderd17 on 2011-09-12
can you give the output of the following commands?
```

mount
cat /etc/fstab
cat /etc/mtab

```

(please put them between CODE tags)

---

### Post by premchand21 on 2011-09-12
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c40cdc31-3637-4861-8e12-917b74e146be /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=0f340538-43f2-40b6-991b-967aced850ed /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=792982d5-0d91-4aca-ac40-4501b2cbddc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1        /mnt/data1      ext3    defaults        0       2
/dev/sda2        /mnt/data2      ext3    defaults        0       2
/dev/sdb2        /mnt/webtools   ext3    defaults 0   0
//mvfil002/groups6/WRTools /mnt/wrttools smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

```


```
cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb2 /home ext4 rw 0 0
/dev/sda1 /mnt/data1 ext3 rw 0 0
/dev/sda2 /mnt/data2 ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```

---

### Post by sanderd17 on 2011-09-12
> **premchand21 said:**
> ```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=c40cdc31-3637-4861-8e12-917b74e146be /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=0f340538-43f2-40b6-991b-967aced850ed /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=792982d5-0d91-4aca-ac40-4501b2cbddc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1        /mnt/data1      ext3    defaults        0       2
/dev/sda2        /mnt/data2      ext3    defaults        0       2
/dev/sdb2        /mnt/webtools   ext3    defaults 0   0
//mvfil002/groups6/WRTools /mnt/wrttools smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0

```


```
cat /etc/mtab
/dev/sdb1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/dev/sdb2 /home ext4 rw 0 0
/dev/sda1 /mnt/data1 ext3 rw 0 0
/dev/sda2 /mnt/data2 ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```

you forgot the output of the command "mount" (I need this too). But anyway, there are some weird things here. Summary of your files:

```

# / was on /dev/sda1 during installation
and
/dev/sda1        /mnt/data1      ext3    defaults        0       2

# /home was on /dev/sda2 during installation
and
/dev/sda2        /mnt/data2      ext3    defaults        0       2

/dev/sdb2        /mnt/webtools   ext3    defaults 0   0
and
/dev/sdb2 /home ext4 rw 0 0

```

What partition do you want to have where?

---

### Post by premchand21 on 2011-09-12
Ohh here is the output for mount
```
mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb2 on /home type ext4 (rw)
/dev/sda1 on /mnt/data1 type ext3 (rw)
/dev/sda2 on /mnt/data2 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

Here is the output for df just in case
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1             24027628  21780516   1026576  96% /
udev                   1676736       316   1676420   1% /dev
none                   1676736      1196   1675540   1% /dev/shm
none                   1676736       148   1676588   1% /var/run
none                   1676736         0   1676736   0% /var/lock
none                   1676736         0   1676736   0% /lib/init/rw
/dev/sdb2             96124936  36505628  54736352  41% /home
/dev/sda1            480618344  14591324 441612960   4% /mnt/data1
/dev/sda2            961529388  16216192 896470332   2% /mnt/data2

```

I want sdb2  (which is the new hard drive) to point to /var/www

Thanks

---

### Post by sanderd17 on 2011-09-12
I get the problem. In you fstab file, it says:

```

# / was on /dev/sda1 during installation
UUID=c40cdc31-3637-4861-8e12-917b74e146be /               ext4    errors=remount-ro 0  

```

And that doesn't get overwritten anywhere, and still mtab says your root directory is /dev/sdb1, and not sda1. Since you can't change partition numbers without problems, that means you have switched disks. So sda has become sdb. The UUID stays the same, but the order of a and b have changed.

That also means that this line
```

# /home was on /dev/sda2 during installation
UUID=0f340538-43f2-40b6-991b-967aced850ed /home           ext4    defaults        0       2

```
says that sdb2 is mounted to /home.

Now, before you go any further, are you sure you want to unmount sdb2 from /home? Since it has been that way since you installed it.

I think you want sda2 mounted to /home.


Try booting up a live CD and see what partition you want where (draw a schema on a sheet of paper). See which files are on what partition.

---

### Post by premchand21 on 2011-09-12
Yes I want to unmount sdb2 from /home as my purpose of installing a new hard drive is to mount it to /var/www

I am not aware of live CD :( 
Could you please help to unmount it with some command in terminal

---

### Post by sanderd17 on 2011-09-13
> **premchand21 said:**
> Yes I want to unmount sdb2 from /home as my purpose of installing a new hard drive is to mount it to /var/www

I am not aware of live CD :( 
Could you please help to unmount it with some command in terminal

sdb is your old hard drive. You switched the order of the hard drives.

So you probably want sda2 mounted to your /home directory.

Now, if you want to do that, remove the lines

```

/dev/sda2        /mnt/data2      ext3    defaults        0       2
/dev/sdb2        /mnt/webtools   ext3    defaults 0   0

```

from your fstab file, and mount sda2 as /var/www (after you moved everything from /var/www to that partition).

---

### Post by fdrake on 2011-09-13
from what i understand it looks like you have 2 partitions (/dev/sda2 and /dev/sdb2) mounted both in the same mount point (/home)

if you do sudo umount /home you will unmount your user account too so it will give you some error messages like device is busy. try instead this:

```

sudo umount /dev/sdb2
sudo mount /dev/sdb2 /mnt/webtools

```

if it shows any errors copy and paste here.

---

