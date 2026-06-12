---
title: "Installing ubuntu along side with windows"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by Kinnza on 2008-05-28
hi
i just installed ubuntu about a week ago, and i used another partition for that, and left the previouse winows running

first i have a question, during the installation it asked for a swap partition, i didnt give it one and it warned me that it might cause probs. how true is that? how big should be such a partition?
also, i formated the linux partition in ext2, is that ok?

the problem is that when i boot windows, it tries to do a check disk or something. basicly it identifies the linux partition as a bad one and tries to scan each time, and get stuck (it doesnt even start the scanning).
do you know if i can make it just skip it? ignore that partition? cause its pretty annoying...

---

### Post by logos34 on 2008-05-28
Technically, you can run without a swap but you won't be able to hibernate. Nor will it run as efficiently.  Can't you spare at least 512mb to 1 x your ram? That's all you really need for everyday computing on linux. (I have 512 mb ram and I'm about ready to reduce my 768mb swap to 512 because I never see it load up more than ~350mb) 

ext2 does not have journaling.  Less resilient.  So if you have a power outage (and you're not on APC) you won't recover as easily.  You'll have to google for the details but ext3 is the way to go (and the default). There's also JFS, XFS, Reiser4. 

Ext3 is rock-solid in my experience.  I've had at least 3 blackouts here and I can boot right back up--hardly misses a beat. (try that on ntfs!) I'm just plugged in to a surge protector powerstrip.  Knowing that I can always recover with ext3 means I don't have to go out and spend $50 on an battery backup.

---

### Post by Kinnza on 2008-05-28
oh thanks ALOT!
i will move to ext3 i think i have to reinstall anyway 
and then i will try to spare few G for it... (i have 2 G so according to your calcs i need 1g swap am i correct?)

---

### Post by logos34 on 2008-05-28
if you also want to be able to hibernate then you need 1 x your ram.  So 2 gb in that case.

---

### Post by Kinnza on 2008-05-28
oh ok cool thanks :D

now im just left with the stupid disk checking when windows boots

---

### Post by logos34 on 2008-05-28
> **Kinnza said:**
> oh ok cool thanks :D

now im just left with the stupid disk checking when windows boots

wish I had suggestion to offer on that one.  good luck

---

### Post by Kinnza on 2008-05-29
well no biggie, i just hope someone else knows...
its pretty annoying

---

### Post by housam on 2008-05-29
Try installing this [[COLOR="Red"]_driver_[/COLOR]]("http://www.fs-driver.org/") as it makes windows to recognize ubuntu partitions . it may make it stop trying to check the HDD.

---

### Post by Kinnza on 2008-05-29
thanks i will try that :D i'll let you know it if works

---

### Post by Kinnza on 2008-05-30
ok i installed it and now windows see the linux drives and all but it still wants to scan it on load....

---

