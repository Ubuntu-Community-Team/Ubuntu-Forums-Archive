---
title: "Ideal Disk repartition"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by marsopia on 2005-03-14
Hi people!!

I am planning to re-install Ubuntu and wondering which would be the ideal way to partition the 20 GB space on disk I have for it. 

I actually have 
/ 1.9           Giga and only 500 mb used 
/home 5.8 Gig  78% used 22 % free
/usr      7.6 G     36 % used 64 % free
/usr/local 1.8 G   12% used  88% free
/var          1.7      50% used 50% free
/temp        1.4 G   12% used  88 free
/swap       0.9 G
/boot        141 Mb  55% used 45 % free     (I have Sid on hdb)

How would you repartition the disk?

Thanks

Mariano

---

### Post by BaffledMollusc on 2005-03-14
I'd be curious to hear the opinion of people on this one too. For a linux install I generally just go with a / (root) partition and a swap partition. I can't see the point in having lots of partitions on a home PC. Sure, if you have a server with huge amounts of I/O you might gain some performance by putting small, often accessed files on a physical disk with a really low latency or something. 

But in general, why would you want buckets of partitions? Doesn't this just reduce flexbility because you have to guess how much data in various categories you're going to have in future?

---

### Post by bored2k on 2005-03-14
[QUOTE=marsopia]Hi people!!

I am planning to re-install Ubuntu and wondering which would be the ideal way to partition the 20 GB space on disk I have for it. 

I actually have 
/ 1.9           Giga and only 500 mb used 
/home 5.8 Gig  78% used 22 % free
/usr      7.6 G     36 % used 64 % free
/usr/local 1.8 G   12% used  88% free
/var          1.7      50% used 50% free

/temp        1.4 G   12% used  88 free
/swap       0.9 G
/boot        141 Mb  55% used 45 % free     (I have Sid on hdb)
[/QUOTE]

First of all do you NOT download anything ? Where do you save all your Home user stuff ? What if you're downloading a 4.7gb *backup* disc ? You would have to basically erase stuff in $Home. Or what if you plan of making VCD's or DVD's? -You asked for opinions, thats mine as a person who does dvd authoring and downloads big files a lot.

With only 20gbs I would:
10gb /home [I deal with big files]
500mb Swap [because 20gb is too small for 1gb+ swaps]
6gb /usr
other stuff whatever

---

### Post by bored2k on 2005-03-14
[QUOTE=BaffledMollusc]I'd be curious to hear the opinion of people on this one too. For a linux install I generally just go with a / (root) partition and a swap partition. I can't see the point in having lots of partitions on a home PC. Sure, if you have a server with huge amounts of I/O you might gain some performance by putting small, often accessed files on a physical disk with a really low latency or something. 

But in general, why would you want buckets of partitions? Doesn't this just reduce flexbility because you have to guess how much data in various categories you're going to have in future?[/QUOTE]
 For a desktop computer I just make
/home
/
swap

Like you say, no server is running here or anything vital like that so I find my configuration perfect. Plus I get out of space a lot and having a /usr or a /var or /usr/local with that much spare space I can not deal with.

Since he likes dividing stuff I told him that but I would just create a 14gb /home, 5.3 / and 600mb swap.

---

### Post by marsopia on 2005-03-14
Thank you guys!! I recieved very good advice from you.
I read about that kind of partitioning on a Linux magazine, but I found that it was little flexible. I started finding myself with advices of "no space enough" when downloading big files, as iso ones for example, and the same happened when I tried to copy a dvd with my brand dvd burner.

I still think it is a good thing to have an independant /home partition. Do you agree with this?

Mariano

---

### Post by BaffledMollusc on 2005-03-14
[QUOTE=bored2k]For a desktop computer I just make
/home
/
swap

Like you say, no server is running here or anything vital like that so I find my configuration perfect. Plus I get out of space a lot and having a /usr or a /var or /usr/local with that much spare space I can not deal with.

Since he likes dividing stuff I told him that but I would just create a 14gb /home, 5.3 / and 600mb swap.[/QUOTE]

Fair enough, but could you explain to me what the advantage is in having / and /home on seperate partitions?

---

### Post by Xian on 2005-03-14
[QUOTE=BaffledMollusc]Fair enough, but could you explain to me what the advantage is in having / and /home on seperate partitions?[/QUOTE]
You can do a re-install or full CD upgrade and keep all your user prefs.

---

### Post by BaffledMollusc on 2005-03-15
[QUOTE=Xian]You can do a re-install or full CD upgrade and keep all your user prefs.[/QUOTE]

Good answer  :smile: Now I see the point!

---

