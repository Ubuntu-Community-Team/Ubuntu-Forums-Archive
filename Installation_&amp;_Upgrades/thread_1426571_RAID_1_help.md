---
title: "RAID 1 help"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by stringman10 on 2010-03-10
This is a clean install of Ubunto 9.10 using the alternate CD install. I'm using this to setup software RAID 1 at install for a home file server. I have a pair of 250GB drives (OS + storage) and a pair of 500GB drives (storage).

So here's what I did. I set a primary partition (EXT4) of 25G for /, logical partition for swap space of 1G, balance set up as logical partition EXT4, named /files2. This was on the 250 G drives (both configured identical). On the 500G drive, I set the entire drive to be FAT32 and called it /files. Both drives partitioned the same way.

Went into "Configure Software Raid" and selected the Create MD Device (RAID 1) for each partition to be mirrored, that would be / and /files2 on the 250G drive and /files on the 500 G drive. Once completed I hit finish. I received an error stating that "No root file system is defined". When I went back to the partition screen, it showed my 3 Raid 1 devices, but all of the partition types now showed raid (instead of EXT4 or FAT32) and the mount point (/, /files2, /files) were gone.

What did I do wrong? Thanks in advance.

---

### Post by psusi on 2010-03-10
You format the drive to have a raid partition on it, and that partition becomes part of the raid device.  You then use the raid device to install your filesystem on.  It sounds like you created normal partitions, then went back and blew them away ( thus throwing out your mount point assignments ) and replaced them with raid partitions.

---

### Post by stringman10 on 2010-03-10
I followed the procedure here:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

So if I read you correctly, first set up raid on both pairs of drives, then set up the partitions? Thanks.

---

### Post by stringman10 on 2010-03-11
I guess I didn't follow the procedure as closely as I thought. My issue was that after creating my partitions and then creating the RAID 1, I needed to go back and reconfigure the new RAID 1 partition. Once I did that it was smooth sailing.

---

### Post by spbitticks on 2010-03-12
Just found the solution myself.  After configuring the RAID, the drive listed under the RAID category should be selected, and the use configured to "/" (root).  

Heya,

I'm facing exactly the same issue you described above.  However, I don't know what you meant by going "back and reconfiguring the new RAID 1 partition."  Could you please give an explicit description of what you did after configuring the RAID (as in the tutorial [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID"))?

Cheers!

---

