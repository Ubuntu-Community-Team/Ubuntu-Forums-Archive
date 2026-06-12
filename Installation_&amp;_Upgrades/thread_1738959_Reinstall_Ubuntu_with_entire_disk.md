---
title: "Reinstall Ubuntu with entire disk"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2011-04-25
I have a bad windows partition my Dell Mini 10v.  I have run gparted with errors about missing clusters and to run chkdsk /f.  Well, I can't since I can't boot into windows, I get the missing hal.dll error.

I can however, run Ubuntu 10.10 without problems.  I want to get the disk space that is all for the windows partition.

Can I reinstall ubuntu netbook and when it ask me to use the entire disk: can I?  Will I be able to over write the entire disk, or will I get an error that I can't access that partition, gparted gives me that error now?

Is there any way to resize the partition?  I ran ntfsfix without any change.

I've looked and can't seem to find an acceptable option here or other areas.  As far as I know I can't run chkdsk from ubuntu.

Dennis

---

### Post by ratcheer on 2011-04-25
Yes, if you reinstall Ubuntu, one of the first things it should ask about is reformatting the disk. Make sure you save anything you need to keep before doing it.

It would be more difficult, but it also should be possible to delete unwanted partitions and resize your Ubuntu partition(s) at the partitioning phase of installation.

Tim

---

### Post by Pyrophorus on 2011-04-25
> **ratcheer said:**
> 
It would be more difficult, but it also should be possible to delete unwanted partitions and resize your Ubuntu partition(s) at the partitioning phase of installation.

Tim

I would like to do this, without reinstalling Ubuntu all together.

---

### Post by claven123 on 2011-04-25
I can't do anything to that partition until the missing cluster thing is fixed.  Gparted has an error and it won't allow me until it's fixed.  That is why I'm concerned about the reinstall of ubuntu.

D

---

### Post by claven123 on 2011-04-25
I just remembered it should ask me to reformat, that will fix the missing clusters?  Right?

D

---

### Post by ratcheer on 2011-04-26
> **claven123 said:**
> I just remembered it should ask me to reformat, that will fix the missing clusters?  Right?

D

It should, unless the disk is so damaged that format cannot deal with the problem. In which case, you will find out and can go about replacing the drive. But, I imagine format will remap any damaged sectors and fix things up.

Tim

---

### Post by claven123 on 2011-04-26
Thanks,  I think that is my only option.  I've been doing some searching about getting a bootable USB drive with XP and attempting to fix the windows partition, but it's seems a bit elusive.

I'll reinstall ubuntu and then if all else fails I can always replace the drive.  Heck, it was a free computer anyway. 

Thanks,

D

---

