---
title: "moving partition problem!!"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by moufa on 2007-06-01
Hello,

i recently installed ubuntu at my samsung R40 plus laptop and i am very happy about that!

my hdd had already 2 primary partitions, 1 with vista and 1 with data(NTFS). therefore i installed ubuntu at the end of the second partition creating 1 extended that contains 2 logical, 1 for ext3 and 1 for linux swap.

However i set ext3 at 7GB and now i have only about 100MB left! I dont want to reinstall it cause i spent a lot of effort perfect configuring it so i thought about moving and resizing the partitions with gparted (decreasing the data ntfs partition and increasing the extened one with linux inside). Bad luck! I have forgoten that neither NTFS nor EXT3 can be moved, but only resized! :(

What should be the easiest and fastest way to achieve that? I have thought about making a ghost image or sth(by the way ghost should work also for ext3, right?)  of the extended one, then resize the ntfs and then set the ghost image back to my hdd. Could that work or by moving the partition of the linux wil mess up the grub and cannot boot anymore at all?

Thanx
Hope i didnt confuse u!
:)

---

### Post by ryanVickers on 2007-06-01
Could be clearer, but I understood it ok :)

Yes, I would make a second ext3 near the left of your HD then copy your existing image onto it.  I would back everything up first though because you never know if it will work, with the new /dev names and all.  If this is a worry, try changing the files that say where the partitions are and thier names before doing the move so it's sure to work!  Maybe someone else can list in detial what these might be?  I know the fstab and mtab, but there may be more...

---

### Post by moufa on 2007-06-02
hm..!
u mean changing the files before making the image?? are they only these 2 that i should change? are they located in /dev?
and  what should i use to make the images? 

thx!
:popcorn:

---

### Post by moufa on 2007-06-02
hey it seems that with the liveCD of gparted the extended and linux partitions can be resized/moved also from the left side! that probably solves my problem? should i also need to configure the files mentioned??
any suggestions??

;)

---

### Post by ryanVickers on 2007-06-03
I believe that as long as the device name does not change (which it shouldn't ,unless you delete and recreate partitions) there is no need to change the files.  I don't remember where the files are, I think /etc (where else!? :p)

I'm surprised that booting from the disk worked to move the start point.  I thought that everything that the installable version could do was it's limitations and as long as the partition in question was unmounted, it could do everything (but only) what was listed in the features window.  Well, if it worked though... great!

---

### Post by moufa on 2007-06-03
i used the gparted livecd not the ubuntu livecd! could be a reason!
:D

---

### Post by ryanVickers on 2007-06-03
Yeas, perhaps they've got a newer version on their own CD, rather than the ubuntu one.  But you would think that if you have gparted installed on the actual system, it would get updated periodically?..

---

