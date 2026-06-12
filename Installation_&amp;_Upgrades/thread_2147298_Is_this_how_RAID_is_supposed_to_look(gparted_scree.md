---
title: "Is this how RAID is supposed to look?(gparted screens)"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by MeltedFlame on 2013-05-21
Hello again :-),

I had a RAID 1 device: 2 seagate HDD's - 160gb & 500gb, working for quite some time, untill one day they both dissapeared. I used gparted to take a look and I found both the Disks had been formatted and the partition table deleted; they were just appearing as unallocated spaces. So, I created a new Partition(ext2) on the 150gb and formatted, hoping it would use both Disks.

Now, the HDD's looks like this and I have no idea if my 500gb HDD is active at all? - What do I need to do to create the correct array?

[http://www.flame-d.co.uk/RAID1.png](http://www.flame-d.co.uk/RAID1.png) - the 150gb disk.

[http://www.flame-d.co.uk/RAID1_2.png](http://www.flame-d.co.uk/RAID1_2.png) - the 500gb disk.

Cheers,

Dan.

---

### Post by linuxtechguy on 2013-05-21
I would use ext3 or ext4 not sure why you made it ext2. The 500gb disc doesnt look partitioned or formatted at all. You should just follow a guide to install a new disc and mount it where you want.

---

### Post by MeltedFlame on 2013-05-21
> **linuxtechguy said:**
> I would use ext3 or ext4 not sure why you made it ext2. The 500gb disc doesnt look partitioned or formatted at all. You should just follow a guide to install a new disc and mount it where you want.

I'm not quite sure why I made it ext2 either; I think I read a comparison guide an the ext2 seemed suitable for me, at the time...

I was sure that was my only option, but, re-thinking it, if both the HDD's are being used by the RAID 1 function, why isn't the 500gb affected at all? :/

---

### Post by darkod on 2013-05-21
First of all, are you talking about fakeraid (bios raid) or software raid (mdadm)? That is important because they work in a very different way.

---

### Post by MeltedFlame on 2013-05-22
> **darkod said:**
> First of all, are you talking about fakeraid (bios raid) or software raid (mdadm)? That is important because they work in a very different way.


I created the RAID in BIOS/BIOS RAID, and to this day the BIOS menu shows functionality between the two HDD's and that they're working correctly. What you see above(on the screens) is whats happening in gparted software. 

So, I'm not sure if I can just go ahead and create an equal partition to the 150gb from the 500gb and it to work insync with the 150gb.

---

