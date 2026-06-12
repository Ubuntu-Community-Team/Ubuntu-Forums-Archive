---
title: "help with installing Ubuntu on hp dv2000"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by icecube76 on 2007-03-24
i want to install ubuntu on my new hp dv2000
i have 3 partetions 
c: , d: and HP Recovery partetion

i want to install ubuntu without deleting the recovery partetion or c: partetion
i also want to keep the MBR or back it up.

regards

---

### Post by eapache on 2007-03-24
You can't back up your MBR, however, if you have the windows xp install disk, that will restore it no problem. Because you want to keep c: and recovery, I assume that you therefore wish to install Ubuntu on d: Keep in mind that any info on d: will be erased when you install. Your other option is to shrink one of your partitions, so that it can't hold as much, but is still available (and doesn't get erased). I don't know the size of your partitions, so I can't really make a firm suggestion at the moment.

---

### Post by GordSellar on 2007-03-24
Yes, you should just make the recovery CD -- it's able to reinstall the drive completely if you want to -- and then clear out that space. You can use the partitioner in the Ubuntu install sequence to resize the big drive, keep the quickplay partition if you like, make s big fat partition for shared data, and then use a third partition split into two logical partitions -- your ubuntu partition, and your linux swap partition. That's how my PC is set up, anyway...

---

