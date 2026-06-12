---
title: "Server 20.04 install on RAID0"
date: 2022-04-23
forum: Installation &amp; Upgrades
---

### Post by hddvd01 on 2022-04-23
Trying to setup RAID0 on a server 20.04. I have 2 new NVME drives and the ubuntu installer is only showing 1 drive as multipath. If I use shell and run lsblk then I see both drives. The desktop installer sees both drives no issue. Is there a way to get the server install to see both drives? I have to perform the following steps in shell every time before I continue through the installer: [https://saelzler.com/tech/disable-multipath-for-identical-nvme-drives-on-ubuntu-server/](https://saelzler.com/tech/disable-multipath-for-identical-nvme-drives-on-ubuntu-server/)

Secondly, if I create the partitions and RAID0 array manually in shell, the ubuntu server installer crashes when I go through all the steps. If I format both drives so there are no partitions, and I create the RAID array using the installer, it still crashes.

---

### Post by QIII on 2022-04-23
Hello!

We would prefer that users not cut and paste their questions asked on other forum venues (assuming that this question was, in fact, yours and not a prelude to spam).  Please demonstrate some courtesy for our users by asking your question rather than copying it verbatim from elsewhere. 

We particularly do not care to have unsupported formatting and fonts pasted.

---

### Post by TheFu on 2022-04-23
Using RAID0 for an OS install is extremely suspect. It just isn't needed.  What you can do is setup the partitions on 1 NVMe to be the size needed, not larger. That would typically be 35G for /, perhaps 2G for /var/.
Then take the remaining storage on NVMe-A and NVMe-B creating a RAID0 stripped data partition.  If it were me, I'd use LVM for this, since LVM supports striping LVs withing the same VG with many performance tuning options.  The RAID0 aspects can all be added post-install.  It isn't like the OS performance will notice the difference between non-striped and striped NVMe storage.

Where it will make the most performance difference is with scratch files for video editing of 4K and 8K video files.

Plus, if anything bad happens related to RAID0 storage, the OS will likely still boot.  That's a win in my book too.
Now, if you want to setup the OS as RAID1 and data as RAID0, I could get behind that ... also using LVM for the RAID1 and RAID0 areas.  A little reading on **lvconvert** may open your eyes about this.  No need for mdadm, btw.
From the lvcreate manpage:
```
       RAID LVs can be created by specifying an LV type when creating  the  LV
       (see  lvmraid(7)).  Different  RAID levels require different numbers of
       unique PVs be available in the VG for allocation.
```

From the lvconvert manpage:
 ```
      In most cases, the mirror type is deprecated and the raid1 type  should
       be used.  They are both implementations of mirroring.

       Striped raid types are raid0/raid0_meta, raid5 (an alias for raid5_ls),
       raid6 (an alias for raid6_zr) and raid10 (an alias for raid10_near).
```

LVM brings all sorts of enterprise storage capabilities that have been proven for decades.

---

### Post by hddvd01 on 2022-06-20
Really appreciate the response and I'm sorry about the delay in responding. I'm actually still trying to get this all figured out. One thing that is frustrating is that the Ubuntu installer will use something called Multipath to group my drives together? I can get it to eventually see them as different disks, but i have to run this command every time I start the installer:

```

#/etc/multipath.conf


blacklist {devnode "^nvme[0-9]"}


sudo systemctl restart multipathd

```

Any ideas on how to get the installer to see my disks as separate? They are in 2 different physical M.2 slots.

---

