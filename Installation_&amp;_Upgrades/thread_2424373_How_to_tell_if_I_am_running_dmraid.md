---
title: "How to tell if I am running dmraid?"
date: 2019-08-07
forum: Installation &amp; Upgrades
---

### Post by mogrify2 on 2019-08-07
I configured the BIOS with a (fake-raid) 5-disk RAID5 config.
The installed Ubuntu on two Dell desktop servers specifying to use fake raid and entering exactly the same config as in the BIOS.

Now I am not sure whether we are running mdadm or dmraid and not sure how to tell. They both seem to list the disks.

Any help much appreciated as I have to debug a problem with it and not even sure which one I am working with here.
```
root@mg2:/home/gough# dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs
```
```
root@mg2:/home/gough# dmraid -s
*** Group superset isw_cagejhggbf
--> Subset
name   : isw_cagejhggbf_Volume0
size   : 14846582784
stride : 128
type   : raid5_la
status : ok
subsets: 0
devs   : 5
spares : 0
```
```
root@mg2:/home/gough# dmraid -r
/dev/sda: isw, "isw_cagejhggbf", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdc: isw, "isw_cagejhggbf", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sde: isw, "isw_cagejhggbf", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdb: isw, "isw_cagejhggbf", GROUP, ok, 3907029166 sectors, data@ 0
/dev/sdd: isw, "isw_cagejhggbf", GROUP, ok, 3907029166 sectors, data@ 0
```
```
root@mg2:/home/gough# dmraid -s -s isw_cagejhggbf
ERROR: either the required RAID set not found or more options required
no raid sets and with names: "isw_cagejhggbf"
```
```
root@mg2:/home/gough# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md126 : active raid5 sda[4] sdb[3] sdc[2] sdd[1] sde[0]
      7423287296 blocks super external:/md127/0 level 5, 64k chunk, algorithm 0 [5/5] [UUUUU]
      
md127 : inactive sdd[4](S) sdc[3](S) sdb[2](S) sda[1](S) sde[0](S)
      26005 blocks super external:imsm
       
unused devices: <none>
```
```
root@mg2:/home/gough# mdadm --detail /dev/md126
/dev/md126:
         Container : /dev/md/imsm0, member 0
        Raid Level : raid5
        Array Size : 7423287296 (7079.40 GiB 7601.45 GB)
     Used Dev Size : 1855821824 (1769.85 GiB 1900.36 GB)
      Raid Devices : 5
     Total Devices : 5


             State : active 
    Active Devices : 5
   Working Devices : 5
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-asymmetric
        Chunk Size : 64K
```


Consistency Policy : resync
```
              UUID : 1460e363:36bb479d:6caeffc6:a5ffe2ef
    Number   Major   Minor   RaidDevice State
       4       8        0        0      active sync   /dev/sda
       3       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       1       8       48        3      active sync   /dev/sdd
       0       8       64        4      active sync   /dev/sde
```

---

### Post by #&amp;thj^% on 2019-08-07
Try:
```
sudo dmraid -s
```

---

### Post by TheFu on 2019-08-07
I thought dmraid was deprecated a few LTS releases ago.  [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1028677](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1028677) says that mdadm has been used on new installs since 14.04.

---

### Post by #&amp;thj^% on 2019-08-07
It's still going, and some devices need it. 
 dmraid uses the Linux device-mapper to create devices with respective
 mappings for the ATARAID sets discovered.
 .
 The following formats are supported:
[list]
  [*]Highpoint HPT37X/HPT45X
  [*]Intel Software RAID
  [*]LSI Logic MegaRAID
  [*]NVidia NForce RAID (nvraid)
  [*]Promise FastTrack
  [*]Silicon Image(tm) Medley(tm)
  [*]VIA Software RAID[/list]
 .
 ***Please read the documentation in /usr/share/doc/dmraid BEFORE attempting***
 any use of this software. Improper use can cause data loss!
[https://launchpad.net/ubuntu/bionic/amd64/dmraid/1.0.0.rc16-8ubuntu1](https://launchpad.net/ubuntu/bionic/amd64/dmraid/1.0.0.rc16-8ubuntu1)
And: [http://manpages.ubuntu.com/manpages/bionic/man8/dmraid.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/dmraid.8.html)
I agree though I like to use "mdadm" for my set-up's.

---

### Post by mogrify2 on 2019-08-08
Thanks 1fallen, I already posted the dmraid -s output
My problem is interpreting it as both dmraid and mdadm seem to be reporting positively (with the exception of [COLOR=#000000][FONT=&quot]dmraid -s -s isw_cagejhggbf[/FONT][/COLOR])

... so I can't tell which one is actually controlling the volume before I go and start messing with it

---

### Post by mogrify2 on 2019-08-08
I am wondering, is it possible I somehow accidentally set up both, and they are interfering with each other?

---

### Post by #&amp;thj^% on 2019-08-09
> **mogrify2 said:**
> Thanks 1fallen, I already posted the dmraid -s output

So you did, :) If stuff isn't in code tags I really don't bother reading a lot.
Not trying to sound rude or harsh, but code tags are very important here. ;)

For raid5 you need the dm-raid module, but not for a raid0.

FYI, unless you are dual booting with Windows you should use conventional linux md raid rather than fake/dmraid, as md is far better supported and properly handles failures and reshapes, which fakeraid does not.

If you want to boot an IMSM/ISW raid with dmraid and without mdadm, you still have to install the mdadm package in a kickstart minimal install and have to specify "noiswmd" or "rd_NO_MDIMSM" on the kernel command line.+When booting an IMSM/ISW RAID with dmraid but without mdadm, the mdadm package still needs to be installed on the system in a kickstart minimal install with the "noiswmd" or "rd_NO_MDIMSM" parameters specified.

---

