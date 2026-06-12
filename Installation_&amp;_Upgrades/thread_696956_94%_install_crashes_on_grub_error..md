---
title: "94% install crashes on grub error."
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by Jay D. on 2008-02-14
Hi all, I'm very new to unbuntu and from what I seen, really like it. I am trying to install on a older system, with an raid 5 (3ware 9500s-4lp) and 4 segate st3750330as 750 gb drives. At about the 94% mark on the install the error comes up: "executing grub-install hd0 failed". 

I am not using any other partitions on the drive(s). I want to use the machine for a network storage device, and a bit of a desktop machine. Any advice would be great!

Thanks,
Jay

---

### Post by jan quark on 2008-02-14
try to install with the[ alternate cd ]("http://releases.ubuntu.com/gutsy/")
if you haven't already

[guide]("http://users.bigpond.net.au/hermanzone/p3.htm")

---

### Post by Jay D. on 2008-02-14
I'm downloading now. I'll update as soon as I get it going.

thanks,
Jay

---

### Post by Jay D. on 2008-02-15
It looks like the alternate cd install didn't work. Grub just doesn't want to go on. Looking into the 3ware site, I might have to install the 3ware drivers to make it bootable. But how in the heck do I do that? With Unbuntu?

---

### Post by MasterJS on 2008-02-15
Which of those four hard drives are you trying to install it to? That might be the problem.

---

### Post by Jay D. on 2008-02-15
I'm trying to install it as a raid 5 whole drive. using all 4 drives as one.... type deal.

---

### Post by MasterJS on 2008-02-15
Does the installer see the whole raid 5 or as individual hard drives?

---

### Post by Jay D. on 2008-02-15
it sees the whole raid 5. It gives me the size, 3tb in partitioning part of the install...

---

### Post by MasterJS on 2008-02-15
have you tried creating a separate /boot partition?

---

### Post by Jay D. on 2008-02-15
no I haven't. I figured I was doing a fresh install on a new drive(raid 5) and there are no other os's on there that I wouldn't need to.

---

### Post by spiderbatdad on 2008-02-15
mmm. That wont help. I have seen other issues with raid controllers in Ubuntu, usually where dual booting.

[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188) Everything I find, indictaes Ubuntu installed on a single disk, with the raid added after.

---

### Post by dstew on 2008-02-15
I have seen that error happen when trying to install grub onto an ext3 filesystem with certain hardware (don't remember which). The workaround was to create an **ext2** filesystem, and grub installed fine. Then, the filesystem can be converted to ext3 after installation.

---

### Post by Jay D. on 2008-02-15
I can try that. how do I install a ext2 system. 

Or should I just use a single ide drive for the os and mount the raid for storage?

---

### Post by PmDematagoda on 2008-02-15
This thread really belongs in the Installation and Upgrades section because it concerns the installation of Ubuntu.

---

### Post by Jay D. on 2008-02-18
> **Jay D. said:**
> I can try that. how do I install a ext2 system. 

Or should I just use a single ide drive for the os and mount the raid for storage?

Any help on this?

---

### Post by tps on 2008-04-10
I'm running into the same problem. I'll try the /boot partition after I try the ext2 route and report back if either one works.

Tim

---

### Post by tps on 2008-04-11
No dice on anything I tried. Straight EXT2 3TB partition, 200MB EXT2 or EXT3 /boot, reiserFS in any combination...  There has to be a way to do this...

---

### Post by tps on 2008-04-11
> **tps said:**
> No dice on anything I tried. Straight EXT2 3TB partition, 200MB EXT2 or EXT3 /boot, reiserFS in any combination...  There has to be a way to do this...

Heh. Replying to my reply... I created a 200GB / partition, installed to that, and all is well with the world. Grub is working fine. I'll mount the unpartitioned space where I need.

Tim

---

