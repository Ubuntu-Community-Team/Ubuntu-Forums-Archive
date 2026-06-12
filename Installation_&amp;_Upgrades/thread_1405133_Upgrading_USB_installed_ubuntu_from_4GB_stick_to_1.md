---
title: "Upgrading USB installed ubuntu from 4GB stick to 16GB"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by bwallen on 2010-02-12
I've got a persistent install of ubuntu 9.10 on a 4GB stick. That stick is slow and running out of space, so I'd like to upgrade to my much larger 16GB stick. Can I do this easily or would it be easier to re-install fresh on the 16GB stick?

---

### Post by khelben1979 on 2010-02-12
> **bwallen said:**
> or would it be easier to re-install fresh on the 16GB stick?

Yes!

---

### Post by ljwobker on 2010-02-12
Not sure I agree entirely.  ;-)

I just moved my USB installation from one 4GB USB drive to a different 4GB drive.  One nasty little wrinkle is that the "new" drive was a few MB *smaller* than the "original" USB drive.  To solve this, I just turned off swap on the original install, then shrunk the swap partition to a size that would fit.  

Then, just do a direct copy of the original drive to the new drive... to do this, boot from a LiveCD and use "dd" -- you're just making a bit-by-bit copy from the old drive to the new drive, so it picks up the partition table, the master boot record, and all of your files.

Sanity check: make sure all of your filesystems are UNMOUNTED. (hence need for liveCD)... this will *sometimes* work if you copy from a mounted partition, but better to be safe and use a liveCD and unmounted devices.

My command line was simply this... you will need to adjust your devices accordingly:

```
dd if=/dev/sda of=/dev/sde bs=8192
```then let it run for as long as it takes (depends on flash drive speeds, etc) ... I think mine ran for about 20 minutes.  When dd either runs out of input blocks to read or fills up the target device, it will print a summary of what it did and you're done.

anyway... your particular case/setup should be easier since you will not need to shrink any partitions  (you're moving to a larger drive...)    so... You should be able to:


[LIST=1]
[*]boot liveCD; check both devices are present.
[*]**MAKE 100% CERTAIN **that you know which device is 'new' vs 'old' as "dd" is quite unforgiving of such mistakes.  ;-)
[*]start your 'dd' copy of original->new
[*]go get coffee/water/soda/beer/drink of choice while waiting...
[*]boot from 'new'
[*]make sure everything works
[*]resize your 'new' partitions to larger ones, grow filesystems, etc.  (suggest gparted for this)
[/LIST]
Depending on your device location and how your boot loader works, you may have problems if the 'new' device does not show up in the same place as the 'old' device.... to reduce this risk try to have everything plugged in the same way you originally did so that your boot device "/dev/whatever" still boots as "/dev/whatever".

hope this helps...

---

### Post by stlsaint on 2010-02-12
> **ljwobker said:**
> Not sure I agree entirely.  ;-)

I just moved my USB installation from one 4GB USB drive to a different 4GB drive.  One nasty little wrinkle is that the "new" drive was a few MB *smaller* than the "original" USB drive.  To solve this, I just turned off swap on the original install, then shrunk the swap partition to a size that would fit.  

Then, just do a direct copy of the original drive to the new drive... to do this, boot from a LiveCD and use "dd" -- you're just making a bit-by-bit copy from the old drive to the new drive, so it picks up the partition table, the master boot record, and all of your files.

Sanity check: make sure all of your filesystems are UNMOUNTED. (hence need for liveCD)... this will *sometimes* work if you copy from a mounted partition, but better to be safe and use a liveCD and unmounted devices.

My command line was simply this... you will need to adjust your devices accordingly:

```
dd if=/dev/sda of=/dev/sde bs=8192
```then let it run for as long as it takes (depends on flash drive speeds, etc) ... I think mine ran for about 20 minutes.  When dd either runs out of input blocks to read or fills up the target device, it will print a summary of what it did and you're done.

anyway... your particular case/setup should be easier since you will not need to shrink any partitions  (you're moving to a larger drive...)    so... You should be able to:


[LIST=1]
[*]boot liveCD; check both devices are present.
[*]**MAKE 100% CERTAIN **that you know which device is 'new' vs 'old' as "dd" is quite unforgiving of such mistakes.  ;-)
[*]start your 'dd' copy of original->new
[*]go get coffee/water/soda/beer/drink of choice while waiting...
[*]boot from 'new'
[*]make sure everything works
[*]resize your 'new' partitions to larger ones, grow filesystems, etc.  (suggest gparted for this)
[/LIST]
Depending on your device location and how your boot loader works, you may have problems if the 'new' device does not show up in the same place as the 'old' device.... to reduce this risk try to have everything plugged in the same way you originally did so that your boot device "/dev/whatever" still boots as "/dev/whatever".

hope this helps...


NOTE: Ensure that you do a backup of the 4GB drive prior to using dd. Also if you use this process MAKE SURE that you have equal partitions of the old drive to the new drive.

---

