---
title: "Installing Ubuntu 10.10 Server or Alternate with RAID1"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by Packetloss on 2010-10-20
I bought another [HDD]("http://www.afuture.nl/products/12563/HD154UI_Samsung_HD154UI.html") to install Ubuntu 10.10 Server in a RAID1 SoftwareRaid configuration. After lots of reading, including [Advanced Installation]("https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html"), I cannot understand why option 8 in last named link doesn't work: whatever I do and try, the boot flag cannot be changed. I tried both the Server and the Alternate installers, both will keep the boot flag 'off' and cannot be changed.
Anyone knows if this is a bug in the 10.10 installer?

By the way: the installer finished correctly and the system boots. Even with one of the two SATA drives disconnected :).

---

### Post by chideock on 2010-10-26
I have been asking the same question in the "Server Category". Same issue with the "boot flag" in instruction 8. I was using the server alternate CD to install.


New info

What I have found  out is that this set of instructions is wrong, at least for the  most current versions of Ubuntu 10.10 and Ubuntu server.

Use this link as a guide [http://www.youtube.com/watch?v=-x2rZe2Z9as&NR=1](http://www.youtube.com/watch?v=-x2rZe2Z9as&NR=1)

It works and one finds that one does not have to even bother with the "boot flag"

---

### Post by udippel on 2010-11-18
> **chideock said:**
> 
New info

What I have found  out is that this set of instructions is wrong, at least for the  most current versions of Ubuntu 10.10 and Ubuntu server.

Use this link as a guide [http://www.youtube.com/watch?v=-x2rZe2Z9as&NR=1](http://www.youtube.com/watch?v=-x2rZe2Z9as&NR=1)

It works and one finds that one does not have to even bother with the "boot flag"

Could you just write it up quickly, please? Youtube is very slow here. Also, I want RAID1; not RAID0.
Please, what's the trick??

---

### Post by udippel on 2010-11-18
> **udippel said:**
> Could you just write it up quickly, please? Youtube is very slow here. Also, I want RAID1; not RAID0.
Please, what's the trick??

No answer?
So I'll wrap up what I found out myself, and tried out here:

The trick not mentioned in the 'official' documentation is, that it needs to go in three steps:
1. create all the slices on all disks that you want to assemble later. Make sure to identify them as 'Physical volume for RAID'.
2. 'Configure software RAID' 
3. 'Create MD device', where you select the RAID-level

You may as well create more than one partition using RAID, and you can create all the slices (see 1., above) in a single go for all RAID partitions that you will assemble later. Then you assemble all the RAID partitions in MD devices. 
What you need to see in the end, are RAID partitions in the partitioner above your physical drives. 

Only then, and only then, can you select the file system types (Ext4, e.g.) and the mount points when you move the cursor over these RAID file systems created above your physical disks.

---

