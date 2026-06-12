---
title: "Vaio CD/dvd drive not working after install"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by bharath82in on 2012-03-15
Hi,

Newbie to ubuntu/linux...decided to get rid of windows on my sony and install 10.10...

Sony Vaio VGN-NR498E

After the install, my cd-dvd drive is not working. I do see the drive under "Computer" but it does not read CDs/DVDs...searched around in google and did my own troubleshooting without luck. 

Need help....

brt@brt-laptop:~$ su - root
Password: 
root@brt-laptop:~# mount /dev/cdrom /mnt/cdrom
mount: mount point /mnt/cdrom does not exist
root@brt-laptop:~# mkdir -p /mnt/cdrom
root@brt-laptop:~# mount -t iso9660 /dev/cdrom /mnt/cdrom
mount: no medium found on /dev/sr0
root@brt-laptop:~# sudo mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brt)
root@brt-laptop:~# 
root@brt-laptop:~# cat /etc/fstab /etc/mtab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c76c65f5-3e6c-4992-a9da-1431afa27197 none            swap    sw              0       0
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/brt/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=brt 0 0
root@brt-laptop:~# /sbin/fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090948

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29276   235153408   83  Linux
/dev/sda2           29276       30402     9042945    5  Extended
/dev/sda5           29276       30402     9042944   82  Linux swap / Solaris


Thank you...

---

