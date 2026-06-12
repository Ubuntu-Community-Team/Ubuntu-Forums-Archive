---
title: "Natty: jfs mounting - fstab options problem"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by skasturi on 2011-06-01
Hello,
          I have installed natty using the image ubuntu-11.04-desktop-amd64.iso on my machine through a bootable usb.  I have two hard drives. One 80G(installed natty on this) and another 1TB(jfs). 
 

Following is my /etc/fstab 


```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
 # for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=33fd9bfc-df81-4f40-b456-e61870b8bcaf /               ext4    errors=remount-ro 0       1
 /dev/sdb1       /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=7d861a1b-3553-46c5-87c8-6c0ecb1967b0 /home           ext4    defaults        0       2
 # swap was on /dev/sdb6 during installation
UUID=2d76d66a-bc91-416f-927f-3e86d5ae8b25 none            swap    sw              0       0
# 1TB harddisk
/dev/sda1    /mnt/hadoop    jfs    defaults    0    2
 
```The following is the output of "mount" command after restart with the above fstab. I replaced my username with ####.

```

/dev/sdb5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
 none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
 none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
 none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /mnt/hadoop type jfs (rw)
/dev/sdb1 on /boot type ext4 (rw,commit=0)
/dev/sdb7 on /home type ext4 (rw,commit=0)
 binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/####/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=####)

```> 
/dev/sda1 on /mnt/hadoop type jfs (rw)
 As we can see, though the fs options in the fstab for this partition are "defaults", the jfs partition is not loaded with options user,auto,exec. This is very painful as I have to deal with large file IO in and out of the jfs partition. Added to the problem, it is not allowing me to write to the partition unless I am the super user. 

I tried changing "defaults" to individual options. But it still didn't work. 

I tried to manually mount as follows:
```
sudo mount -t jfs -o rw,exec,user /dev/sda1 /mnt/hadoop
```Even this didn't work. The options set are just "rw". 

> I was previously running hardy and this problem wasn't there. The jfs partition loaded without any hassle with all the default options set. I thought updating to a newer version would be better, but actually its turning out to be worse.  I request someone to please help me out. 

Thank you.

---

