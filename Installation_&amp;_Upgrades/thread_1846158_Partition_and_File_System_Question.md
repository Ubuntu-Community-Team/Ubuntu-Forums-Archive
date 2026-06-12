---
title: "Partition and File System Question"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by Nuvielle on 2011-09-18
Hi =)

I have bought an not realy very new but very cheap PC and i want to use Ubuntu on it. This should be a linux only PC, a normal Desktop

IT has built in

AMD Phenom 2 x3 445
4 GB DDR2 RAM
ATI Radeon HD4650
1 SATA2 HDD 160 GB / No SSD
1 SATA2 HDD 500 GB / No SSD

So i asking myself how should the Partitions be and what Filesystem would be the best. Its like in the Candy shop, many sweet things and you don't know what you should take ._. You are reading very often what filesystem XY does well and what not, but no site tells you realy understandable  Filesystem X is very goot for /, Filesystem Y is good for /home and Filesystem Z is good for Media usw. To say it at first, i don't want to use EXT4, i simply don't like it, i can't argument that ^^ I don't like young filesystems, BTRFS is the same.

The 4 possible Filesystems i want to use are EXT3,XFS,JFS or ReiserFS.

I planned to partitinate the disks like like

160 GB HDD / 1 GB Boot (ext3 ?)
            30 GB Root (JFS (heard that JFS is very good for / ?)
          REST    Home (XFS?)

500 GB HDD / 4 GB SWAP
          REST    /data (XFS/REISER?)

I am no native english Speaker so forgive me the mistakes i made in my initial Post =)
Thanks for every Tipp and Suggestion ! :p

---

### Post by MAFoElffen on 2011-09-18
I'm curious...

I do multi-boot <> so I have multiple file systems "because" I use multiple operating systems and use Linux as the go-between between them.

BUT- If you only have "one" OS planned (Linux), why would anyone want to use multiple file systems?  Physical data security is one thing by adding protective walls around data into segments and partitions, but by file systems?

EXT4 seems fine for me in desktop and server implementations... But ZFS has a lot of advantages also.  Linux implementation of ZFS are still a little extra work though.

---

