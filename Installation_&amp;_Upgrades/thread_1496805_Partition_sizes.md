---
title: "Partition sizes"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by rap3point0 on 2010-05-29
I plan on installing Ubuntu 10.04 and it will be my first Ubuntu install.  I plan on dual booting with windows 7 and I would like advice on partition sizes.  I have a 250 GiB drive and my planned partitions are as follows.

sda1 (PQSERVICE) 12GiB This was pre-installed should I delete it
sda 2 (System Reserved) 100MiB This was also pre-installed should I delete it
I know one of the above is the windows recovery partition but I don't know which one
sda 3 (Gateway) 25 GiB This will contain windows will 25 GiB be enough 
Extended partition
   Logical 1 10 GiB / the main Ubuntu partition 10 GiB should be enough
   Logical 2 1 GiB /home this will just hold settings so 1 GiB will be enough right?
   Both above partitions are ext3
   Logical 3 3 GiB swap partition I have 1 gig ram upgradeable to two
   Logical 4 180 Gib shared NTFS partition

I am new to Ubuntu and would like to know if you think this is proper. I have already defragmented the hard drive and will make the partitions in Gparted on Ubuntu live test from usb drive.
Thanks in advance

---

### Post by darkod on 2010-05-29
sda1 is your recovery/restore partition.
sda2 you can't delete, it is the win7 small 100MB boot partition holding its boot files. If you delete it, win7 can't boot.
sda3 25GB is a little tight for win7, but if you delete the hibernation file (if you are not using hibernation) it might be OK. I would recommend to make this 30GB.

When shrinking sda3 use win7 Disk Management. Do not create any partition in the unallocated space. Boot win7 few times to do its disk checks. After win7 is happy after the shrink, proceed with installing ubuntu.

logical1 is fine but still I would give it 15GB for / if you can spare the space.
logical2 also, better at least 5GB if you can spare

PS. I also have 250GB disk so here is my example:

sda1 win7 ultimate system partition 65GB (I wanted to be on the safe side, but at the moment I have only 25GB used, the hibernation is disabled and that deletes the hibernation file which can be 6-7GB)
sda2 ntfs data 141GB
sda3 ext4 / 15GB

extended
logical1 swap 2GB
logical2 ext4 /home 10GB

---

### Post by rap3point0 on 2010-05-29
Thank you very much for your time.

---

### Post by darkod on 2010-05-29
> **rap3point0 said:**
> Thank you very much for your time.

No problem. Did you see my PS also?

---

### Post by rap3point0 on 2010-05-29
Yes great example thank you for all the help

---

