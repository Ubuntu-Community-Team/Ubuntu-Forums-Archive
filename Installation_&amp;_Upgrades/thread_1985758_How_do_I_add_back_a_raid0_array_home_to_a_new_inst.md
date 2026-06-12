---
title: "How do I add back a raid0 array /home to a new install of 12.04"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by v4169sgr on 2012-05-23
Apologies if this is a F.A.Q., but I didn't see a suitable answer - maybe I'm blind :P

In about a week and a half, I will:
* install 12.04 on a new desktop PC [on an SSD];
* take out two Samsung HD603Js [1 TB each] from the 10.04 PC and install them in the new PC;
* switch it on;
* and - hope it all works! :)

The two disks have two software raid0 partitions spread over them, one for root, and the other for home. I am not sure, but I think /boot and swap are not raided.

I'd like to use /dev/md0 [root] for reference, and /dev/md1 I do need for the user space files [that is /home].

Information as below, but is it really so simple as I've described? If not, what do I need to do?

Asking because I don't know much about raid ...

Thanks!
v4169sgr

cat /etc/mdadm/mdadm.conf

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=fda88cf5:7dbf771e:84aa465c:f0e60ba7
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=3e44c0c4:ce2cd4af:66d5c71f:8b1bacd3

# This file was auto-generated on Thu, 03 Jun 2010 10:46:12 +0100
# by mkconf $Id$


```

df -kh


```

Filesystem            Size  Used Avail Use% Mounted on
/dev/md0               19G   11G  7.2G  59% /
none                 1003M  364K 1002M   1% /dev
none                 1007M  556K 1006M   1% /dev/shm
none                 1007M  252K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda1             1.9G  335M  1.5G  19% /boot
/dev/md1              1.8T  346G  1.4T  21% /home


```

sudo mdadm --detail /dev/md0

```

/dev/md0:
        Version : 00.90
  Creation Time : Thu Jun  3 10:37:07 2010
     Raid Level : raid0
     Array Size : 19529600 (18.62 GiB 20.00 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jun  3 10:37:07 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : fda88cf5:7dbf771e:84aa465c:f0e60ba7
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5

```

sudo mdadm --detail /dev/md1

```

/dev/md1:
        Version : 00.90
  Creation Time : Thu Jun  3 10:37:27 2010
     Raid Level : raid0
     Array Size : 1930084224 (1840.67 GiB 1976.41 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Thu Jun  3 10:37:27 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 3e44c0c4:ce2cd4af:66d5c71f:8b1bacd3
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        6        0      active sync   /dev/sda6
       1       8       22        1      active sync   /dev/sdb6

```

---

### Post by darkod on 2012-05-23
Did you install with the Alternate Install CD originally, and created the softraid during install?

If you did, you should be familiar with the alternate installer.

If I'm not wrong, use the alternate installer and select the manual partitioning. It will detect your arrays.

From there on, use the /dev/md0 for what ever you want (I guess the new root will be on the SSD otherwise there's no point using a SSD :) ), and use /dev/md1 as /home.

Don't forget to select the same filesystem as it has now, for example ext4 if that's what it has. This is very important especially for /home.

You could mount /dev/md0 as /data or another custom mount point as you wish.

If you see that things are not the way you expect them to be (for example the arrays are not discovered correctly), exit the installer and that will make no changes to the system.

---

### Post by v4169sgr on 2012-05-23
Thanks a lot for the super-quick answer :)

Actually, I've not done the install yet [I don't even have the new PC yet! :P]

I'm thinking of (a) fresh installing to the SSD [with /boot, /, and swap], then (b) powering off the PC and adding the raid0 disks. This way, I avoid fat fingering and losing the user data.

Apologies if I was not clear enough earlier ...

What do I need to do to 'see' the disks?

---

### Post by v4169sgr on 2012-05-23
And yes, I must have created the softraid using the alternate install originally, but it was a long time ago and very hazy ... :(

---

### Post by darkod on 2012-05-23
You will have to install mdadm and assemble the raid, I think. Not sure if any further action will be needed to make mdadm load at boot.

That is the difference. If you do it during install, I think it's included in the OS automatically.

Be careful about one thing though, you use mdadm --create only the first time, and NEVER again unless you want to lose all data on the raid.

You assemble an existing array(s) with:
sudo mdadm --assemble --scan

That will scan all disks automatically so you don't need to enter the correct info by hand. After that command you should have your /dev/md0 and /dev/md1 devices available.

Then you will have to make entries in /etc/fstab so that they mount on boot.

Personally, I would do it during the install, not after.

I know you didn't do the 12.04 install yet, I was talking about the 10.04 installation. Somehow, someone, created this current raid right? If you did it during install that time, it seems you already used the alternate installer.

On another note, but I guess you are aware of that, raid0 doesn't offer any redundancy or protection for the data. I see you have your /home there and want to keep using it. But if one disk dies, everything is gone.

Personally I wouldn't use RAID0 for any important data.

---

### Post by v4169sgr on 2012-05-24
Thanks again for your replies :)

Agreed, it seems most sensible to let the system sort out the auto detection during the install process. Editing /etc/fstab seems a bit of a faff for what it is, and I've been down that road often enough - years back [MCC and SLS, anyone?].

I guess I'm just slightly worried that I would 'install to the wrong place'; previously I added the user data back after the install for this reason, but I've never done that with a raid array.

Point taken about raid0, and yes, I am aware, however the disks are reliable, and I back up frequently to an external HDD with the same size as the array.

---

### Post by darkod on 2012-05-24
As long as you are being careful selecting the mount points and filesystems, you should be fine.

The most important thing when using existing /home partition is in the Use As field to select the filesystem that it already has. Otherwise it can try to format it, and if you don't notice that it can wipe your data.

So, just make sure you select the /home mount point and the correct FS.

For the root partition, since you will be installing on a new SSD, it's easier. Simplt select the / mount point, and the FS you want to use which will format the partition anyway since it's new.

When you look at the partitions list when everything is done and before you continue, the partitions marked for format will have F in their line, I don't remember exactly now in which column. Watch out that /home doesn't have the F.

---

### Post by v4169sgr on 2012-06-05
Just wanted to say 'thankyou' for your advice - much appreciated. You are of course completely right, and manual partitioning on the alternate install disk is very capable of doing what I wanted to do.

---

