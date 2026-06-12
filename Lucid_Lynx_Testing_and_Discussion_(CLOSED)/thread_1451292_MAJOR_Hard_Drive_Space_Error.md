---
title: "MAJOR Hard Drive Space Error"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Socialsymbol on 2010-04-10
[IMG]http://boonce.org/up/5077_Screenshot.jpg[/IMG]

[IMG]http://boonce.org/up/Screenshot2.jpg[/IMG]

This happened after I updated yesterday, however I restarted without any problems. As many of you probably know, libipod was updated yesterday, and upon testing it I found that I could finally sync my iPhone (3gs 3.1.3) successfully in Rythmbox.

As you can see in this picture, nautilus detects that I have a very limited amount of space left, yet gparted is reading the actual remaining storage. I let the iPhone sync overnight, and when I came back the next morning the computer was actually reading ZERO bytes free in my home folder. I restarted and the computer did a hard disk check, leaving me with roughly 150mb free space. Upon booting in I deleted an old .vdi which freed up a couple gigs.

This is the first major problem I've encountered on 10.04, and I really need to get this fixed. I have no idea how it happened.

---

### Post by Socialsymbol on 2010-04-10
I just tried syncing an album to the iPhone (last night it didn't sync everything) and midway though it gave me an unhandled transfer error. I don't know if this has anything to do with it or not.

---

### Post by ubunterooster on 2010-04-10
I had a Home folder at one point filled to the brim with files I was recovering. I had to use a Knoppix LiveCD to move the files to another drive or delete them.

---

### Post by Socialsymbol on 2010-04-10
> **ubunterooster said:**
> I had a Home folder at one point filled to the brim with files I was recovering. I had to use a Knoppix LiveCD to move the files to another drive or delete them.
where were the files located?

---

### Post by ubunterooster on 2010-04-10
They were hidden files in Home.

[I wish WinDirStat had a Open Source alternative; it would really help here]

---

### Post by warfacegod on 2010-04-10
That looks like you are running up against the System Reserve. Ubuntu automatically reserves 5% of any drive. That 22 or so GB discrepancy is almost exactly 5%.

```
sudo tune2fs -m x /dev/sd
```

Make x 1 or 2 for the percentage you would like. And in your case, you'll need to make it sd*a1*.

I also see you have an 11 GB swap. That is quite big. If you don't Suspend/Hibernate (I forget which uses swap) and you don't do any video encoding, you can likely never need it. I'd do away with swap entirely and resize your sda1 to fill up the space.

```
sudo apt-get autoremove
```

That can potentially free up some space as well.

If you do all three, I wouldn't be surprised if you get back 30+ GB.

---

### Post by Socialsymbol on 2010-04-10
> **warfacegod said:**
> That looks like you are running up against the System Reserve. Ubuntu automatically reserves 5% of any drive. That 22 or so GB discrepancy is almost exactly 5%.

```
sudo tune2fs -m x /dev/sd
```Make x 1 or 2 for the percentage you would like. And in your case, you'll need to make it sd*a1*.

I also see you have an 11 GB swap. That is quite big. If you don't Suspend/Hibernate (I forget which uses swap) and you don't do any video encoding, you can likely never need it. I'd do away with swap entirely and resize your sda1 to fill up the space.

```
sudo apt-get autoremove
```That can potentially free up some space as well.

If you do all three, I wouldn't be surprised if you get back 30+ GB.
Thanks, I'm not sure what it was that ended up working (I didn't check system space before doing any of this), but after rebooting, doing autoremove and changing the reserve space I have the proper amount of free space left.

Anyway, whatever it is that worked, thank you.

---

### Post by warfacegod on 2010-04-10
Glad to help. Most of what you got back would have been from tune2fs.

If you like your results then mark this thread as solved under Thread Tools. Cheers:P

---

### Post by cascade9 on 2010-04-10
I've got to ask- why do you have a 500GB HDD and no /home? o.O  

A nice 10-15GB / partition makes a lot of things easier- if you do get expanding .log etc,files then you get a warning well before they can eat too much space, and if there ever is a major file system error on / you still have all your data in /home, amongst other nice benefits.

---

### Post by warfacegod on 2010-04-10
An excellent point. If you do decide to go that route, I suggest using ext4 instead of 3. Also if you do, don't bother using tune2fs on your OS partition but definitely do it on your home partition.

---

