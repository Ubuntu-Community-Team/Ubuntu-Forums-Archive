---
title: "boot failure, cloned partition to new disk, after boot-repair no boot"
date: 2016-09-14
forum: Installation &amp; Upgrades
---

### Post by jeffbourassa on 2016-09-14
[FONT=Helvetica Neue]Problems getting a cloned/restored volume to boot after using boot-repair

paste.ubuntu.com/23179734/


Hoping for some help with why not?  I have been working on this for a couple days now, can get the partition and data copied over to a new disk/new partition but can't get the system to boot.


Thanks


Jeff




[/FONT]

---

### Post by oldfred on 2016-09-14
Little strange that swap is sda1 and install is sdb1.

You have lots of kernels, once you get it going best to houseclean.

UUID in fstab does not match UUID. Did you clone or partition and copy data?
And install in fstab says sda, but grub is looking for hd1,1

 Your fstab:
# / was on /dev/sda1 during installation
UUID=[COLOR=#ff0000]0177b6f1-d8f5-4b7b-ba91-36a2d2676f04[/COLOR] /               ext4    errors=remount-ro 0       1 

   Your UUID, grub entries match this UUID, not fstab
/dev/sda1        7500df2d-947e-40c2-8c3d-7bab33cf3993   swap       
/dev/sdb1        [COLOR=#ff0000]1f643abf-e4db-473c-a020-6b285365e9ae[/COLOR]   ext4        

If drive boots as sdb, hd1 then you may only need to edit fstab.

---

### Post by jeffbourassa on 2016-09-14
Bit more history.

Original disk - 1.6Tb disk, sda - deleted a bunch of files (1.5Tb worth), only 30G left after shrink - booted fine
sdb was the 8G swap drive

Now want to move system to a new disk

Added a 120Gb drive, new drive - created a blank partition, booted from liveCD - rsync copy of files from big 1.6Tb disk to 120Gb disk  (about 30G of files)

Then removed big disk, restarted from liveCD and ran boot repair - I have 2 drives, 120Gb (sdb) and 8G swap (sda).

I updated the fstab file, updating the UUID to point to sdb's UUID - on boot, sits at a blank screen with a cursor.

I feel like this is really close to working but I am running out of ideas.

---

### Post by oldfred on 2016-09-14
If you hold shift key do you get grub menu?
With only one install grub will not normally show.
And then can you boot recovery mode?

---

