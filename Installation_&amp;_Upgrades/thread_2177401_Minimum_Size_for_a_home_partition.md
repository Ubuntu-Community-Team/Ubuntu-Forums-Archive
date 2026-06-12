---
title: "Minimum Size for a /home partition?"
date: 2013-09-28
forum: Installation &amp; Upgrades
---

### Post by hwCDFd3 on 2013-09-28
Here's how my partitions are currently set up:

500 GB HDD:
[21 GB Free Space]
[145 GB Windows partition - unfortunately I can't move it so it starts at the beginning of the Hard disk]
[175 GB Data partition]*
[145 GB Extended partition, containing / and Swap]

SDD:
[30 GB used as a cache for the HDD in Windows]

*Note that my "My Documents." "My Downloads," etc. folders are relocaed to the data partition. The "Documents," "Downloads," etc. folders in linux are symlinked to the same folders.

----------
I'd like to reinstall Ubuntu and put / on the SSD. I'd also like to make use of the 21 GB on my HDD before the windows partition. Here's what I was thinking:

HDD:
[8 GB SWAP]
[13 GB /home]**
[145 GB Windoze]
[320 GB Data]

SDD:
[30 GB / ]

**Alternatively, I could make this 21 GB and move the SWAP partition to be after the Windows Partition.

---
My question is: What's the minimum size I can make my /home partition so I will probably never run out of space, given that all of my Documents, Downloads, and Media will be on a separate partition?

---

### Post by Lars Noodén on 2013-09-28
It depends on what you are doing.  If you have no photos, no music and no videos, then you can get by with less than 5GB -- probably.  If you have a lot of photos, then that increases your space needed.  It's even worse for music and if you have video, you will probably need an extra drive.  One trick is that you can also symlink directories from your home directory to your Data partition.  I usually set up 10GB for the system, a bit for swap, and then the rest for /home.

---

### Post by deadflowr on 2013-09-28
> **Lars Noodén said:**
> It depends on what you are doing.  If you have no photos, no music and no videos, then you can get by with less than 5GB -- probably.  If you have a lot of photos, then that increases your space needed.  It's even worse for music and if you have video, you will probably need an extra drive.  One trick is that you can also symlink directories from your home directory to your Data partition.  I usually set up 10GB for the system, a bit for swap, and then the rest for /home.

You can go as low as less then 1GB for home, if you a) don't add any files like pictures, videos, etc. and b) clear your various caches like browers regularly.

I have a fresh(somewhat fresh) install of saucy and home takes up less then 500MB, including a single picture for wallpaper purposes.
And I haven't even cleared the caches for anything.

---

### Post by oldfred on 2013-09-28
I have my /home on my SSD inside my / (root). But symlink all the data folders and even some hidden folders with lots of data like Firefox & Thunderbird profiles to data partition.
My entire system is 9GB with about 2GB of that for /home. But 1.5GB of /home is .wine for Picasa. Or home settings without any data can be very small.

---

### Post by hwCDFd3 on 2013-10-01
Thank you all. Every answer was helpful :D

---

