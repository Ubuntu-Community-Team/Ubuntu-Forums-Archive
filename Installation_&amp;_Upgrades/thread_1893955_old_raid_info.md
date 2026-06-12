---
title: "old raid info"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by jhayes on 2011-12-11
i have several 2 TB drives in ubuntu box. there is a "fantom" raid getting in the way. ideally i want all the drive parts to be in /dev/md0. 5 of the drives were in a raid array at some point.  it's as if they are trying to be both in the 5-drive fantom array and the real 7-drive array. trying to have /etc/fstab automount the7-drive array has not yet worked. getting the UUID info sometimes it starts with a 5, other times a 7. sometimes the 7-drive array is at /dev/md1, and sometimes /dev/md/bigarray1  (bigarray1 is the label i gave it). How do i completely remove raid array info from the individual drives? or what can i do to do away with the fantom raid ?

---

### Post by darkod on 2011-12-11
Was the old array software raid or some kind of fakeraid (mobo raid)?

You delete software raid meta data with:
sudo mdadm --zero-superblock /dev/sdX

But if you already created the new array, it will probably remove that data too. I don't know if you should run that if you have data on the array. You should have done it before creating a new array.

Before running it, you also might need removing the disks/devices from the raid:
sudo mdadm --manage /dev/mdX --remove /dev/sdXY

But again, if you plan to keep the data on it, you should investigate first what will happen to the data.

---

### Post by jhayes on 2011-12-11
the drives/arrays were/are linux mdadm array, not mobo fake raid. 
i don't mind blowing out the array/data on the 7-dri ve array.
i have copied stuff to it, but i still have the source data. 
i think after i reload the os (was on a flash drive, acquired a hdd).

---

