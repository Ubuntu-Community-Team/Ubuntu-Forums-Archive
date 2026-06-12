---
title: "windows 7 ntfs partition appeared unallocated"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by MuffinMan123 on 2010-04-07
following from my last thread,
[http://ubuntuforums.org/showthread.php?t=1446662](http://ubuntuforums.org/showthread.php?t=1446662)

I used testdisk as the replies suggested recovered all my linux partition including my 2 linux distros and boot partitions, but now my windows 7 appeared as unallocated space, which is very ironic, I fixed my last problem only to have situation reversed. I recovered the mbr record from my boot partition, but because that record dose not include the ntfs partition, that partition appears as unallocated space.

so how can I make that ntfs partition recognized again so I can update grub and boot to my windows 7 partition? Please help me out, I have had this partition stuck in my computer for a while doing nothing...

---

### Post by MuffinMan123 on 2010-04-12
bump

---

### Post by Herman on 2010-04-12
Probably you just need to run Test Disk once again but this time be sure to include the Windows 7 partition in the new partition table. Maybe you forgot to select it or something.
It can take a little practice to learns how to use TestDisk and since it's not a program we need to use very often, (thankfully), it probably takes most people  more than one attempt to get the results they want.

---

