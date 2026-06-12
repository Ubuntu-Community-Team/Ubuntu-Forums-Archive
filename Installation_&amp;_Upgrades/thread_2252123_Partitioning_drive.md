---
title: "Partitioning drive"
date: 2014-11-09
forum: Installation &amp; Upgrades
---

### Post by enisakca on 2014-11-09
Hi Dear Ubuntu Users,

I want to install Ubuntu my laptop. I have an big question. I would like to install all of the my drive. There is 2 option in my mind. 

1) Erase disk and Install ubuntu with lvm (i did but if other option has more performance than this i may reformat my laptop)

2) A swap area 500 mb and Install Ubuntu in 20 gb size on my drive and ~900 GB Data area

I have a 1 TB harddrive. Disc read/write or 4K random read speeds is too important for me. I want to use ubuntu with max performance on my old laptop.

Which is max performanced option? Thanks for advices.

---

### Post by The Cog on 2014-11-09
I would suggest a third option:
* 20G used as /
* 20G not used 
* swap - 500M or perhaps more
* remainder used as /home

I do this, and always install my next version to the unused partition. Once I'm happy it works, I start using the separate /home partition, and all my files and settings reappear in the new version. So my "current" version alternates between the two 20G partitions.

If you used lvm, be careful that the /boot partition doesn't get full. I've seen updates get stuck where they can't complete because the disk is full, but can't revert because they haven't yet completed. Reinstalling is quicker than sorting out the mess unless it involves a long drive to get to the machine.

---

### Post by enisakca on 2014-11-09
[COLOR=#000000]I would like install ubuntu on my disk in fastest [/COLOR][COLOR=#000000]area [/COLOR][COLOR=#000000]read/write and 4K performance. So i must install first area swap and after 20 GB / 
[/COLOR][COLOR=#000000]using /home separete partition is useful? [/COLOR]Is it a negative performance impact? Beacuse caches and configs and system dirs in it.[COLOR=#000000]
[/COLOR][COLOR=#000000]I update my system everyday. When a new version is released, i install it. [/COLOR][COLOR=#000000]good idea 20 gb unused. but i think ubuntu is stable and i think this isn't [/COLOR]necessary[COLOR=#000000]. Am i wrong? 
 how much [/COLOR][COLOR=#000000]Swap [/COLOR]required for me? i have 4 gigs ram and i5 processor.
[COLOR=#000000]
i think this is good :)
[/COLOR][IMG]http://s1.postimg.org/5s91vqf73/Ekran_g_r_nt_s_2014_11_09_15_35_55.png[/IMG]

[COLOR=#000000]Can i reformat my laptop? I installed LVM on all of my disk. Is LVM useful for this? Or can i use install media and realign and reformat disk?


[/COLOR]

---

### Post by nerdtron on 2014-11-09
Swap - How much RAM do you have? Probably 500 MB is a bit small.
20 GB - system partition is good. I assume you won't use wine and install disk hungry applications?
900 GB - I suggest don't use as /home but rather make is a single partition and mount independently as /data. Just dump all your stuffs, pics, docs, music in there. Usually /home may store some config files of application which can conflict if you choose not to format it and reinstall another version of linux/ubuntu.

LVM - If you won't be adding another disk to your system or use the resizing capabilities of LVM, you might benefit slight increase in write speeds for removing the overhead of LVM

---

### Post by sp40140 on 2014-11-10
Hi The suggestions provided above are good. I would like to know if that 1TB drive is SSD or Platter? Do you have any specific use case for which you want such high performance from HD or just boot up time and gaming? 
I think the HD performance in very large part depends on hardware itself. There are changes in performance depending on the format (EXT, ZFP, NTFS).
But as long as you have enough room for os, you shouldn't have to worry about other partitions if your only concern is drive performance. 
Size of the swap partition depends on the hardware specs mostly ram.

---

### Post by enisakca on 2014-11-11
Thanks for suggestions. I have 1 TB platter harddrive. I want to use apps with 0 lag, 0 app launching time. bootup isn't important.
I don't use disk hungry apps. ubuntu apps is enough for me. I install lots of apps it takes only 9 GB. I don't think use wine.
I have 4 gigabytes RAM, i5 2410M proccessor, Nvidia GT 540M gpu.

---

### Post by sp40140 on 2014-11-11
In that case as I mentioned, the main concern is the specs of HDD.. 5400 rpm or 10k rpm? Based on your GPU I am taking a guess that it's a laptop and therefore, very likely that your HDD runs at 5400 rpm. And that is very slow. The configuration of partitions and OS is way down the list. If you still want the OS part of the chain fixed, I think you should look for an os with very low requirements for resources, and Ubuntu doesn't fit very well in that scenario.
If you put SSD in there, all your concerns will be addressed.
I have EliteBook and I got an SSD and put the platter drive in the slot for DVD (and got rid of dvd drive as it was useless for me). May be you should look into doing something like it. SSDs are cheap these days and performance diff is crazy big.

Cheers

---

### Post by nerdtron on 2014-11-11
Moving partitions on the start of the platter or end of the platter of the drive won't matter much. I think you won't even feel the difference. The main bottleneck of spinning hard drives are the platters themselves. 5400rpm found usually on laptop hdds are slowest, normal drives 7200rpm are on most desktop and Server drives SAS have about 10k to 15 rpm which have fast read/write times.
But in all these, the winner is always the Solid State Drives.

---

