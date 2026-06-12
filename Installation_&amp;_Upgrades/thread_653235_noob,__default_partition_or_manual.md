---
title: "noob,  default partition or manual?"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by mrchaos101 on 2007-12-29
I was just gonna go with the on line guide for the install, but reading some threads here they say this isn't the "secure thing to do".  Said something about I should have a partition for my files then rest ubuntu or something?

Any help or advise or an explain would be cool?  Keep in mind your talking to a windows user.

---

### Post by Craigus on 2007-12-29
Is the machine purely for ubuntu, or will it dual boot another operating system?

Is there any data on the HD(s) that you want to keep ?

---

### Post by mrchaos101 on 2007-12-29
100% ubuntu

Not data yet. it is a fresh clean box I built for this.

HOW EVER, Im gonna need to learn how to back up contacts and such from an xpbox to an thumb drive and get it in the ubuntu box later.

---

### Post by Craigus on 2007-12-29
Just go with the guided install. Make a separate /home partition. You can always resize partitions later if need be.

---

### Post by rfruth on 2007-12-29
all the defaults work fine :)

---

### Post by alekseyportland on 2007-12-29
Hi. Not a pro here, but this is what has worked best for me so far.

Manual configuration; you will need at least 5 GB for your root partition (recommend 10GB)
You will have to type the backslash "/" manually where it says "Mount Point" or something similar.

A separate Home folder (type "/home" where it says Mount point) will allow you to keep your files and settings if you need to start over and format the root ("/") partition; very handy. Make this partition as big as reasonably possible.

Now you need a swap partition of at least 1or 2 GB. Change the file system type from "Ext3" to '"swap"; you will see it on the right hand side. 

That is what I would consider the bare minimum. If you have a large drive, I would recommend leaving some space unpartitioned. You could also add a FAT32 Partition just in case you'll ever want to share files between Windoze and Linux. That should be enough to get you started

---

### Post by mrchaos101 on 2007-12-29
> **Craigus said:**
> Just go with the guided install. Make a separate /home partition. You can always resize partitions later if need be.

Ok sounds good.

I got ubuntu running. =) 

ALSO seen I needed video drive for my nvidia card.  Followed on line codes and got it working.

So far moving along an not too painful


And thank you Craigus.  You been helping a lot in my threads..

---

