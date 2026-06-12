---
title: "Filesystem Unable to be Created"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by windexh8er on 2004-10-21
Well... Coming from a world of Gentoo &amp; FreeBSD I figured I'd throw Ubuntu on a system laying around.  Most of all I wanted to see the new Debian Sarge installer in all it's glory.  Too bad it's seemingly b0rked on my hardware.

I did a quick search but didn't see anything jump out.  What my problem is the system I'm installing on has 2 hard drives on IDE primary / slave channels.  The system also has 2 SATA controllers...  Regardless, those are empty.  Ubuntu install goes fine up until partitioning (of which I am seasoned in doing).  When I try to create my reiserfs partitions it says the filesystem cannot be created.  I switched over to the second TTY and grepped through /var/log/messages and it was bitching about files not existing or the like.  It's late and I forgot to write them down.  Anyway.  So I decided to start over and figured I'd just run the "recommended" ext3.  No luck, the file structure seemingly writes out to the disk (activity on the disk) but at the end it fails, this time with a tune2fs type error I believe...

Anyway.  I give up for the night.  Anyone else have problems with the official release?

TIA!

Regards...

---

### Post by EagerBeaver on 2004-10-21
I believe i have the same problem as you.

[http://www.ubuntuforums.org/viewtopic.php?t=1508](http://www.ubuntuforums.org/viewtopic.php?t=1508)

---

### Post by windexh8er on 2004-10-21
Hmmm.  Anybody else?

I have an MSI board with the VIA KT600 chipset...  How about you Eager?  I'm guessing this is a bug that a number of people will be running into.

---

### Post by EagerBeaver on 2004-10-21
[quote=windexh8er]I have an MSI board with the VIA KT600 chipset...  How about you Eager?[/quote]

I have Shuttle board with a VIA KM266, and a VIA 8235.

---

### Post by windexh8er on 2004-10-21
Any SATA controllers?

Doesn't look like anybody really has an answer for us as of yet.  I'd really like to give Ubuntu a shot, but if I can't install it on a pretty mainstream hardware setup it probably won't fit in well...  :(

---

### Post by windexh8er on 2004-10-25
Nobody else has seen this issue?

---

### Post by lazydog on 2004-12-09
Same Problem here.

I have an Epox 8RDA3+ mainboard with a SiImage 3112 SATA Raid Controller and one 160gb HDD from Seagate.

Already installed is Win2k and Gentoo Linux, but when I try to format a partiton with the Ubuntu/Warty installer the filesystem creation fails. 

I created an ext3 filesystem on the free partiton with Gentoo, which was successful, but still the Ubuntu installer is unable to use this partition as mount point /

---

### Post by MSR on 2005-03-02
I have the exact same problem, I registered here just so I could post for help. I'm guessing since there haven't been updates to this thread, that no one has yet found a fix?

Thanks.

Michael

---

