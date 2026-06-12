---
title: "&quot;cloning&quot; install to another drive"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by rkleemann on 2008-05-18
Hi,

I have 2 laptops (different brands) and I've installed Hardy on one of them, installed some different themes, installed MS Office, etc... did a lot of configuring and I did not want to have to repeat that all over.

I wanted to image the 2nd laptop's disk with what I've already spent time configuring, and then run grub on that.

Two questions I have:

1. What is the best/correct way of imaging so that I can simply drop in the drive in the 2nd laptop and have it boot up?

2. Will Ubuntu automatically detect the different hardware and necessary drivers since it's a different computer, different drivers?

Please help me so I don't have to go through the days of configuration I just spent on the other... :(

Thanks for any help!

---

### Post by tamoneya on 2008-05-18
try using partimage: [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by Sef on 2008-05-18
> 1. What is the best/correct way of imaging so that I can simply drop in the drive in the 2nd laptop and have it boot up?

[Clonezilla]("http://www.clonezilla.org/") is another way to clone.

---

### Post by Pumalite on 2008-05-18
'2. Will Ubuntu automatically detect the different hardware and necessary drivers since it's a different computer, different drivers?'

Sometimes it works; sometimes it doesn't. If you are lucky all you have to do it reconfigure your xserver.

---

