---
title: "Ubuntu install messed up grub"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by bikewrecker on 2013-04-12
After installing Ubuntu 12.10 over 11.10, my computer will no longer boot up. 

When I try to boot normally I get this:
```
Verifying pool data............
error: file not found. 
grub rescue>
```

I can still boot from the Ubuntu CD, but idk what commands will fix this. 

Thank you for your help!

---

### Post by darkod on 2013-04-12
From live mode post your partition with something like:
```
sudo parted -l (small L)
```

After that we can give you commands to add only grub2 from live mode.

---

### Post by Routhinator on 2013-04-12
If you boot into rescue mode, there is an option to reinstall the grub boot loader. Alternatively you can use the live cd to boot a root shell in under your main partition and run:

```

sudo update-grub
sudo grub-install /dev/sda

```

update-grub should be able to detect your partitions for you and simplify the process.

---

### Post by Routhinator on 2013-04-12
Oh, I should mention.. Rescue mode (last I checked) is only available on the ALT-Install disk, which is a good idea to keep a copy of at all times.

---

### Post by bikewrecker on 2013-04-12
Ok here it is:
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD6400AAKS-2 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  419GB  419GB  primary   ntfs         boot
 2      419GB   530GB  110GB  primary   ext2
 3      530GB   640GB  110GB  extended
 5      530GB   640GB  110GB  logical   ext2


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 
```

---

### Post by darkod on 2013-04-12
I don't know if your root partition is sda2 or sda5. I guess you know that. To install grub2 from live mode to the sda MBR, in terminal execute:
```
sudo mount /dev/sdaX /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

In the first command use sda2 or sda5 according to your root partition. The second command should have only /dev/sda with no number in it.

The above only installs small code of grub2 on the MBR, to get the booting off. It assumes your grub2 files and config are correct inside ubuntu. If they aren't, there is a way to fix that too. The above is the shorter procedure to try first.

On a side note, why are you using ext2 instead of ext4?

---

### Post by bikewrecker on 2013-04-12
Ok, that worked perfectley! Thank you so much for your help!

I don't know the difference between ext2 and ext4. I really don't know as much about installing OS's as I should. I just try to make do. Should I have installed it as ext4 instead? Should I go back and reinstall it?

---

### Post by bikewrecker on 2013-04-12
Also I don't remember how to change the prefix to solved.

---

### Post by darkod on 2013-04-12
The Mark As Solved option should be in Thread Tools above the first post but I think it's not working right now after they upgraded the forum to another version.

ext4 vs ext2 is not that critical, I don't know the differences in details myself. I only know that the ext4 is the latest one and used by default unless you select otherwise.

You can google to read more about their differences and maybe it will have some recommendations whether a reinstall is worth it. People are still running ext2 so it's not like you have to do it. On the other hand, if the disk is still empty from personal data it might be the best moment to reformat and reinstall before you start loading it with data. The formatting will delete everything of course.

---

### Post by claracc on 2013-04-14
> **bikewrecker said:**
> Also I don't remember how to change the prefix to solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

