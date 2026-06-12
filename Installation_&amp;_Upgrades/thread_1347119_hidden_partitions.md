---
title: "hidden partitions"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by ceph8 on 2009-12-05
I have used ubuntu before but each time i got a new windows os (xp, vista, 7 and now back to Xp) i installed a new ubuntu and they are all on my hard drive but i was wondering if there was a way I could get rid of some of the old partitions and make them become a part of the normal external harddrive again???

---

### Post by phillw on 2009-12-05
> **ceph8 said:**
> I have used ubuntu before but each time i got a new windows os (xp, vista, 7 and now back to Xp) i installed a new ubuntu and they are all on my hard drive but i was wondering if there was a way I could get rid of some of the old partitions and make them become a part of the normal external harddrive again???

Yes, there is. do you need data off them, or just to delete & merge them back to the general area 

(BORG -- ASSIMILATION -- RESISTANCE IS FUTILE) -- soz if you don't know of the Borg ;-)

You want Gparted to delete & merge partitions, a good read up on it is here --> [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Or you can just post what u need to do & we can 'talk' you through it.
Can you post the output of
 ```
sudo fdisk -l 
```
and 
```
df -ah | grep dev
```

Before and After you have gone to Places and mounted every device that is listed.

Cheers,

Phill.

Phill.

---

### Post by misterbk on 2009-12-05
Partitions can be deleted.  There are a variety of ways, some of them probably have a nice GUI.  (anything I know about that is outdated though, I always partition Linux during install and haven't had to mess with it afterwards.)

Deleting a partition erases everything on it.  (Just in case!)

If the empty partition is before the Linux partition, it might be easiest and safest to just keep it there, format it as something usable, and mount it in your Linux using FSTab.  I have something like this mounted as "/basement" on one machine and "/music" on another.

Advantage of that would be not changing the partition numbers.

---

### Post by Bartender on 2009-12-05
Under my sig is a link that'll get you started with GParted LiveCD.  

I love GParted  :)

If you download the latest stable .iso and create a bootable disc like you would an Ubuntu LiveCD, you end with a handy partitioning tool on a bootable CD.

It takes a bit of scratching around in GParted to figure out how to do what you want to do, but it's not hard.  I've found Gparted to be a wonderfully helpful tool for all kinds of things.

In your case, let's say you want to install Windows to part of a drive before installing Ubuntu.  You don't want to screw around with defragging and trying to squish Windows into its corner.  Use GPLCD to wipe all partitions out, then create a primary NTFS partition out of half of the drive.  When you pop the Windows install disc in, it will only see the NTFS partition and install there.  The rest of the disk is ready for Ubuntu

---

