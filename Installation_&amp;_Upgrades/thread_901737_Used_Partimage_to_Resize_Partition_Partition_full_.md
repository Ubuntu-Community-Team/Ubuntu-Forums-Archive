---
title: "Used Partimage to Resize Partition: Partition full with unknown data"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Justin312 on 2008-08-26
I wanted to resize my extended partition for Ubuntu (larger) and needed to reinstall windows anyway (I am keeping a dual boot). 

However, I've been using ubuntu for awhile now I didn't want to lose my installed programs, configuration, etc etc. 

Therefore I used Partimage to make an image. So I installed windows from scratch. Popped in the ubuntu installation disk when done and installed ubuntu selecting the new partitions that I wanted during the install. I then booted-up the live cd again and used partimage to restore my old (smaller partition) to my new (larger partition). 

Except, now I have the same freespace as I had before (a few hundred MB) in my new 20 GB partition that I had in my 10 GB partition. I don't know where this data is coming from. I highlighted all my folders in file manager (*except media) and it only totals up to about 10 GB. Except, when I go to Partimage (not from the livecd - but I'm not trying to change anything) it shows that I'm using over 20 GB. 

Please help!

Thanks,

    Justin
(Note: I've included screenshots to illustrate)

---

### Post by Justin312 on 2008-08-26
I stumbled on the answer to this problem. 

Something I didn't realize is that the size of the filesystem and the partition is not exactly the same thing. Thread [http://ubuntuforums.org/showthread.php?t=867335](http://ubuntuforums.org/showthread.php?t=867335) solved my problem. 

For anyone who had this happen resize2fs was the solution to my problem.

---

