---
title: "Trouble with Gparted in fresh install"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by deavik on 2006-07-14
Hello!

[ Firstly, I have read other threads which describe problems with partitioning in the Dapper install and I have tried some of the suggestions, but I couldn't get anything similar to my experience ]

I received my Dapper ShipIt CD today, and have been trying to do a fresh install with it but I am having trouble with Gparted.

I have 2 HDs partitioned thus:
```

hda1: ntfs
hda2: ext3 (/ from Breezy install)
...
hda5: swap (from Breezy install)

hdb*: My Windows XP installation uses these partitions
```

hda is the primary master, hdb primary slave and these are ATA disks. With the new install, I want / to be at hda2, swap at hda5.

THe problems are that while install, after I get to the Gparted "manually edit partition table" screen:

1. Gparted shows the **whole** of hda as "unallocated space". Running Gparted before starting the install yields the same result. **However**, "disks-admin" can read all the partitions on hda properly.

Further, Gparted says it cannot understand the DiskLabel on hda, it can read hdb's disklabel (msdos). (I don't know what a Disk label is!)

2. If I skip the partitioning (my partitions are already there!), set the mount points properly and click "Install" it gives me a error "No Root File system" and throws me back to the partitioning step.

I suspect the culprit is Gparted, but I don't see what I can do to install Dapper. Thanks for any help! :-?

---

### Post by aysiu on 2006-07-14
GParted is the culprit, and you're not the first to notice that it's buggy in Dapper.

You have a two choices:

1. Use a different partitioning tool (I highly recommend DiskDrake, which is available on the PCLinuxOS CD).

2. Use the Alternate CD instead of the Desktop CD. People seem to have fewer problems with that.

---

### Post by deavik on 2006-07-14
Hi aysiu, thanks for the reply! :)

If possible I'm trying to avoid downloading the CD image (I have a 1 GB data transfer cap per broadband billing cycle). Your other suggestion:
 
> **aysiu said:**
> 
1. Use a different partitioning tool (I highly recommend DiskDrake, which is available on the PCLinuxOS CD).

... sounds interesting! As I said, my partition tables are exactly like they were when I had Breezy installed and I don't need anything changed. disks-admin can format the ext3 partition - other than that I don't really need a partitioning software.

But Dapper quits the install process right after I set my mount points ("No Root File system"). How do I force it to accept the mount points I provide and carry on with the installation?

Thanks

---

### Post by aysiu on 2006-07-14
Sorry. So basically everything's working right except for the mount points not being accepted.

Can you post a screenshot of your mount points and then error?

---

### Post by deavik on 2006-07-14
> **aysiu said:**
> 
Can you post a screenshot of your mount points and then error?
Sure! I went on a screenshot spree:

Mount points:
[[IMG]http://img352.imageshack.us/img352/2838/mountpoints6ay.th.png[/IMG]](http://img352.imageshack.us/my.php?image=mountpoints6ay.png)

^^ Notice that here hda2 / hda5 are recognized. I tried removing the hdb mount points also, to no avail.

Error:
[[IMG]http://img179.imageshack.us/img179/38/error4ob.th.png[/IMG]](http://img179.imageshack.us/my.php?image=error4ob.png)

Apart from Gparted telling me the whole of hda is unallocated space, here is the "Confirmation screen" the Dapper installer gives me (it doesn't list any partitions at all!):
[[IMG]http://img179.imageshack.us/img179/3629/confirmation3sa.th.png[/IMG]](http://img179.imageshack.us/my.php?image=confirmation3sa.png)

---

### Post by aysiu on 2006-07-14
That's weird. I'm not sure what to tell you, to be honest.

---

### Post by deavik on 2006-07-14
> **aysiu said:**
> That's weird. I'm not sure what to tell you, to be honest.
:p

One thing I could use some information with: does the alternate CD also use Gparted or does it use some other partitioner?  The other option, ofcourse is to try and get the partitioner to wipe hda and lose all the data on it... :(  

There seems to be a bug report on this too: [https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/37872](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/37872)

Apart from this, running from the live CD, it took me seconds to set up my networking, so kudos there to the Ubuntu team! Everything looks really sleek as well!

---

### Post by deavik on 2006-07-16
> **deavik said:**
> 
One thing I could use some information with: does the alternate CD also use Gparted or does it use some other partitioner?
Sorry for the bump, but I really do need this information!

Thanks

---

### Post by gary4gar on 2006-07-20
sorry for digging this thread but guys i also facing this problem.also for what should i use partion managers because i have already allocated a partion for it.here my prob

================================================================
i got the desktop version upgrade from 5.10  is not possible though, so i format my ext3 partion for a freash install but there so problem.i have the following partions 80gb sata
1)c:win xp[ntfs](6.81)
2)d:ubuntu [ext3](6.43)
also first d: was 6.81 only but i created 384ms swap partion out of it.
3)e:data so no os[ntfs](30.4)
4)f:data so no os[ntfs](30.4)

when i try to install the then i select sda2 as ROOT("/") and sda6 as SWAP and proceed with install but the installer says while installing no root partion found.is this a bug?? if so any fixes available to it. pls help guys.

---

### Post by ubuntu_demon on 2006-07-20
I'm not an expert on gparted. But you can try this (on your own risk) :

-The alternate install cd (download it here : [http://www.ubuntu.com/download](http://www.ubuntu.com/download))
-gparted live cd (which has a newer version of gparted) : [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
-doing the partitioning with parted (or other tools) in the terminal (if you are a power user otherwise you might mess up your system)

---

