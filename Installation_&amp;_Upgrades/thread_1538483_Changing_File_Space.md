---
title: "Changing File Space"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by DrewCollins on 2010-07-25
Hey, I know this has been posted and reposted a million times but I'm new to Ubuntu and have no idea what I'm doing.  I installed it using the download on the website and accidentally set my file space fairly low when I was installing it.  How to I change it, I don't have a disk or anything and you are going to have to explained this as though you're talking to a 5 year old because I don't know anything.

Thanks in advance,
Drew :D

---

### Post by quixote on 2010-07-27
What follows assumes you installed ubuntu to its own partition ("drive") rather than under Windows in a wubi install.  I haven't used wubi, so I'm not sure how you'd do it then.

1) You need some way to boot ubuntu that doesn't use the drive you're trying to enlarge.  If you installed from a livecd, and you still have that, that's all you need.  If you don't, download one from ubuntu.com and burn a cd.  (If you want more detail on that, just say.)

2) Boot with the livecd.  Go to System > Administration > Gparted. (Stands for gnome partition editor.)  MAKE SURE IT'S WORKING WITH THE RIGHT DRIVE.  You can tell by the size and the different partitions on it.  Eg. you know the first 115GB should be Windows (ntfs) and the last 5GB are ubuntu (ext3, or ext4).  If it doesn't look right, go to the Gparted menu at top left, then Devices, and try another drive.

3)In the example above, your next step would be to a) shrink the Windows partition, then b) enlarge your ubuntu partition into the free space, which will also move all the files in it up to the beginning of the partition.  The next time you boot Windows, it'll notice the change in size and want to run a disk check.  That's not a problem.  Just let it run.

To give you more precise info, say how big your drive is, how it's arranged (i.e. what's first, second, third, etc, and how big each partition is), and which one you want to shrink to make ubuntu bigger.  All this is actually very easy.  Just tedious. :D

---

### Post by DrewCollins on 2010-07-28
> **quixote said:**
> What follows assumes you installed ubuntu to its own partition ("drive") rather than under Windows in a wubi install.  I haven't used wubi, so I'm not sure how you'd do it then.

1) You need some way to boot ubuntu that doesn't use the drive you're trying to enlarge.  If you installed from a livecd, and you still have that, that's all you need.  If you don't, download one from ubuntu.com and burn a cd.  (If you want more detail on that, just say.)

2) Boot with the livecd.  Go to System > Administration > Gparted. (Stands for gnome partition editor.)  MAKE SURE IT'S WORKING WITH THE RIGHT DRIVE.  You can tell by the size and the different partitions on it.  Eg. you know the first 115GB should be Windows (ntfs) and the last 5GB are ubuntu (ext3, or ext4).  If it doesn't look right, go to the Gparted menu at top left, then Devices, and try another drive.

3)In the example above, your next step would be to a) shrink the Windows partition, then b) enlarge your ubuntu partition into the free space, which will also move all the files in it up to the beginning of the partition.  The next time you boot Windows, it'll notice the change in size and want to run a disk check.  That's not a problem.  Just let it run.

To give you more precise info, say how big your drive is, how it's arranged (i.e. what's first, second, third, etc, and how big each partition is), and which one you want to shrink to make ubuntu bigger.  All this is actually very easy.  Just tedious. :D

Thanks but I used a Wubi installer.  It's OK now though. :)

---

