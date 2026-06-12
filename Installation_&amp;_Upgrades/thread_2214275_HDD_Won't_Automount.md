---
title: "HDD Won't Automount"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by Keith W on 2014-03-31
I am using Ubuntu 12.04 and want a hard drive to mount automatically at start up.  I have found lots of advice on line but whatever I do I always get this message during boot up:
"The disk drive for </media/BackupDrive> is not ready yet or not present."   I have tried waiting but nothing happens so I have to skip the mounting.

I have attempted creating a folder called BackupDrive in /media but still get the same message (and when mounted manually the drive appears in another folder called BackupDrive_ - note the underscore).  

This is the drive identity from blkid:
/dev/sdb1: LABEL="BackupDrive" UUID="4A54C43254C42295" TYPE="ntfs"

and this is the entry currently in fstab:
UUID=<4A54C43254C42295> </media/BackupDrive> <ntfs> uid=<1000>,gid=<1000>,umask=0022,async,auto,rw 0 0
The drive is (like the other drive in the machine) an IDE drive.

I should add that I am far from au fait with Linux so am probably missing something blatantly obvious.

Any help would be greatly appreciated.

---

### Post by sandyd on 2014-03-31
> **Keith W said:**
> I am using Ubuntu 12.04 and want a hard drive to mount automatically at start up.  I have found lots of advice on line but whatever I do I always get this message during boot up:
"The disk drive for </media/BackupDrive> is not ready yet or not present."   I have tried waiting but nothing happens so I have to skip the mounting.

I have attempted creating a folder called BackupDrive in /media but still get the same message (and when mounted manually the drive appears in another folder called BackupDrive_ - note the underscore).  

This is the drive identity from blkid:
/dev/sdb1: LABEL="BackupDrive" UUID="4A54C43254C42295" TYPE="ntfs"

and this is the entry currently in fstab:
UUID=<4A54C43254C42295> </media/BackupDrive> <ntfs> uid=<1000>,gid=<1000>,umask=0022,async,auto,rw 0 0
The drive is (like the other drive in the machine) an IDE drive.

I should add that I am far from au fait with Linux so am probably missing something blatantly obvious.

Any help would be greatly appreciated.

Try removing the '<' and '>'
```

UUID=4A54C43254C42295 /media/BackupDrive ntfs-3g uid=1000,gid=1000,umask=0022,async,auto,rw 0 0
```

---

### Post by Keith W on 2014-03-31
> **sandyd said:**
> Try removing the '<' and '>'
```

UUID=4A54C43254C42295 /media/BackupDrive ntfs-3g uid=1000,gid=1000,umask=0022,async,auto,rw 0 0
```


You have cracked it for me. Mounts perfectly now.  My sincere thanks.

---

