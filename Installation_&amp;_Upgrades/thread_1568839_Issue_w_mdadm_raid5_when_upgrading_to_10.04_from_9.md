---
title: "Issue w/ mdadm raid5 when upgrading to 10.04 from 9.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by lordofduct on 2010-09-05
So tonight I upgraded my fileserver to 10.04 using the upgrade utility. I was going from 9.04 to 10.04. I went step by step from 9.04 -> 9.10 -> 10.04. I stopped at 9.10 to make sure things were still working, and everything was fine there as far as I could tell.

When I got to 10.04 though I had a problem booting up. My fileserver is headless and I remote desktop into it with FreeNX, or ssh in if I can't connect that way. Neither would work, and I connected a display to find that there was an error saying it couldn't mount /dev/md0p1... and to press "i" to ignore. I ignored.

Now I'm booted in and I do have a raid device on here. It's 3 harddrives in a raid5 configuration for 1.25 terrabytes storage.

The thing is, my device is /dev/md0/ and it's working!

There is no /dev/md0p1 either...

```

server@server1:~$ sudo mdadm --misc --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Oct 27 14:16:27 2006
     Raid Level : raid5
     Array Size : 1250258432 (1192.34 GiB 1280.26 GB)
  Used Dev Size : 625129216 (596.17 GiB 640.13 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Sep  5 22:06:24 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : ab22c354:d3e6a737:cc4346d7:9e3ce630
         Events : 0.5589482

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
server@server1:~$ sudo mdadm --misc --detail /dev/md0p1
mdadm: cannot open /dev/md0p1: No such file or directory


```

I can even access it, I have the device mapped to /mnt/storage_raid5, and I can navigate it and read it. It's even shared through samba and all my other computers can access it.



But if I open gparted and go to /dev/md0, and there is a partition on it called /dev/md0p1 with a giant exclamation point. If I open the 'Information' it says:

```

e2label: No such file or directory while trying to open /dev/md0p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.41.11 (14-Mar-2010)
dumpe2fs: No such file or directory while trying to open /dev/md0p1

Unable to read the contents of the file system!
Because of this some operations may be unavailable.

```

This partition is the size that /dev/md0 aught to be... as if it IS the partition I'm sharing... but, how is it having this error AND still accessible? And this error keeps occurring if I restart, so it persists.

---

### Post by lordofduct on 2010-09-08
So no help?

Well I also have another issue as well. Another computer in my house was just upgraded to 10.04 as well and it won't mount this share though I have it set in fstab...

```

//ip_of_server/media /mnt/somename   cifs   auto,_netdev,file_mode=0555,dir_mode=0555   0   0

```

This is the same exact way I have it set on another machine running 10.04, and it mounts just fine at boot up. But on this other machine it doesn't... if I run 'mount -a' after logging in it works fine.

I'm thinking it's because the network isn't up yet when the mount occurs... but I thought that's what _netdev was for... isn't it?

---

### Post by lordofduct on 2010-09-21
Self Bump...

if anyone could please help... still haven't gotten anywhere with these.

---

