---
title: "Partitioning...in reverse?"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by jr.gotti on 2005-11-24
So I have a full linux box. 

However, I have come to realize, that as of now, you CANNOT completely eliminate windows. As i will continue to run linux for my day to day work, I need windows for photoshop (I HATE the Gimp), 3ds max, Maya, Lightwave, yada yada...

Now, how can i resize/move my linux partitions to the beggining of the drive, so i can install windows in the remaining space?

I don't want to lose my linux, as i have set a lot up.

(I tried GParted, but i cannot edit hda1, since it is "active"

any ideas?

---

### Post by earobinson on 2005-11-24
you could use a linux live cd, i think KNOPPIX has a partitioner built in. or something like the partition magic boot disks

Just a note it is much harder to install windows after linux than linux after windows, windows dont play nice.

---

### Post by jr.gotti on 2005-11-24
So, would you say it would make more sense to scrap everything and insall windows first?

---

### Post by yesplease on 2005-11-24
Try resizing first, if you cant get it working there is still the option to scrap everything.

Windows will overwrite the mbr, be prepared for that: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

---

### Post by poptones on 2005-11-24
Why not set up a virtual windows host?

---

