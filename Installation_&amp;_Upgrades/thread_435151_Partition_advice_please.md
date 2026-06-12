---
title: "Partition advice please"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by timofthec on 2007-05-06
guys,

I'm about ready to install ubuntu 7.04 after doing a little research here, but before I do, I wanted a bit of advice about how to manage the partitions because I do have some unused space on my hard drive that I can use.

I have a 160gb HDD which has two active ntfs partitions, the main one is of 60gb which has the main windows installation.  The second partition is of 40gb and is there for the kid's crap (sorry, I meant their important music files and vids).

That leaves me with around 55gb of unused space but I am unsure how to partition and allocate this.  My plan is to use 5gb as a fat32 partition so I can put files there that need to be accessed by both operating systems.  How much of the remaining 50gb should I set aside for the ubuntu swap file?  I have 512mb of ram by the way

Some of the examples of disk partition have the fat32  “shared data” partition as being very large but I’m not sure why this is.

I've seen some links to a project to allow the ubuntu OS to be able to both read and write to an ntfs partition, therefore, should I not bother with the fat32 partition?

ANY help, tips and advice would be most welcome.

---

### Post by mikewhatever on 2007-05-06
The fat32 partition size depends on one's personal needs, so it is up to you.
The swap size should be about twice the size of RAM. NTFS-3g enables Ubuntu to write to ntfs. It is in the repositories, ready for installation, but again, it's up to you.
I think that if you want the fat32 partition for storage only, you won't notice any difference with ntfs.

---

### Post by davezac on 2007-05-06
the swap space should be double your ram. so 1Gb for you.
make a back up before commencing!

i dont think fat32 can handle files >4Gb so if you plan to place large files in their you may need to re-think.

i have recently had a probelm installing fiesty. it worked initially on a blank hd freshly partitioned. but last week i had cause to re-install the os and when you do that you are required to reformat some of the partitions. so if you get stuck when you get to the partition manger come back to me.

from what i know - linux can only get read access to ntfs partitions(however commercially available drivers are available from [www.ntfs-linux.com](www.ntfs-linux.com)

i think if you are a novice, the best thing to do is mess about and learn the system before jumping into a complex wrangle with windows file shares!

---

