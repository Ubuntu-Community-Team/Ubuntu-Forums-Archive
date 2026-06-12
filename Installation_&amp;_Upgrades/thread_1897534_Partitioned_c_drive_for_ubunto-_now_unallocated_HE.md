---
title: "Partitioned c drive for ubunto- now unallocated?? HELP"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by echapp on 2011-12-19
Hi, I am trying to install ubuntu side by side with windows. 
 
I have 4 primary partitiones with my hp laptop. 
 
ubunto only sees 4 primary partitiones so i tried to delete sda 3 and 4, trying to make them extended and _divide c drive into 2 primary partitions._ (1 partition for my windows of 200GB, and 1 partition for ubunto of 400GB)
 
_This is what I started with:_
 
sda/1 - boot(windows)-2GB
sda/2 - cdrive (600GB)
sda3 - recovery (windows)-25GB
sda/4 - hp_Tools- 100mb
 
--------------------------------
I went into terminal -- fdisk to divide my 600gb drive into 2 partitions.
 
_terminal_
fdisk
partitioned my c drive, and made the 600GB drive a 200GB for windows to save all my data and pictures. now I have _400GB unallocated_ under computer management-storage. 
 
I inserted ubuntu and when it came to partitioning screen, it would not allow me to use the 400GB free space, it says its unusable. 
 
How do i make this usable. 
 
I went into terminal-fdisk and deleted recovery partition and hp_tools partition, and created a primary partition with the 400GB free space. I am trying to make and extended partition for recovery, and this worked. when i went to make an extended partition for hp_tools, it says values out of range. 
 
I am a beginner, so if anyone has any idea of this problem please help...

---

### Post by Mark Phelps on 2011-12-19
If you forced the split of the "C" drive while you still had 4 primary partitions, then you could have caused major filesystem corruption as a result.

Not really sure what you have now, so please open a terminal and enter "sudo fdisk -lu" (lowercase L, not a one) and post the results back here.

---

