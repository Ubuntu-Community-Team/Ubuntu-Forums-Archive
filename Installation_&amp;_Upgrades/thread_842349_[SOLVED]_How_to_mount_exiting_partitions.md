---
title: "[SOLVED] How to mount exiting partitions?"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by imjscn on 2008-06-27
I cut one big partition into two small partitions, now I want to mount them like this:
Mount  /sda8 as  /var
Mount  /sda9 as /data

How can I achieve this?

(all in one harddisk, no other disk involved)

---

### Post by Pumalite on 2008-06-27
assuming directories /var and /data already exist:
sudo mount -t ext3 /dev/sda8 /var
sudo mount -t ext3 /dev/sda9 /data

---

### Post by ibutho on 2008-06-27
Edit /etc/fstab and do something like
```
/dev/sda8    /var    ext3    defaults    1 1
/dev/sda9    /data   ext3    defaults    1 1

```
You may have to fine tune the fstab options depending on your needs. You can use "mount -a" to mount them after making the changes to your fstab.

---

### Post by imjscn on 2008-06-27
Thanks! Now I mounted the /var by this 

sudo mount -t ext3 /dev/sda8 /var

but, there's no /data directory exist, what to do with the /data?

---

### Post by Pumalite on 2008-06-27
sudo mkdir /data

---

### Post by imjscn on 2008-06-27
sudo mkdir /data

it says: can't mkdir /var/run/sudo: No such file or directory

I shut down the Terminal, still such a message. how can I quit this /var directory?

---

### Post by imjscn on 2008-06-27
Seems something wrong in my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4cd544d3-c87d-4ef6-bd80-58b31d33f4f9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=ace91e21-60da-4c6d-a814-ffc3616501a2 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=eacac28e-428f-4a0e-acd3-76dffe68c825 /home           ext3    relatime        0       2
# /dev/sda8
UUID=effa6039-72a0-406c-98e1-bc9e2ab5bf7c /srv            ext3    relatime        0       2
# /dev/sda6
UUID=a65e392c-7f36-44a3-bfc6-02faa8b621a5 /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=3aa87b31-f289-4552-99fb-20549a551323 /usr            ext3    relatime        0       2
# /dev/sda3
UUID=7876bdf1-e391-4727-9073-efa44c205819 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by imjscn on 2008-06-27
sda8 was mounted as /srv by mistake during installing. I already use Gparted unmounted it and cut it into 2 partition.  fdisk -l shows the cut was successful.
Now, in the fstab, sda8 is still mounted as /srv

what to do now?

---

