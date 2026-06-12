---
title: "Filesystem change/full ? (Hardy =&gt; Intrepid)"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by riodemes on 2008-10-31
Hey everyone!

I recently upgraded to 8.10 this morning, and it looks great. But everything I try to download, write, or even try to backup spits out an error that my filesystem is full, which it is most certainly not, as it doesn't show as being full on Windows, and was not full under Ubuntu 8.04 

I am running Ubuntu 8.10 on a dual boot. The filesystem when going into system monitor displays:
(Device, Directory, Type, Total, Free, Available, Used)
/host/ubuntu/disks/root.disk,  /,  ext3 ,12.9GiB , 89.5MiB, 0 bytes,  12.8
/host/ubuntu/disks/boot, /boot, none, 51.0GiB, 20.2GiB, 30.9GiB
/dev/sda3, /host, fuseblk, 51.0GiB, 20.2 GiB, 20.2 GiB, 30.9 GiB

I would send images, but i can't print screen or anything. Please help, I have no idea where to go for course of action. I tried googling and browsing through documents, but I haven't found anything.

---

### Post by riodemes on 2008-10-31
bump

---

### Post by Herman on 2008-10-31
:) Hello riodeme,
 
I'm just taking a wild guess here, but sometimes it can happen that the file system is full but the partition is not full.
It could be that your file system isn't big enough to fill the partition.

Some programs look at the file system and tell you it's full, while other programs look at the partition and report that the partition is not full yet.
Both kinds of programs are telling you the truth.

That can happen especially after restoring a partition from a backup made with Partimage or the 'dd' command. Normally the new partition you are restoring to needs to be bigger than the previous one, (the one the backup was made from), or there would be trouble. The file system should be resized afterwards though.

It you have an ext3 file system, you should try running the command '[FONT=Bitstream Vera Sans Mono]resize2fs -p /dev/sda2'
[/FONT]The [resize2fs]("http://linux.die.net/man/8/resize2fs") command is used to calibrate the size of the file system to the size of the partition. The file system needs to be unmounted to do this, so it's probably best if you can do it from a LiveCD, or at least from an operating system in a different partition, making sure to unmount the file system in the partition you want to work on.
```
resize2fs -p /dev/sda2 
```Where: sda2 is your ext3 partition, if not, replace with whatever partition number you have. Check with Gnome Partition Editor or 'sudo fdisk -lu' command.

EDIT: I don't know what that could possibly have to do with upgrading from Hardy to Intrepid Ibex, but it won't do any harm to try  resize2fs anyway, if I'm wrong then nothing will happen.  

Regards, Herman :)

---

