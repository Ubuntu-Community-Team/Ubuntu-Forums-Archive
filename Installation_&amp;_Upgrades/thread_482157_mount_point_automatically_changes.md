---
title: "mount point automatically changes"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by umairsaeed219 on 2007-06-23
problem is that when i install 7.04 everything goes smoothly except when partition editor comes
here i tell you in detail
i have 4 partitions on my 80gb hd before installing ubuntu (on windows ntfs)
important point is all 4 of them were primary partitions
so i choose one of the to install the 7.04
this partition which i have selected was not one on which windows was installed it was totally empty no data was on it
so i delete this partition and use free space to create ext3 partition having mount point /
After that the unused space which i have kept for swap was declared unusable by partition editor ?????????(i think this is because there cant be more than 4 primary partition at a time and here i am going to have 5 3 of them ntfs and one ext3 so swap was not allowed to make)
then i decided to keep on going with out swap which goes well and installation complete
after installation i decided to reboot the system as per installer instruction. after that nothing happens screen remain blank and only hd led was blinking
i tried again to install 7.04 then i came to know that mount point which i have kept / was automatically changed to /media/etc (i cant remember exactly )
this happens several  time each time i select / as mount point but ubuntu does not start so i install again and here partition editor tells me that  mount point is not /

---

### Post by confused57 on 2007-06-23
> **umairsaeed219 said:**
> problem is that when i install 7.04 everything goes smoothly except when partition editor comes
here i tell you in detail
i have 4 partitions on my 80gb hd before installing ubuntu (on windows ntfs)
important point is all 4 of them were primary partitions
so i choose one of the to install the 7.04
this partition which i have selected was not one on which windows was installed it was totally empty no data was on it
so i delete this partition and use free space to create ext3 partition having mount point /
After that the unused space which i have kept for swap was declared unusable by partition editor ?????????(i think this is because there cant be more than 4 primary partition at a time and here i am going to have 5 3 of them ntfs and one ext3 so swap was not allowed to make)
then i decided to keep on going with out swap which goes well and installation complete
after installation i decided to reboot the system as per installer instruction. after that nothing happens screen remain blank and only hd led was blinking
i tried again to install 7.04 then i came to know that mount point which i have kept / was automatically changed to /media/etc (i cant remember exactly )
this happens several  time each time i select / as mount point but ubuntu does not start so i install again and here partition editor tells me that  mount point is not /

There is a limit of 4 primary partitions to a hard drive, however one primary can be an "extended" partition, which can contain many logical partitions(for example, your root and swap partitions need to be logical partitions within an extended partition).
I don't know of any way to change a primary partition to a logical partition, unless someone else knows, you should probably reinstall Ubuntu.
See this guide:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Read the guide, but basically you would reinstall Ubuntu on the same partition that it is currently on, you may need to resize it to all but how much you want for swap(or you may not need to resize, if you already have unallocated space for swap)...for your root partition, set the mountpoint as / , format as ext3, select logical partition(or extended, if the partitioner won't allow you to select logical)...then setup the remaining space for swap, mountpoint swap, format swap, set as logical partition.
Just make sure not to select format for your Window's partitions.

---

