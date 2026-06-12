---
title: "software raid impact of different partition start/end"
date: 2012-12-07
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2012-12-07
I currently booting off a RAID 1, but need to move to different disks.

All pretty straight forward, by adding the new disks to the aray as spare and failing the exiting ones.

I did notice, however that the existing disk partitions are as follows:

 /dev/sde1   *          63    58589054    29294496   fd  Linux RAID autodetect

while the new disks are as follows:

/dev/sdc1            2048    61442047    30720000   83  Linux

Will the difference in the start/end cause any problems?

---

### Post by darkod on 2012-12-07
These days it's standard the first partition to start at sector 2048 which means 1MiB (one sector is usually 512B except on some 4k disks where it is 4KiB).

The start sector is not relevant, but the partition on the new disk has to be equal or larger than the partition of the disk you are trying to replace. As far as I can see, that condition is also met.

However, you will have to change sdc1 from code 83 (Linux) to code fd (Linux RAID). I usually use terminal and cfdisk to change partition codes. Once partitions with code fd will be accepted by mdadm.
sudo cfdisk /dev/sdc

As for replacing the disk, you don't have to set the new as spare, and then fail the old. Since this is raid1 which can work if one disk fails, you can fail and then remove the old disk, and then add the new one. This link can give you some ideas but you don't have to do it exactly the way they did it:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

For example, they use fdisk to "copy" the partitions layout from one disk to the other before adding the new one, but I would rather prepare the partition manually. And once you have the partition created, simply add it to the correct md device.

---

### Post by lister171254 on 2012-12-07
Thanks for the quick response and the link.

one more question.

Do I need to set the boot flag too?

Will let you know how I go

---

### Post by lister171254 on 2013-01-28
Have moved to the new disks successfully, but have one final question and it's about the raid flag.

I did create the new raid with two disks without setting the raid flag. They came up ok and there were no problems, so my queston is: 

What's the purpose of the flag.

Thanks,

---

### Post by darkod on 2013-01-28
> **lister171254 said:**
> Have moved to the new disks successfully, but have one final question and it's about the raid flag.

I did create the new raid with two disks without setting the raid flag. They came up ok and there were no problems, so my queston is: 

What's the purpose of the flag.

Thanks,

I set it manually before hand but it seems the mdadm is configuring the flag (or it doesn't need it) during the creation of the md device. So, even if you don't have the raid flag in advance, it will create the md device correctly.

Since you never set it manually, it's interesting to see whether mdadm did. Do the raid partitions have a raid flag now in parted?

---

### Post by lister171254 on 2013-01-28
Thats the interesting thing; they didn't. mdadm happyly assembled the raid without the flags.


I set the flag before switching the newhome for the old just to make sure the two raids were the same, but originally, the newhome taid did not have the raid flag set.

---

