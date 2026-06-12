---
title: "All 4 primary partitions - modify?"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2011-11-10
A friend has just bought an HP Pavilion G7 laptop (win7) and  guess what, it has 4 primary partitions. He wants me to install Ubuntu dual boot.

A bit of searching  and I found this
(see Method 2) How to Create Extended Partition / Logical Drives Where Needed.
[http://www.sevenforums.com/tutorials/146694-partition-extended-logical-drives.html](http://www.sevenforums.com/tutorials/146694-partition-extended-logical-drives.html)

It makes use of a bootable CD apparently based on tinycore, and is intended for Windows users. 
partition wizard
[http://www.partitionwizard.com/download.html](http://www.partitionwizard.com/download.html)

It looks like it includes the job of converting a primary partition to logical.

Has anyone used it?
Any comments anyway please?

tia

---

### Post by darkod on 2011-11-10
There have been lots of questions here for HP because they started shipping with all 4 primary partitions used.
The least painful solution, and the best in my opinion, seems to be: The HP Recovery Software (or what ever it is called exactly) offers you to create a set of bootable DVDs for recovery to factory state (as it came). In this case you can safely delete the recovery partition. This has been even advised by HP support in lots of cases.

After deleting the partition there is no problem to create extended in its place. If you feel like it, you could install not the standard root + swap for your friend, but instead root + home + swap. Allowing him to do clean installs in future when ever he feels like it, and keeping his /home partition separate.

PS. I forgot to point out something. Deleting the partition will allow you to create a new extended one however if you need more space than the current recovery partition uses you will still have to shrink one of the win7 partitions with the Disk Manager tool.

---

### Post by candtalan on 2011-11-10
Thanks for your comments, appreciated.

For the record (after creating a complete disc image using clonezilla live cd) I did proceed with the approach in the links in my first post, using a live CD of partition wizard, following the procedure in the sevenforums link, and it worked ok. I now have a 300GB unpartitioned space  on the drive, with all partitions still in place. The win7 partition was resized by win7 down from 650GB whatever.

I now hope to  use ubuntu 10.04.3  to install into 'largest available space' hope the option still exists, will look.

---

