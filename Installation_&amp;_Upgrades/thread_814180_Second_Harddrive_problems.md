---
title: "Second Harddrive problems"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by Xinto on 2008-05-31
Hello everyone.

I'm pretty much brand new to the whole Ubuntu OS, and i need some help. Ok here's my problem. I am running 2 harddrives at the current moment. 1 is an 80gig which is my OS drive, nothing but Ubuntu on it. The second is a 320gig which is split into two 160gigs. Now the 320gig was from when i ran windows. So it is in NTFS file format.But i have no trouble reading or writing to it. I just purchased a 500gig and installed it. I made it one 500gig partition and it is in EXT3 file format. But for some reaoson i cannot read or write to the drive. I've looked on other forums and found some help, but nothing seemed to work. If you could help out in any way it would be great. 

Thanks
Xinto (newbie)

---

### Post by Rocket2DMn on 2008-05-31
Can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```

---

### Post by Xinto on 2008-05-31
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3e423e42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009d151

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34f1c91d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19456   156280288+   7  HPFS/NTFS
/dev/sdc2           19457       38913   156288352+   7  HPFS/NTFS

---

### Post by Rocket2DMn on 2008-05-31
Can you post the other commands as well?  Then we can add an entry to fstab using the UUID of the new drive.

---

### Post by Xinto on 2008-05-31
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5e2a0375-86b9-4bc5-a7f5-d0b57ed7aed8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3cf9698a-7586-4ac1-8d2e-4ce650a678db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


/dev/sda1: UUID="5e2a0375-86b9-4bc5-a7f5-d0b57ed7aed8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="3cf9698a-7586-4ac1-8d2e-4ce650a678db" 
/dev/sdb1: UUID="451c4fa8-fe00-4981-ae82-dc11d1e54ebe" TYPE="ext3" 
/dev/sdc1: UUID="F25C2AF25C2AB0F1" TYPE="ntfs" 
/dev/sdc2: UUID="6E549C4A549C1745" TYPE="ntfs" 

I think that should be it?
Xinto

---

### Post by Rocket2DMn on 2008-05-31
OK, now we're going to add an entry to fstab for sdb1 (the 500GB partition).  First we will make the mount point, you can call it whatever you want (no spaces please) - i will call it "500gb".
```
sudo mkdir /media/500gb
```
now open the file to edit
```
gksudo gedit /etc/fstab
```
Add the line
```
UUID=451c4fa8-fe00-4981-ae82-dc11d1e54ebe /media/500gb ext3 defaults 0 0
```
Save and close, then chown the mount point so your username has ownership
```
sudo chown <yourusername> /media/500gb
```
Now you can mount the drive with
```
sudo mount -a
```

Are your other partitions mounting ok?  They don't have fstab entries, but if they are working as you want, there is no need to add them.

---

### Post by Xinto on 2008-05-31
The 500gig mounted perfectly, but i still can't write/copy the drive at all.

---

### Post by Rocket2DMn on 2008-05-31
Did you chown the drive like I said?  Try using the command recursively with the drive mounted:
```
sudo chown -R <yourusername> /media/500gb
```

---

