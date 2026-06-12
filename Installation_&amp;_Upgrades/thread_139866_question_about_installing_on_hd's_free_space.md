---
title: "question about installing on hd's free space"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by hyimted on 2006-03-05
hi all -

i'd like to install ubuntu (my first foray into linux) on my 160g hd.  it currently has windows xp on it.  but when i try to install ubuntu, it wants to take up *all* of my hd's free space (about 140g).  i really only want to put ubuntu onto a small chunk of space (maybe 30g) ... just so i can play around with it.

is there any way to do this?  i tried playing around with the partition part of the install (guided partition) ... but i couldn't figure it out.

thanks!

ted

---

### Post by m.musashi on 2006-03-05
When you get to the point of partitioning in the install, one of the install options says to resize and use free space. You can try that and see if you like the suggestion. Nothing is permanant yet and you can "go back". The other option is to manually resize. Pick a size you like and go from there. The wording is a bit confusing and I think you are choosing a size for windows and not Ubuntu so keep that in mind. I'm not 100% sure about that so read carefully and if something dosen't make sense start over.

Once you choose the write changes option you are commited.

Whatever you do, don't choose the erase entire hard disk or you will obviously lose windows. Of course, backup important stuff if you haven't already.

Enjoy. I've been using ubuntu for a couple months and loving it. Still use windows from time to time but not much.

---

### Post by hyimted on 2006-03-05
> When you get to the point of partitioning in the install, one of the install options says to resize and use free space. You can try that and see if you like the suggestion. Nothing is permanant yet and you can "go back". The other option is to manually resize. Pick a size you like and go from there.that's pretty much where i'm having the probs.  i guess i can try to pick my size, but i wasn't sure if that meant i had to pick a size for each partition (boot/swap/whatever).

i guess i'm just gonna try to partition the hd ahead of time ... then do a clean install ... not sure yet.

---

### Post by Nachtengel on 2006-03-05
It's not too hard to do the partitioning manually, as long as you have the free space to do it in.  You need two partitions to run Ubuntu, an ext3 partition mounted at / and a swap partition mounted at /swap (oddly enough).  The swap space should be at least twice as big as your amount of RAM (or so the old rule of thumb goes), probably would need a little bit more if you plan on using some swap-heavy applications like GIMP.  A few gigs should do you fine.  The rest you can devote to the ext3 partition mounted at /, make sure you make that partition bootable (the bootable flag is set).  If you can follow these pretty straight-forward directions, you should have Ubuntu up and running alongside Windows in no time.

---

### Post by m.musashi on 2006-03-06
If you do manual partition to create the free space, you can select the free space and do automatically partition to create the two you need for ubuntu (that probably made no sense). There are a lot of dual boot guides but [this one](http://users.bigpond.net.au/hermanzone/p3.htm) seems quite good and includes screen shots of the various steps.

Hope that helps and isn't too late.

---

### Post by hyimted on 2006-03-14
thanks all for the info .... the dual boot guide musashi posted really helped!  :)

---

