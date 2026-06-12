---
title: "add second hard drive to /home ?"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by rolypolycat on 2010-06-21
Hello!

I just did a command line install of ubuntu, put xfce on it,( so I could add what few programs I actually use, not all the stuff that comes with xubuntu). When I partitioned, I set my home partition on the first drive, but couldn't add the 2nd drive to the /home directory, so I set it as /opt. It's owner is listed as root. I used the "users and groups" gui to add myself to /opt, but it still won't let me create any folders and whatnot in /opt. I went and checked  the box under root to presumably add myself to root, but that didn't work either. I mostly want to keep my biggest files in /opt, so I don't run out of space in /home. I tried LVM when I was setting up, but I did something wrong all 4 times because it only recognized the root partition as /home, and didn't merge the 2 drives at all. After the 4th time, I gave up because I must have a working system right now.
Does anyone have a simple method for getting /opt under my control, so I can start adding my big files to the drive? I figure it's probably something simple,but I'm missing the idea somewhere. I really, really don't want to re-do my machine a 5th time, so any help is very greatly appreciated. thanks!:confused:

---

### Post by dabl on 2010-06-22
> **rolypolycat said:**
> 

 When I partitioned, I set my home partition on the first drive, but couldn't add the 2nd drive to the /home directory, so I set it as /opt.



This is where you went wrong.  "Couldn't add ..." is not a problem description -- that issue needs to be understood and fixed, before there's going to be any help for setting up /home on the second drive.

- Is it seen correctly in the BIOS?
- Is it partitioned?
- What is the filesystem?

p.s. Are you aware that your avatar says "7.10"?  Which version are we talking about here?

etc. etc.

---

### Post by rolypolycat on 2010-06-22
The 2nd drive is visible; that's where /opt is located. Swap and /opt are both there. On the 1st drive is /home and /root. The filesystem is ext4. When I used the partitioner, I tried to set up the 2nd drive as part of home, but the partitioner wouldn't allow 2 /home directories, nor could I understand how to combine the two.
I never even noticed my avatar had the wrong version until now. I've used it for a long time. The version I'm using is Lucid Lynx from a command line install.

---

### Post by dabl on 2010-06-22
OK -- that's a good story.  :lolflag:

So, I take it you have (at least) two partitions on the second drive?  And at this time one of them is /opt and the other one is empty?

Can you please post the output of these three console commands:

```
cat /etc/fstab
```

```
sudo fdisk -lu
```
```

sudo blkid
```

That should be enough to get us clear on the partition and filesystem layouts.

---

### Post by oldfred on 2010-06-22
You do know that /opt is a system directory that you should not be using for your data??

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

If you do not have enough room in /home you may really want  a /data partition and mount that into /home. My current /home is about 1GB with all my data (and I move as much as possible including some things in hidden folders) in the /data partition.

while discussing multiboot it is about setting up & easily using a data partition in mutiple systems.
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by rolypolycat on 2010-06-23
shell@the-cathouse:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=811c9756-9f83-466b-bb74-dec91f725335 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=34be25fc-08c2-421b-b9a3-07d97b4be0cc /home           ext4    defaults        0       2
# /opt was on /dev/sdb1 during installation
UUID=5bf3621a-999a-47f4-876c-b246e28a558b /opt            ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
#UUID=8dccb2a9-c5a4-4adf-bf0e-b8b44f9b9fd3 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
shell@the-cathouse:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009c71a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    21878783    10938368   83  Linux
/dev/sda2        21880830   312580095   145349633    5  Extended
/dev/sda5        21880832   312580095   145349632   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b0db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   306638847   153318400   83  Linux
/dev/sdb2       306640894   312580095     2969601    5  Extended
/dev/sdb5       306640896   312580095     2969600   82  Linux swap / Solaris
shell@the-cathouse:~$ sudo blkid
/dev/sda1: UUID="811c9756-9f83-466b-bb74-dec91f725335" TYPE="ext4" 
/dev/sda5: UUID="34be25fc-08c2-421b-b9a3-07d97b4be0cc" TYPE="ext4" 
/dev/sdb1: UUID="5bf3621a-999a-47f4-876c-b246e28a558b" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="69fa7ba9-33d7-47d9-a989-d3872acaf6b2" TYPE="swap" 
shell@the-cathouse:~$ 

I know enough about Linux to do more than the average user, but not to prevent screwing it up in grand style, so please bear with me.
I don't remember seeing /data as an option when naming partitions when I was setting up the drives; did I just miss it?

---

### Post by oldfred on 2010-06-23
You can create after the install your /data. You create a mount point and mount it. You can also make a permanent mount in fstab.

It also can have a name from a label of a partition which can be used in fstab for mounting instead of UUIDs. 

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data

If you cannot read and write then change the permissions. (not NTFS)

$ sudo chmod -R 777 /Data
sudo chown -R user:user /Data

---

### Post by dabl on 2010-06-23
This unfortunate arrangement of partitions and mount points is fixable.  You will have to think about it as a sequential process -- I'm going to describe the process as best I can, and let the precise commands be an exercise for the student (after all, you can always just reinstall it correctly).

1. unmount, via the umount command, the filesystem that is currently mounted to /opt

2. Delete from /etc/fstab the line mounting a partition to /opt

This will leave you with /home still mounted on /dev/sda5.  Reboot your system.  I don't know if there will be an error regarding a missing /opt directory -- I've never tried to boot without one.  Assuming you can get booted, and a "ls" at the "/" directory confirms that you have no /opt directory, go ahead and

```
sudo mkdir -p /opt
```

( if booting fails, you could boot a Live CD and chroot into the root filesystem to create the missing /opt directory )

3. Reboot to confirm you've got a working OS all on /dev/sda, with /home mounted on the /dev/sda5 partition. You should have a non-used /dev/sda2 partition as well as a non-used /dev/sdb drive with 3 unused partitions on it.

So, now you have some choices, but choices also have consequences.  For example, using GParted to merge /dev/sda2 and /dev/sda5 (by eliminating /dev/sda5 and enlarging /dev/sda2) will have the consequence of creating a new UUID and screwing up the partition ID for /dev/sda5 in /etc/fstab.  That is fixable by editing, but you need to know about it and plan for it.

You are correct that "/DATA" is not a part of the standard Linux filesystem and does not appear as a choice during manual partitioning in installation.  If you want to use GParted to label the partitions on /dev/sdb, you can label them "MUSIC", "VIDEOS", and "IMAGES", or whatever you have, and also make same-name mountpoints in /mnt, then you can add mount lines in /etc/fstab and mount them at boot time (use their UUIDs or their labels in /etc/fstab).  Then, once you have confirmed that they are automatically mounting, you can make a single directory on each of those partitions, same name as the label, and you can change the permissions on the folders to your user and symlink them into your /home/rolypolycat folder for convenience.

I hope this helps.

---

### Post by rolypolycat on 2010-06-23
well folks, I've read the posts, a bunch of the links, and printed it all out, so I'm going to try these suggestions. Hopefully everything  will work out, and I won't have too much trouble. (If you hear an anguished scream from the southwestern US, don't be surprised, though:p)
I'll let you know how it turns out. Thanks again for all the help and tips!

---

### Post by rolypolycat on 2010-06-25
Houston, we have liftoff!
The drive is working! I can read/write and store stuff on it!
So this might help somebody in the future, here's what I did:
1. reboot
2. re-install from command line; put root, home, and swap on 1st drive, labeled other as /data
3. partitioned the drives this way.
4. sudo blkid -c /dev/null and got a very long UUID number
 for the drives
5. sudo mkdir data  /home/shell
6. sudo mount /dev/sdb5  /home/shell/data
7. sudo chown -R shell:shell  /home/shell/data
8. sudo leafpad /etc/fstab (leafpad is an editor I use a lot)
9. added really long UUID number to bottom of fstab file
10. saved and rebooted. Added programs I wanted, then booted into new desktop. The data partion on 1st drive didn't seem to link to the one on the second drive, but I could get into the second /data on the 2nd drive. Still couldn't create any folders, so I went to step 11.
11. sudo chown shell:shell /home/shell/data
sudo chown shell:shell  ?home/shell
sudo chmod 766 /home/shell/data
The /data directory on the 1st drive still isn't linked to the /data  directory (which makes up all of drive 2); I deleted it late without problems. While in /data on 2nd drive, I made a link in the listing on the side panel, and it works fine. I can work with the drive. Not all that sure what I've done, but at least now I can use both drives, and I wrote it all down, so I know what to do next time I add any more drives.
Once again, thanks everybody!:KS

---

### Post by oldfred on 2010-06-25
Glad it is working if you want a list of the commands you ran just from terminal:
history

I saved my history from my Karmic install and converted it to a bash file which I have used to install to Lucid and Karmic on my portable so my portable is set up similar to my desktop.

---

