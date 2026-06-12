---
title: "Cannot chmod on new HDD installed"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by e24ohm on 2013-05-11
Folks:
Hi Community:

I recently installed a new HDD and partitioned the drive with one primary partition. I then used the mkfs.ext4 to format it. Currently Ubuntu is Automounting the drive on boot; however, late last night I was not able to ‘sudo chmod +x’ to a BASH script I made on the drive. I am able to read and write files on the drive. The command functioned as if it worked; however, when inspecting the file, the attributes were not changed.

This is the output of the file system from ‘fdisk –l’:

//---
```
Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0b493b78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953525167   976761560   83  Linux
```
//---

I am not sure if this means anything, but this drive was originally partitioned and formatted as NTFS on windows box; however, once I installed the drive into my Ubuntu box – I ran ‘sudo fdisk /dev/sdc’ and ‘mkfs.ext4’ for the correct drive. And, like I said – I am able to read/write to the drive, just cannot ‘sudo’ chmod.


I’m at a lost, so I’m looking for suggestions and to brainstorm the issue.

Thanks.
E

---

### Post by prodigy_ on 2013-05-11
> **e24ohm said:**
> just cannot ‘sudo’ chmod.


I’m at a lost, so I’m looking for suggestions and to brainstorm the issue.
Well, my suggestion is that you specify what exactly you tried to chmod and post the output you got.

---

### Post by e24ohm on 2013-05-11
> **prodigy_ said:**
> Well, my suggestion is that you specify what exactly you tried to chmod and post the output you got.

A BASH file as I pointed out, and the the syntex I used included the SUDO command. In addition, there is no output - it appears as if it worked, and throws no errors. In addition, despite the user and group membership, it should not matter due to the fact that I used “sudo”. In addition, I wanted to give execute to all “groups” “user” and “other”, so the +x should work. Also, I did a “```
chmod +r
```”, which did not work as well. And, I tried other files, which did not work as well.

Due to the latter, I am suspecting it is something with the file format or partition, yet what is confusing me – is the fact that I can r/w since I am able to copy and make new files and directories.

One thing I did notice – _the drive does not have an entry in my ‘fstab’ location, so Ubuntu is automounting the disk somehow_. **Where does Ubuntu Automount HDD/Disks at**?

---

### Post by prodigy_ on 2013-05-11
> **e24ohm said:**
> there is no output - it appears as if it worked, and throws no errors.
What's the output of ```
cat /proc/mounts
``` command? I guess the partition is mounted with **noexec** option (explicit or implied).

---

### Post by e24ohm on 2013-05-11
> **prodigy_ said:**
> What's the output of ```
cat /proc/mounts
``` command? I guess the partition is mounted with **noexec** option (explicit or implied).

thanks for the help Prodigy... this is driving me crazy...since I can read/write files to the drive.


cat /proc/mounts
```
/dev/sdc1 /media/DATA fuseblk rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 0 0
```

I'm not sure what this is telling me, so I hope it has some details.

I configured this drive like I did my other drives.

sudo fdisk /dev/sdc
and did the standard partition wizard, via fdisk... and just created a primary partition with the defaults. only thing I can think of, is that it did not blow all the partition information off from the windows partition, but i'm not sure if that is possible...only brainstorming.


Thanks.

---

### Post by e24ohm on 2013-05-11
I became quite annoyed at this issue, and decided to partition and format the drive one more time. This time I supplied a name when I formatted the drive, since I noticed it still was using the name given to the hdd when it was installed in the windows server.

This is odd, but that is the only step different I performed this time, and it works. It now allows files and directories to have permissions changed (example: +x or +r or +w). I am not sure if permission types were broken; however, as my earlier posts show &#8211; it had the correct partition format.

Odd, but I am marking this thread closed.

---

