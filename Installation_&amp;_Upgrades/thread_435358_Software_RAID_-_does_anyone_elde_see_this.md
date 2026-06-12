---
title: "Software RAID - does anyone elde see this?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by marcw on 2007-05-06
I'd like to ask a favor of anyone running software RAID, but first this short background.

About a week ago I installed feisty on what will become a general purpose server.  I've got 4 new SATA HDDs and decided on a mixture of raid1 (for /boot) and raid5 for everything else.  I included a spare for each new md device.  The installation went fine including some rather customized partitioning, RAID setup, and LVM setup.   I've been putting this machine through its paces ever since and all is well.

Then just today I started nosing around in the logs and discovered a nerve-rattling warning in the daemon.log:
```
host1 mdadm: SparesMissing event detected on md device /dev/md0
```

Same warning for md1 and md2.  Every one of those RAID arrays is supposed to have a spare.  So I searched through the logs for other occurances.  Sure enough, this has been happening since day1.

Now the favor.  If you're running software raid with a spare, would you look through your daemon.log(s) and see if this warning is occurring for you?  Thanks!

---

### Post by Ol'man on 2007-05-08
> **marcw said:**
> discovered a nerve-rattling warning in the daemon.log:
```
host1 mdadm: SparesMissing event detected on md device /dev/md0
```

This is what it sounds like. One of your spare drives has had problems. You should investigate it.

> 
If you're running software raid with a spare, would you look through your daemon.log(s) and see if this warning is occurring for you?  Thanks!

You don't need to peek through your logs when you configure a valid MAILADDR line within /etc/mdadm/mdadm.conf (and a reasonable MAILFROM too). It's also possible to configure any other program than sendmail (e. g. some SMS or pager app). Ubuntu, at least seen on 6.10 and 7.04, installs a RAID monitoring daemon (based on the mdadm app which is the swiss army knife for md devices) that does it for you. It's enabled by default in /etc/default/mdadm.

I would recommend to play around with your RAID system a while when you are new to software RAID/Linux multiple-path (md) devices. Having a well-configured system, it would be even feasible on a production server, though no-one ever really will recommend it :-) - so do it before giving the box away.

Get familiar with mdadm options. You can simulate HDD crashs (by marking a disk 'failed'), invoke on-the-fly restoring or perform disk replacements, with or without server downtime. You will be happier when you have to cope with real emergencies.

man md
man mdadm
man mdadm.conf
cat /proc/mdstat

Regards

Olaf

---

### Post by marcw on 2007-05-10
I was pretty sure that there would be nothing wrong with this drive since it's a brand new Seagate.  But just to be sure I ran smartctl (long test) and SeaTools DOS (long test) and both confirmed there's nothing wrong with the drive.  Further, /proc/partitions - where mdadm gets its device info - shows all 4 drives.

While certainly not claiming to be an mdadm expert by any stretch of the imagination, I had acquainted myself with mdadm before I posted.  I still think there might be a bug either in mdadm or the kernel which is the reason for my original posting where I was looking for validation.

---

### Post by dazlari on 2007-10-26
I started getting this message after upgrading to Gutsy. I have 4 relatively new Seagate drives in a RAID5 that were in place and working in Feisty. At restart after the installation, the startup stopped after fsck failed to find /dev/md0:

```
# cat /var/log/fsck/checkfs
Log of fsck -C -R -A -a 
Fri Oct 26 18:11:27 2007

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Invalid argument while trying to open /dev/md0
/dev/md0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8
```

It took me a while to understand that mdadm - for a reason I still am unable to determine (help please!) - was not able to assemble the array. So I achieved it myself with the following:

```
# mdadm -A /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

Despite having the information in /etc/mdadm/mdadm.conf (and also /etc/mdadm.conf - not sure why there's two config files, but they both now have the desired information):

```
# cat /etc/mdadm.conf
ARRAY /dev/md0 level=raid5 num-devices=4 spares=1 UUID=63ed4da3:846b65a3:9af87e3b:e081059b
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
```

The manually assembled array appears completely intact, though I must do this in busybox at restart now until I figure this one out. Perhaps the conf file is flawed. The scan option of mdadm fails to assemble it. 


```
# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Sun Apr 29 18:01:49 2007
     Raid Level : raid5
     Array Size : 351654528 (335.36 GiB 360.09 GB)
  Used Dev Size : 117218176 (111.79 GiB 120.03 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Oct 26 18:43:28 2007
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 63ed4da3:846b65a3:37714b3c:70842709
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
```

Since then the SparesMissing message is noted in the syslog, despite it seems,  all system are fully operational and functioning normally ;) I'm not sure if this is something that the upgrade has broken and if I should post this in another more relevant topic.

daz

---

### Post by cyriss on 2007-12-23
Yikes, I am experiencing this same problem after upgrading a Feisty machine to Gutsy.  I'm pretty nervous about fiddling with the array (lots of data that is not backed up elsewhere, i know i know) and so wanted to check here and see if the root of this problem has been discovered.  

dazlari, did you determine how to resolve this problem (how to get the array to stay built after rebooting)?

thanks,
G

---

### Post by cyriss on 2007-12-23
ok, i got it working.  it turned out that the problem was that gutsy decided to rename my /dev/hd* devices to /dev/sd* which confused mdadm since my mdadm.conf file had the old /dev/hd* names.  i guess this has to do with recent kernel changes and fading support for old ide drivers.  why i'm just seeing this problem now (as opposed to when i upgraded to feisty) is a mystery to me since the changes supposedly happened some time ago.  anyway, just thought i'd post in case anyone else comes across this problem...

---

