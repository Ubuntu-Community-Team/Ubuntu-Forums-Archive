---
title: "Swap Partition!"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by lnogueir on 2007-10-17
Hi!

I don't now why but looks like I don't have a swap partition!

[http://img120.imageshack.us/img120/6703/swaprq1.jpg](http://img120.imageshack.us/img120/6703/swaprq1.jpg)


Someone can help me??? Please!

---

### Post by Pumalite on 2007-10-17
Your system is just not using /swap. Post:
sudo fdisk -lu

---

### Post by lnogueir on 2007-10-17
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd7f6d7f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    31455269    15727603+   7  HPFS/NTFS
/dev/sda2        51408000   195366464    71979232+   5  Extended
/dev/sda3        31455270    49415939     8980335   83  Linux
/dev/sda4        49415940    51407999      996030   82  Linux swap / Solaris
/dev/sda5        51408065   195366464    71979200    7  HPFS/NTFS

Partition table entries are not in disk order


THanks for your help!

---

### Post by Pumalite on 2007-10-17
You are welcome. Happy Ubuntuing!

---

### Post by lnogueir on 2007-10-17
Thanks! I'm loving Ubuntu! Compiz Fusion is amazing! 

With Gparted I was able to mount swap partition, but every time I reboot lost swap.

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=c82fd88b-5ea0-4192-aae3-9d307494d088 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5E207A93207A71BF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=CB74F9F4989ECFF5 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=93bbd09c-5999-412b-98c6-c4676072f394 swap            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0




Is something wrong???

---

### Post by Pumalite on 2007-10-17
Post:
mount

---

### Post by lnogueir on 2007-10-17
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

### Post by Pumalite on 2007-10-17
Where did you get the idea that you loose it?

---

### Post by Pumalite on 2007-10-17
You are fine.

---

### Post by lnogueir on 2007-10-17
But on system monitor I have: swap used 0 of o bytes!!!! (Image first post)

With gparted I can mount it, but after restart I loose swap.

---

### Post by Pumalite on 2007-10-17
Most people with 1 GB of memory never use /swap

---

### Post by lnogueir on 2007-10-17
I made sudo swapon /dev/sda4 and I pass from "swap 0 of 0 bytes" to "swap 0 of 978 Mb"

Can I had this command to startup?

Still thinking something is wrong!

---

### Post by bombeg on 2007-10-17
sudo swapon /dev/sdaX

---

### Post by lnogueir on 2007-10-17
[https://bugs.launchpad.net/ubuntu/+bug/133564](https://bugs.launchpad.net/ubuntu/+bug/133564)

It's a gutsy bug!!!!


Thanks for your help!

---

### Post by Pumalite on 2007-10-17
Thank you for posting the link.

---

### Post by louieb on 2007-10-17
check the **uuid** of /dev/sda4  (in /etc/fstab)
against the  output of 
```
ls -l /dev/disk/by-uuid
```and adjust /etc/fstab accordingly. 

Altho the **uuid** should not change I've seen the uuid of a partition change  when formating  a partition  or resizing one.  

I've had to fix my swaps **uuid** on a couple of PC. Never did use Edgy but have see both Feisty and Gutsy change the uuid

---

### Post by lnogueir on 2007-10-17
I have already do that! But thanks! 

UUID seems like a good idea, but isn't working very well!

I think UUID is the reason why I cant hibernate my notebook! Looks like every time I try to hibernate, the UUID to the swap partition change! UUID isn't suppose to be unique!?

---

### Post by louieb on 2007-10-17
> **lnogueir said:**
> ...think UUID is the reason why I cant hibernate my notebook! Looks like every time I try to hibernate, the UUID to the swap partition change! UUID isn't suppose to be unique!?

Yes it is is but you have to change the  uuid  in 2 places. Had that problem before heres the fix I used:  
[http://ubuntuforums.org/showthread.php?t=528306](http://ubuntuforums.org/showthread.php?t=528306)

---

