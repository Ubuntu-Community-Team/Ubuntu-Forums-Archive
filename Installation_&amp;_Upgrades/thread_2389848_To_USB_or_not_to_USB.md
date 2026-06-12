---
title: "To USB or not to USB"
date: 2018-04-22
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2018-04-22
In my quest to upgrade my server to 16.04 without major interruptions, I installed 16.04 on a 32 gb usb 3.1 thumbdrive (~$10) so I could easily switch back and forth while I was getting everything I needed working. I haven't yet moved the OS to the server's hard-drive and am wondering if I should. I don't see any significant degradation in performance, and I cloned the thumbdrive so if one fails, I can easily pop in the clone. I'm tempted to leave it as is unless someone gives me good reason not to.

---

### Post by TheFu on 2018-04-24
Depends on what you need from the system.

Flash storage has fairly limited write cycles when compared to SSDs or  spinning disks.  It is also almost always slower and many systems have issues booting from USB3 when compared to USB2 ports.  All storage fails and flash will almost always fail after a few years (best case) due to the number of write cycles caused by server logging and just day-to-day use.

I've had name-brand flash storage fail after a few months of daily use like this.

But if you find those things aren't a concern for what you want from a server, then it seems like a workable option for this specific situation.  Plus the fact that millions of people run Linux on their Raspberry Pi SBCs using microSD flash storage for years with only minor issues is a good sign. My r-pi storage got corrupted and refused to boot a few weeks ago after about 18 months of nearly constant uptime.  Swapped out the flash storage and restored a backup - everything is fine again.

Modern flash storage has write-leveling, so as long as all the storage isn't used, there will be plenty of space to write-level across, spreading out the wear.

I would suggest that you consider setting up alternate OS partitions/LVs on the internal storage.  Since it is a best practice to keep the OS partition/LV separate from data and HOME partitions, it shouldn't be much storage on a modern disk/ssd to have 2 25G partitions for the different OSes.  Dual booting different Linux versions is pretty safe, since they both know how to play-nice together.  Getting a daily, weekly, or monthly backup plan that works for you is still important from a system security perspective.

But if it works for you, great! Flexibility is one of the main reasons we all run Linux after all. ;)

---

### Post by bilkay on 2018-04-24
> **TheFu said:**
> Depends on what you need from the system.

Flash storage has fairly limited write cycles when compared to SSDs or  spinning disks.  It is also almost always slower and many systems have issues booting from USB3 when compared to USB2 ports.  All storage fails and flash will almost always fail after a few years (best case) due to the number of write cycles caused by server logging and just day-to-day use.

I've had name-brand flash storage fail after a few months of daily use like this.

But if you find those things aren't a concern for what you want from a server, then it seems like a workable option for this specific situation.  Plus the fact that millions of people run Linux on their Raspberry Pi SBCs using microSD flash storage for years with only minor issues is a good sign. My r-pi storage got corrupted and refused to boot a few weeks ago after about 18 months of nearly constant uptime.  Swapped out the flash storage and restored a backup - everything is fine again.

Modern flash storage has write-leveling, so as long as all the storage isn't used, there will be plenty of space to write-level across, spreading out the wear.

I would suggest that you consider setting up alternate OS partitions/LVs on the internal storage.  Since it is a best practice to keep the OS partition/LV separate from data and HOME partitions, it shouldn't be much storage on a modern disk/ssd to have 2 25G partitions for the different OSes.  Dual booting different Linux versions is pretty safe, since they both know how to play-nice together.  Getting a daily, weekly, or monthly backup plan that works for you is still important from a system security perspective.

But if it works for you, great! Flexibility is one of the main reasons we all run Linux after all. ;)

Thanks for responding. According to hdparm, the usb 3.1 is about 75% as fast as my harddisks (which have my home and data files), and I don't see and significant difference in performance. I think the only serious writing to the usb is logs and mysql (mostly mythtv). It should be interesting to see how this works out.

---

### Post by TheFu on 2018-04-24
Databases are particularly hard on flash storage write wearing. I wouldn't.

If this issue is solved, please mark it so using the Thread Tools button near the top.  That helps the community looking to answer or seeking answers.

---

### Post by bilkay on 2018-04-25
> **TheFu said:**
> Databases are particularly hard on flash storage write wearing. I wouldn't.

Here's a good tutorial on moving a mysql database (on ubuntu 16.04): [https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-16-04)

---

