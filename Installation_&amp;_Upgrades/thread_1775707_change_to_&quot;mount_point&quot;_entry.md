---
title: "change to &quot;mount point&quot; entry ??"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by DouglasAdams on 2011-06-05
re: "all variants"
tried this in Ubuntu & Xubuntu, presume same in Kubuntu

in an earlier post i mentioned, just in case it might be relevant:

> **DouglasAdams said:**
> 
the only strange thing during the install was that when i was manually allocating partitions i was unable to specify my data drives as i could not type in the mount point box,
e.g.
in the mount point box i usually enter:
    /home/data1  etc


background:
> **DouglasAdams said:**
> booted 11.04 from pendrive.
copied hd to usb drives and ran my life for 3 days.
formatted my hd, guid (was mbr), setup my preferred partitions
i.e. boot, root, home, 3 data partitions plus a swap.
tried swap at start of drive and at end - same problem.


this happened a couple of times with ubuntu with the swap file at the end of the drive then once with the swap file as the first partition.
then i tried xubuntu, with the swap moved back to the end of the drive, and had the same problems with the mount point box, i.e.
i was only able to select a "pre-ordained" entry - i could not type in the selection box to add **my** personal file systems.

why is this?
have this been changed?  it clearly works differently to 10.10.
why has it been changed?  it is obviously needed and worked great !

---

### Post by Hedgehog1 on 2011-06-05
This was not a planned change in the install, it was a bug found too late to get fixed for the final pull.

The ability to type in your own mount points will return.

I have been suggesting that folks make a copy of their /etc/fstab file before the install, and then copying the additional mount points form that copy into the new /etc/fstab.


***The Hedge***

:KS

---

### Post by DouglasAdams on 2011-06-05
cheers Hedge.

actually, i do have a copy of my /etc/fstab but, as i reformatted one drive, with totally different partition sizes, and my reason for doing this is to trash the other drive (after ensuring i've got all my data) so my old /etc/fstab wouldn't have been any use to me in this particular instance.  great reminder though.

any idea when this feature might be fixed please?
will i need to wait for DOT 1?
if so, any idea when that might be plz?

thanks again

---

### Post by kansasnoob on 2011-06-05
Here's the bug report:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/769043)

You can type the correct mount point in something like gedit, then copy-n-paste it into the ubiquity window.

---

### Post by kansasnoob on 2011-06-05
It won't be fixed in 11.04 but it's currently fixed in 11.10 Alpha1. But you don't want the Alpha1, it's very unstable!

---

### Post by DouglasAdams on 2011-06-05
cheers Kansas.
is there not going to be a point release for 04 then?

---

