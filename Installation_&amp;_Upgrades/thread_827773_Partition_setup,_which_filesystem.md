---
title: "Partition setup, which filesystem"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by Aslund on 2008-06-13
Hey outthere

I know there is many subject regarding this and I have spend hours trying to find a clear solution, but without hope. 
Due to holidays now, I have a plan to try out another filesystem then ext3, my plan so far is: 

/boot  ext2
/      reiserFS
/home  JFS
swap

or 

/boot  ext2
/      JFS
/var   reiserFS
/home  JFS
swap

But I can't really decide between those two solutions. Hope someone can post a comment and advice. 3th solution is also welcomed. 

ps. if I do a /var with reiserFS, what size would be best?


Regards

Aslund

---

### Post by housam on 2008-06-13
For installing Ubuntu , you only need to create partitions with ext3 format and a swap partition. Read [[COLOR="Red"]_this document_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition#head-a7b3b3837fbac5af4f996e6b68de9168781d78a1") about it

---

### Post by Aslund on 2008-06-13
I know that and thats how I run Ubuntu currently, but as I wrote, I would liek to try out somethung different while I ahve time and not worried about data security when I am at university.

---

### Post by Habbit on 2008-06-13
> **Aslund said:**
> I would like to try out something different while I have time and not worry about data security when I am at university.

What do you mean with "data security"? If you mean resilience against system crashes, then ext3 is your FS - its only major risk factor is the lack of journal checksumming [(wiki article)]("http://en.wikipedia.org/wiki/Ext3#No_checksumming_in_journal"). ReiserFS is also fine with crashes as long as the HD does not start suffering physical corruption - it goes down in flames from that point on. Others, I don't know, and JFS is an unknown for me, but I remember that XFS used to suffer from garbage-tailing opened files after a crash-and-reboot.

If, on the other hand, you mean data security as in passwords and all that, then you need on-disk encryption with **cryptoloop**, and what FS you use does not matter (to that effect) since the whole block device is encrypted. Remember not to encrypt your boot partition!

---

### Post by Aslund on 2008-06-13
I mean corruption and such, since I have holiday now I can take a risk for trying out something new and see how it works. 
But instead of all this walkarounds, is'nt there somebody who can answer my question? :S

Regards

Aslund

---

### Post by Habbit on 2008-06-13
> **Aslund said:**
> But instead of all this walkarounds, is'nt there somebody who can answer my question? :S
Well, if you want someone to tell you "use THIS filesystem and no other!" so that your life can be easy and happy, no sugar (well, there are such people, but they are usually flamers, bigots or the FS developers - categories are nonexclusive).

This is about choice, and Linux is in particular the filesystem bitch of all OSes: I use XFS for the recordings partition on my Mythbuntu media center because it can handle very big files with little latency to the client app. However, on my main box I have a small ext3 root and a big ReiserFS /home suitable for the very small config files usually stored in user dirs, while in a Gentoo box with a more flaky HD that is mainly used to run BOINC I prefer ext3 for all its partitions. Finally, my laptop is all-ReiserFS. What I mean is that the FS best fit for you depends on what are you planning to put in it, how are you planning to store and retrieve it, etc. Why do you claim to seek experimenting with different filesystems if you don't want to take the first step in the scientific method and choose what FS to experiment with?

But of course, if you want an easy answer, just use ext3 :popcorn: The SUV of the filesystems!. On the other hand, ReiserFS is fascinating because it can go from lightning fast to crawling slow and back in little time depending on the workload you put upon it.

---

### Post by timcredible on 2008-06-13
i've used just about everything over the last decade, and seems to me that reiserfs used to be the fastest, but i think development stopped when reiser got arrested.  if you're just experimenting, try any/all of them, have fun.  the only problem you may run into is if you're using a sata drive or large drive, some of the older filesystems may not support it.

---

### Post by Habbit on 2008-06-13
> **timcredible said:**
> reiserfs used to be the fastest, but i think development stopped when reiser got arrested.

Reiser3 (i.e. ReiserFS) development had already been halted and development moved to Reiser4 long before Hans Reiser was arrested. I don't know whether they're even taking the time to add bugfixes into Reiser3, which, together with Reiser's natural diplomacy and some problems with the new version, convinced the Linux kernel developers not to include Reiser4 in the "official" distribution: [wiki article]("http://en.wikipedia.org/wiki/Reiser4#Integration_with_Linux"). Flames are still running since them.

---

