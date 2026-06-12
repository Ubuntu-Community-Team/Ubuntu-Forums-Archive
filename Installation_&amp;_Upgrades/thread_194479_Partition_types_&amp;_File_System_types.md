---
title: "Partition types &amp; File System types"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2006-06-11
For partitioning during install of Dapper Drake should the partitions be on this order:

                                              /root
                                              create as:  Primary
                                              file system:  ext2

                                              /home
                                              create as:  Primary
                                              file system: ext2

                                              /swap
                                              create as:  Primary
                                              file system: Linux/swap or should this be ext2 also ?

What is the extended and logical in the **create as** drop down to be used for ?

Why is the NTFS listing in the **file system** drop down for ?  Am I correct that this is NOT for use with the Ubuntu installation partition(s) ?

Shoud I consider using a file system type other than ext2 and why ?

Thanks for your replies.

---

### Post by woot on 2006-06-11
the extended / logical stuff is for when you use more than x primary partitions (and x is 4 I believe)

then you can have to following:
primary --> extended (logic --> logic --> logic --> logic --> ...)
its some kind of solution to have more than 4 paratitions

(not sure if my explanation is correct but i think so)

Your partitioning seems fine, and the swap should be linux/swap indeed

---

