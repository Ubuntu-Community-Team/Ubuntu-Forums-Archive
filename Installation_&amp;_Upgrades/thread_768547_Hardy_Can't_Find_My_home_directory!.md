---
title: "Hardy Can't Find My home directory!"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by neatokino on 2008-04-26
With Gutsy, I used the psychocats guide ([http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)) to put my /home directory on a separate partition.  After upgrading to Hardy, when I try to login I get an error message that my /home directory cannot be found.  What do I do????


TIA
Michael

---

### Post by Pumalite on 2008-04-26
Post:
sudo fdisk -l

---

### Post by seshomaru samma on 2008-04-26
and post /etc/fstab

---

### Post by neatokino on 2008-04-26
alright, running in failsafe mode now... here's fdisk -l:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024893

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2           89723       91201    11880067+   5  Extended
/dev/sda3            2551       89722   700209090   83  Linux
/dev/sda5           89723       91201    11880036   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024893

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS



and here's /etc/fstab :


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ffbd7b3b-aa2f-4527-bd45-2cdee033cc67 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=0ee46013-ed75-40a7-8d3d-5d13fdd31c51 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda3 /home ext3 nodev,nosuid 0 2
/dev/sdb1 /storage ext3 defaults 0 0


Any help would be appreciated!

---

### Post by Pumalite on 2008-04-26
Post:
blkid

---

### Post by neatokino on 2008-04-26
Here's blkid:

> /dev/sda1: UUID="ffbd7b3b-aa2f-4527-bd45-2cdee033cc67" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="0ee46013-ed75-40a7-8d3d-5d13fdd31c51" 
/dev/sda3: UUID="f088e9b5-8a16-49cf-b1e0-527b223275e3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="7FD503F15D7235D1" TYPE="ntfs" 

---

### Post by Pumalite on 2008-04-26
Use this to crete a proper entry in fstab:
/dev/sda3: UUID="f088e9b5-8a16-49cf-b1e0-527b223275e3"

---

### Post by neatokino on 2008-04-26
Thanks, pumalite, but I'm not sure how to do that.  Do I simply add that line to my etc/fstab file, or do I replace something else with it?

thanks again

---

### Post by Pumalite on 2008-04-26
Post:
mount

---

### Post by neatokino on 2008-04-26
OK, here's mount:

> /dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,nosuid,nodev)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)


I have not edited /etc/fstab yet because I'm not sure what to do with your previous suggestion.

---

### Post by Pumalite on 2008-04-26
If this is your home:
/dev/sda3 on /home type ext3 (rw,nosuid,nodev)
Then, it's mounted. You have to find out if this is a 'new' home or your 'old' separate /home.

---

### Post by neatokino on 2008-04-26
How do I find that out?  I do know that I have access to all the stuff in my 'old home' (documents, music, etc.), so I think that means my 'old home' IS mounted.  But it only mounted when I logged in with failsafe mode.

I apologize for my ignorance here, but I really don't understand what I should do to log in normally, the way I used to before I upgraded.

Do I need to edit the /etc/fstab file?

Thanks!

---

### Post by Pumalite on 2008-04-26
what happens when you try to boot 'normally'. Post exact error message.

---

### Post by neatokino on 2008-04-26
I just went ahead and edited my /etc/fstab file, adding what you told me to add (I just phrased things like the other UUID's in the file), and I just restarted normally, it it didn't post an error message.  

So, first of all THANK YOU VERY MUCH FOR ALL YOUR HELP!

Second of all, I think it's working, but if I run into any other issues, I will post here again.

thanks once more
M

---

### Post by Pumalite on 2008-04-26
You are welcome. Good luck.

---

