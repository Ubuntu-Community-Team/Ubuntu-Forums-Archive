---
title: "Question about automatic partition."
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by mfaheypride on 2006-06-16
Hi Ubuntu users, I am new to linux and I currently have windows on my laptop alone. Now i downloaded the iso file but still have to burn it (no problems there) I am looking to use the dapper drake nice looking gui install. In tutorials i have read that you can have the installer automatically edit your partition table. I want my partitions for ubuntu and for windows about 50/50, so I am wondering if this automatic partition resizer resizes it to 50/50 or something else? Thanks in advance.

---

### Post by x64Jimbo on 2006-06-16
Resizing partitions is very risky. PLEASE back up your data before you attempt this. The best thing to do when you want a dual boot is to plan both operating systems to make room for each other before you install either of them. Every time I set up a dual boot, I always divide up the hard disk space first, then install Windows, then install Linux (Windows doesn't play nice with other operating systems during install unless they're other Windows OS's) Ubuntu's installer should automatically detect your windows installation and make that option available in your GRUB menu.

---

### Post by mfaheypride on 2006-06-16
so i will make sure to back up the data. But, I do not want to get rid of my windows now and i was wondering does the automatic resizer resize the partitions 50/50 or something else?

---

### Post by x64Jimbo on 2006-06-16
I haven't personally used the auto-resizer, so I can't tell you for sure. Your best bet will probably be to manually partition so you can be very specific about how much space you want. It also lets you select your filesystem type, which I would highly recommend, as ext3 is pretty slow compared to some of the others.

---

### Post by mfaheypride on 2006-06-16
should i use fat32, or what, I am not really sure how to go about this. I have had ubuntu on my pc before(a friend installed it) but it didnt have network access for some reason so I am trying it again. Now would fat 32 be the fastest? should i make 3 partitions (windows xp (ntfs), shared (fat32), linux (ext3)) or how should i set it up. I have never done a linux install before so im not sure how to go about this really...

---

