---
title: "Grub 2.5 Error  18 - Suggestions"
date: 2010-11-02
forum: Installation &amp; Upgrades
---

### Post by lazypeterson on 2010-11-02
Alright, so I tried installing 9.04 on an older computer and was getting the Error 18 from Grub 2.5, likely because BIOS couldn't access the kernel. So I decided to remove Ubuntu and Grub completely and I'm now back at square one. However, I still very much want to dual-boot with Ubuntu. I was thinking I'd try again with 10.10 because it uses Grub 2 which I hear would probably take care of the problem... is this correct? Am I likely to have better results with Grub 2, or will I probably run into the same problem?

Also, do you have any suggestions of steps I should take before installation to insure I won't run into this problem again, and have to repeat this whole silly process again?

I'd appreciate any info you might be able to give me, I'm not really sure what to do at this point.

EDIT - I meant 1.5 at the beginning, sorry.

---

### Post by oldfred on 2010-11-02
If you are getting grub err 18 it is probably because your BIOS will not let your boot beyond 137GB.

You need to make sure all the boot files are inside the 137GB limit. The most frequent solution is a separate /boot partition at the beginning of the drive. Or if you can make windows small enough, your / (root) partition only needs to be 10-20GB, 2GB for swap and the rest use as /home (which then can be beyond the limit). In either case you need to manually partition in advance and use manual install to choose which partition is root, & /home or which is /boot & which is / and what formats to use.

[http://members.iinet.net.au/~herman546/p15.html#18]("http://members.iinet.net.au/%7Eherman546/p15.html#18")

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by lkraemer on 2010-11-02
lazypeterson,
I was having the same problem in the beginning of the year.  I finally
just wiped Windows, and installed Ubuntu 8.04.  Problem solved!
[http://ubuntuforums.org/showthread.php?t=1387843&highlight=error+18](http://ubuntuforums.org/showthread.php?t=1387843&highlight=error+18)

Error 18 is trying to boot from a cylinder past the 1024 limit.

Remember there is a MAXIMUM of 4 Primary Partitions on any Physical Hard
Drive.  You can use a Logical Partition, and have several partitions
under the Logical, if you need more than 4.

In my Case I had Win XP SP3, then /, Home, & Swap.

lk

---

### Post by lazypeterson on 2010-11-03
I appreciate the help guys. I really didn't want to wipe out Windows altogether so I ended up removing Ubuntu and Grub and installing 10.10. Grub 2 worked like a charm right after installation.

---

