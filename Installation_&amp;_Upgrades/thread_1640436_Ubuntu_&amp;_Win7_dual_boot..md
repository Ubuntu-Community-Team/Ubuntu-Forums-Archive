---
title: "Ubuntu &amp; Win7 dual boot."
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by h34e0f on 2010-12-07
After overwriting my system with Ubuntu it has become clear I have made a mistake and need a Windows partition as I use a lot of CAD software.

Therefore I am planning to blank my HDD and start from scratch to make things as clean as possible.

I have a few questions.


[LIST=1]
[*]Can I install Ubuntu 10.10 32bit alongside Win7 64bit?
[*]My HDD is 320GB (Showing 307 usable in Ubuntu) How large a partition is sensible for Win7? I was recommended around 100GB - is this suitable?
[*]Am I able to share files across the partition to be accessible (and editable) via both OS? (Not a necessity but would be useful!)
[/LIST]

---

### Post by wilee-nilee on 2010-12-07
You may not need to wipe the drive post a screen shot of gparted from Ubuntu. You may need to install gparted, it resides in menu-system-admin-gparted once installed to install from a terminal run.
```
sudo apt-get install gparted
```

1. Not sure about this but probably not if you want to share stuff.

2. Lets get to the size when needed.

3. A shared NTFS partition is often used both W7 and Ubuntu will read and write to it.

---

### Post by h34e0f on 2010-12-07
I only installed Ubuntu afresh 2 days ago so it's no hassle really as I haven't set anything up yet, and I read that it's best to start afresh or with windows installed prior to Ubuntu?

---

### Post by wilee-nilee on 2010-12-07
Yeah if you want to do all fresh installs it will be faster, and should have no snags.

So as far as the size of W7 I would do a 40 or so gig what ever will have the main OS never exceeding a 70% use. Then another ntfs for the data=docs, movies, media...etc to go to. This second could be the shared but you only want to change anything in it from the windows side basically, windows is a bit finicky about this. If you build the NTFS from gparted put the boot flag on it before installing to it.

W7 if you just let it install makes 2 partitions the first a 200Mib boot that is also part of the Ultimate version which allows encryption. If you don't need that make the first install for the main W7 OS a NTFS with gparted and install to it, this will have the whole W7 in one partition, with the boot in it.

Also I notice that with the Ubuntu install the extended is only around the swap it is better around the Whole Ubuntu set up. A extended partition allows as many other partitioned you can fit in it including a shared NTFS with W7. A regular HD will only allow 4 primary partition which a windows set up has to be to work basically.

You may be aware of all this already just trying to have pertinent info here.

---

