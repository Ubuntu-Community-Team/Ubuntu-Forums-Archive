---
title: "Shared partition questions"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by agim on 2008-01-26
I am interested in setting up a shared partition between Windows and Ubuntu. There are several great posts about this, but I still have a few questions.

First, I have read it can be in fat32 or ntfs. Is one better than the other?
Second, I am a little confused about the fstab entry and what it should be (this might be because of the late hour, I will reread some posts tomorrow, but any help here would be appreciated).
Third, the intended use of this shared partition is mostly a backup partition for my Linux files, I hardly ever use Windows. Really, only when I am missing a linux codec and I need to use Windows. So I would like this partition to be read/write from linux and read only from windows. How would I do this?

I would appreciate any help. I plan on partitioning with the gparted livecd, something I am very comfortable with, so we can skip that part. Just the three questions listed above.

Thanks everyone.

---

### Post by rosegarden78 on 2008-01-26
It cannot be either because FAT32 doesn't support file permissions or symlinks.  And it cannot be NTFS because Linux uses a journaling file system called EXT3.  The only way is to dual-boot: Windows are first partition Linux on the second.  If you fresh install XP with FAT32 format it will be detected automatically in Ubuntu.

---

### Post by agim on 2008-01-26
Okay, we may be talking about two different things.

[http://ubuntuforums.org/showthread.php?t=95855](http://ubuntuforums.org/showthread.php?t=95855)

I am looking to do something similar to this. If I cannot make it read-write from linux and read-only from windows, thats fine. As it will mostly be used as a backup.

---

### Post by rosegarden78 on 2008-01-26
My FAT32 partition is located in /etc/fstab as /dev/sda1 and is mounted at /media/sda1.  If I wanted to manually mount or un-mount it I would do this from a terminal:
sudo umount -a
sudo mkdir /home/customMount
sudo mount /dev/sda1 /home/customMount

Of course this mounts in your home directory instead of default location good luck.

---

### Post by erfahren on 2008-01-26
I use a FAT32 partition for storage and to share data between the two OSs, but Gutsy has support to read/write to NTFS, so that would probably be bettter to use since it gets less defragmented and is less prone to errors. (You could use FAT32 if you want to, or if you're not using Gutsy.)

anyway - once you get the partition made you can use the "blkid" command to get the information on it

for example...
```

erfahren@acer-xubuntu:~$ blkid
/dev/sda1: UUID="7004581F16D9B5D2" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="A4E40FFDE40FD10A" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: LABEL="DATA" UUID="3CA5-B33D" TYPE="vfat" 
/dev/sda5: UUID="22ae0b59-13a8-4032-9c54-481d4578bd98" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="683abe23-beda-4617-8907-2f0c2414cb75" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="c42afbbf-30ac-4f7a-9c6c-9f6fb178e32d" TYPE="swap"

```
you can use the [UUID](http://linux.byexamples.com/archives/321/fstab-with-uuid/) for the partition if you want, but it isn't necessary

if I wanted to mount the /dev/sda3 partition - I could create the mount point as "/mnt/data" and make the entry in /etc/fstab like this (back it up first - always a good idea) ....

if it was NTFS (let's pretend it is)
```

/dev/sda3     /mnt/data     ntfs    defaults,umask=000     0       0

```
that will give read/write permission to all users

for FAT32...
```

/dev/sda3     /mnt/data    vfat    defaults,utf8,umask=000     0       0

```

after editing the /etc/fstab "mount all" with:
```

sudo mount -a

```

you can also look at:
[How to edit and understand /etc/fstab - 1.1](http://www.tuxfiles.org/linuxhelp/fstab.html)
[(Fedora forums) Setting permissions for FAT (and NTFS) filesystems](http://forums.fedoraforum.org/archive/index.php/t-32096.html)
[Hermanzone's mounting section](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop)
[Psychocat's mounting windows guide](http://www.psychocats.net/ubuntu/mountwindows)

that should work for you - good luck!

---

### Post by agim on 2008-01-26
Thanks, both of you. I really appreciate it. The forums are great.

After thinking about it a little. I am thinking of just making another ext3 partition for storage. Something kept safe and readable from a linux liveCD. I often install and uninstall different versions of Ubuntu, and I want to keep some files in their own place.
I know that you can make a separate home parition, but sometimes I have a little too much fun with Ubuntu and screw things up beyond belief. I am learning a lot, though.

So thanks again, this is exactly what I was looking for, a pointer in the right direction. Now I can weigh my options.

What do you guys think of a separate ext3 partition?

---

