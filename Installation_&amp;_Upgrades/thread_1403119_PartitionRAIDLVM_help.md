---
title: "Partition/RAID/LVM help"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by kungfu71186 on 2010-02-09
I am trying to do software raid and then do lvm on top of that. How would i be able to do this and create a boot partition.

When i create a raid in the partition manager when install ubuntu it won't let me use just a portion of the raid. I want to be able to just use a portion of the raid and then use the rest for LVM.

Anyway to do this?

Thanks

---

### Post by kungfu71186 on 2010-02-10
anyone?

---

### Post by darkod on 2010-02-10
The /boot partition for software raid has to be OUTSIDE of the array usually. I can't quote you the exact options from the installer, because I haven't used it, but the general steps would be:

1. You need to use the alternate install cd, not the standard desktop one.
2. Create 200MB or 300MB /boot partition on the first disk. Create same size partition on the second disk to be the same (but I don't think it needs to be used).
3. Create partitions from the rest of the both disks.
4. Enable software raid and delegate both large partitions from the disks to it.
5. Once the array is created and it acts as single device, make it a device for LVM and continue with the steps.

Sorry I can't help more, I haven't done this before, but this is what I would look for.

Also, this might give you some ideas:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Separate topic, LVM configuration in 8.10 with screenshots, this covers only the LVM but once you have the raid device as device, you should be able to figure it out:
[http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/](http://linuxbsdos.com/2008/11/11/lvm-configuration-in-ubuntu-810/all/1/)

---

### Post by kungfu71186 on 2010-02-10
I see, ill try something. You gave me an idea. hopefully it works. Thanks.

---

### Post by kungfu71186 on 2010-02-10
In case anyone needs to know:

I created a partition on one of the disks for the boot.
Then i created the raid with all the disks.

I did it with 5 hard drives - all the same size - raid 5
Only exception was now the first hard drive i created the boot partition on was smaller than the rest.

When i created the raid it used up all the space it seemed like on the remaining hard drives instead of resizing them down to the size of the first one.

What i am going to try next anyway is to create partitions on all the hard drives and create 2 raids. The first one will be around 200-300MB and it will be used for the boot. The second one will be the remaining space used for LVM.

---

### Post by oshunluvr on 2010-02-12
Technically with software RAID you can boot off of a RAID1 partition if you set it up correctly - but it's easier to use a non-RAID partition as /boot have a second backup /boot partition.

Since you have five drives it's easy enough to find space for a second /boot somewhere. My /boot using kubuntu is currently only 55mb. 

If your looking for more performance what about:
1. a separate RAID0 device for **/tmp**
2. five small swap spaces one per drive as primary partition 1 and set "pri=1" for all of them in fstab
3. using a RAID0+1 scheme for your install** /**
4. using RAID5 for **/home**

This wouldn't take more than an hour or two to setup plus it'd be a good learning tool!

---

