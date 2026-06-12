---
title: "If making a raid0 partition from large IDE and SCSI, will rest of IDE risk more wear?"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-10-17
I want to try a raid0 array made of 2 25 GiG partitions only, not whole drives. I have a recent 500 GIG Seagate (5 yr warranty) and 100ATA IDE drive and a 2001 dated 10k Ultra160 IBM (Ultrastar) 36 GIG SCSI.

 I read that any raid array causes increased heat to the drives and attached cables etc..., and the SCSI model tends to be hotter than some other drives of that era.  I need to boost speed for video editing and will create a total of 50 GIGS and mount my /temp folder there (I will be keeping the edit projects very simple).  

 Hoping that if a drive fails it's the SCSI first, will I have a problem accessing the non raid part of my IDE drive, considering that my 'targeted for raid' partition is within an extended partition? 
Is the ratio of increase in drive wear great compared to gains in I/O and speed increase for this type of work?  I found so far yeses and nos, I can't decide.

Hoping to finally re-install hardy studio LTS soon, thnks in adv!

Note: I have an HP workstation of same age as SCSI, with many fans so this means that I have adequate cooling environment, right?

:guitar:

---

### Post by craigcrawford114 on 2008-10-17
I am running a RAID 5 array and I can tell you that any warnings about extra heat are totally misinformation.

The extra heat comes from the extra HDDs you are running in order to make that RAID array. The individual HDDs do not increase in temp themselves, only the overall system temp due to more HDDs.

With a RAID array, there is no "increased" wear on an individual drive. But because you are spreading the data across more drives, the chances of losing data increases (this being due to each drive has a chance of failing...).

My guess is that you're using the Intel Matrix RAID to create that 2 x 25GB RAID array. If so, if one drive was to fail then you'd lose the RAID array and the data stored on the non-RAIDed disk.

I hope this was the info you were looking for - if not, tell me :)

---

### Post by Zack McCool on 2008-10-17
> **craigcrawford114 said:**
> 
With a RAID array, there is no "increased" wear on an individual drive. But because you are spreading the data across more drives, the chances of losing data increases (this being due to each drive has a chance of failing...).


This is true of a RAID0, but in a RAID5 (or a RAID1) you chances of losing data decreases, considering the fault tolerance of the array.

I am pretty sure you know that already, but in the interest of making the information clear to newbs...   ;)

---

### Post by cariboo on 2008-10-17
Just as a point of interest I just checked the hard drive temps on my server, I'm running a raid 1 array:

```
sudo hddtemp /dev/sdb
/dev/sdb: ST3400620AS: 22°C
jimk@Willy:~$ sudo hddtemp /dev/sdc
/dev/sdc: ST3400620AS: 22°C
``` 

So it looks like heat is not a problem with raid arrays.

Uptime is currently 141 days. I believe power cycling the drives does more harm then anything else.

Jim

---

### Post by craigcrawford114 on 2008-10-17
> **Zack McCool said:**
> This is true of a RAID0, but in a RAID5 (or a RAID1) you chances of losing data decreases, considering the fault tolerance of the array.

I am pretty sure you know that already, but in the interest of making the information clear to newbs...   ;)

Yeah, I forgot to mention it only applies to RAID 0 ;)

---

### Post by streamsanddragonflies on 2008-10-20
Thanks for the replies!  Since I have a decent HP x4000 workstation with good cooling fans overall, I will not worry about the heat issue anymore.

 I should have specified that the RAID I wanted to try was the software raid that comes included with Hardy's alternate install DVD; I read a bit on how to select your partitions and "use as raid 0" in the expert partitioner, but I don't know much more than that about it!

---

