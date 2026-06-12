---
title: "Couple of quick questions about installing"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by Captiivus on 2006-09-26
My computer is a bit old, but from what I see, the 633mhz/192 ram will do fine, and since it runs XP, I can't see why it wouldn't.  Here are the questions:

I only have about 9 gigs free on my internal hard drive (has xp on it).  I also have an external that has about 25 gigs I can use freely. (used for storing music/vids)

Which should I install it on?  I have no problem taking apart my external and putting it in the computer, and I would even be willing to swap out the two hard drives when I needed to use Windows (since it would be on the other HDD, and theres only one hdd slot in the computer)

And if I do put it on my external, would the partitioning tool be able to leave all of my music/video intact?

Oh, and one final bonus question: Could I access my music/vids from Ubuntu?

I can't thank you guys enough for your help, one of the things that made me want to use Ubuntu was the way users talked about the community and how helpful it is.  Thanks in advance.

---

### Post by em3raldxiii on 2006-09-26
AHA!  Something I can help with!  A little anyway:

1.  your specs are okay, but you would do well to upgrade to 256MB RAM (even for WinXP) - you will have a noticeable boost to performace in BOTH operating systems.  If you are near Edmonton Alberta Canada, I've got some spare PC100 and PC133 RAM laying about that I could give to you,

2.  9 gigs, hey?  Hmm ... well, you don't want to strip XP down to nothing (as in, you need at least 1GB of empty space on your drive for XP to even function passably well), leaving you with 8GB MAX for Ubuntu (minus the obligatory swap of a minimum 384MB).  This would be okay if you don't plan on installing any very large applications.

3.  I personally would put the external into your computer, especially if it's a faster drive, and installing Ubuntu on there.

4.  Swapping drives in and out would not work (well, you could probably arrange something, but it would be a freaking huge pain in the ***, so don't do that LOL).  You are better off putting the drives in your computer and leaving them there.  This is because Ubuntu will install a boot-loader that will "see" your XP and Ubuntu installations (it's called GRUB), so that you can boot either OS at will.  If you pull the primary-master drive (the one you have XP on), then ... ugh ... messes with my head.  Definitely not optimal. ;)

5.  Yes, the partitioning tool that comes with Ubuntu will be able to partition your drive safely.  Even if it is currently NTFS.

6.  Yes, Ubuntu CAN be made to read/write to your music/video partition.  If it is NTFS, this is a "special" situation because there is limited "official" support for NTFS partitions in Linux.  However, there is a beautiful thread on here somewhere for this.  I'll find it for you when I am not so tired.

Mmm ... well, I could go on and on, I have a tendency to be verbose.  Someone else probably already posted while I was typing this.  Anyhoo ... if you have troubles of any sort, please don't be afraid to ask!  Meh ... many of your questions may have been asked before, and you could probably search to find the answers, but hell ... I'll answer them for ya anyway ;)  Itsallgood :D

---

### Post by Jussi Kukkonen on 2006-09-26
> My computer is a bit old, but from what I see, the 633mhz/192 ram will do fine, and since it runs XP, I can't see why it wouldn't.
It could have more memory (but if you're running XP on it, you know this already :)), but it'll be fine.

> I only have about 9 gigs free on my internal hard drive (has xp on it). I also have an external that has about 25 gigs I can use freely. (used for storing music/vids)

9 should be more than enough (if you keep using the external drive for large files). If you don't need much more for XP on the internal disk, go ahead and install on the same disk. For reference, my laptop and server machines both use about 4GB on their 'system disks' (I too use another disk for videos, music and other large files).

> And if I do put it on my external, would the partitioning tool be able to leave all of my music/video intact?
Oh, and one final bonus question: Could I access my music/vids from Ubuntu?


The answer to these depends partly on the filesystem. If you are using FAT, you should have no problems. If it's NTFS you might have problems, e.g. write access from linux is problematic at best and repartitioning might not succeed (I'm not very familiar with the new installer, so I could be wrong on the partitioning ). In any case, remember to run defrag on any disk yopu intend to repartition, otherwise the size of the partition can't be reduced without data loss.

EDIT: I see em3raldxiii already unknowingly corrected me on the repartitioning NTFS -issue. I disagree with him about the status of NTFS write support though -- personally I would not trust it.

---

