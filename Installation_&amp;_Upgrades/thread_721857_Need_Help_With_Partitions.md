---
title: "Need Help With Partitions"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by WoodbineG on 2008-03-11
So im trying 2 install ubuntu again....and before on my last trys i think I created too many partitions for sum reason, last time I tried to install ubuntu I failed and my Hard Drive was of  180Gb and wen I was done I booted back to Xp and my HArd Drive was of 100gb I dont know what I did wrong but i need to "find" those 80 gbs back, my goal is to have Ubuntu on one side with 80Gbs and Xp with 100Gbs or vice versa doest matter, so I need your help people please help me ill be on so if u reply ill reply u back ASAP :(

---

### Post by uberlube on 2008-03-11
Id like to recommend that you download partedmagic. It is a liveCD and also an amazing tool for working with partitions and has lots of great tools for recovering files. The reason that you cant find the 80 gig partition is because you are looking for them from within Windows and NTFS cant read/detect EXT3 partitions. If you boot into PartedMagic and use its visparted program you will be able see your 80 gigs and make any changes that you would like. Just as a reminder, you will also need to make a SWAP partition that is roughly 2wice the size of your RAM. I personally use 3 partitions for linux.
1) SWAP
2) / (root partition, where the actual Linux OS is installed to, usually 15 or 20 gigs)
3) /home (This partition is for keeping my files and programs n junk)

You can assign what you want to mount on the partitions by choosing the 'manual' method instead of 'guided' during the Ubuntu install. 

Hope this helps :)

---

### Post by WoodbineG on 2008-03-11
Yea it helped but im stil a lil bit lost..........so I need to burn a bootable Cd of a partition thingy program? im so lost

---

### Post by uberlube on 2008-03-11
Yup grab the iso from the site listed below, then burn it.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Then pop it in and reboot, ill be here if you need any more help.

Also dont forget if you are planning to resize your NTFS partition you will need to defragment the HD, otherwise you run the risk of damaging your Windows (God forbid, lol).

From what you said before, I am assuming that you already did this and created the ext3 partition. What you should do is delete the ext3 and make a swap that is 2wice your ram. then make an ext3 partition that is about 10-15 gigs, then another ext3 with the rest of the space. Once these are made, reboot with the ubuntu install CD and choose guided for partitioning. Then mount "/" on the 10-15 gig and then "/home" on the second ext3 you made.

---

