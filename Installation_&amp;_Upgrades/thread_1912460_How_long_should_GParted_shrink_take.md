---
title: "How long should GParted shrink take"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by georgeos on 2012-01-20
I'm shrinking my Ubuntu partition to make room for a Windows one, it's a 600gb partition, and I'm shrinking it to 350gb, and it's taking a long time. It's been 20 minutes now. The thing that is strange is that I'm not moving any data, so it really shouldn't take this long, seeing as I'm essentially creating a new partition out of empty space. Someone help please!

GH

---

### Post by Quackers on 2012-01-20
Depending on how much data is in the partition it can take 2 and a half hours on occasions. Go and put the kettle on :-)
What is currently in that partition and what format is it?

---

### Post by cortman on 2012-01-20
> **georgeos said:**
> I'm shrinking my Ubuntu partition to make room for a Windows one, it's a 600gb partition, and I'm shrinking it to 350gb, and it's taking a long time. It's been 20 minutes now. The thing that is strange is that I'm not moving any data, so it really shouldn't take this long, seeing as I'm essentially creating a new partition out of empty space. Someone help please!

GH

No worries. I just did some major partition shrinking/rearranging on my PC, and GParted took over an hour for some operations. I think you're ok.

---

### Post by lisati on 2012-01-20
Your best bet is to be patient. I've had partition resizing take several hours as well: if memory serves correctly, the longest took about 4 hours.

---

### Post by s3a on 2012-01-20
If you're not a newbie or are consciously choosing to do so anyway, you can use LVM2 which allows you to leave a chunk of your hard drive unallocated and then choose to allocate space to any partition while the system is running. You can't shrink online but you can extend online. Online means while the system is running and not anything with the Internet.

---

