---
title: "Hard drive upgrade."
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by kameleon25 on 2007-09-20
I have been running Ubuntu 7.04 on my server since the day after it was released. My poor little 10gb drive is running out of room. I am about to need to upgrade disks. I have a 250gb drive that I want to use as the main drive now. What is the easiest way to accomplish this?

kameleon

---

### Post by Pumalite on 2007-09-20
Plug in the new hard drive and use this to convert it in your new /home:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by kameleon25 on 2007-09-20
Thank you for the fast reply. But I am wanting to replace the whole disk. Not just add the 250gb to my /home portion. I do not use this machine for anything but a server and am about to be putting a few websites and such on there. It will also be a media storage. Hence why I woul drather just replace the whole disk but not lose my current settings if I can help it.

---

### Post by Pumalite on 2007-09-20
Backup /home, including 'Hidden Files' and do a fresh install in your new drive and then restore yout /home.

---

### Post by chrismine on 2007-09-20
Think about cloning the old drive to the new drive with G4U and the use gparted to rezise or create different partitions.

---

### Post by kameleon25 on 2007-09-20
Ok. Here is what I want to do. Currently I have a 10gb disk with the swap and ext3 partitions on it. The non-swap mounted portion is mounted as /

I want to replace this entire disk. Let's just say it is about to fail on me but I can get all the data off of it. I want to replace it with the 250gb disk I have. And have it mounted as /

I saw here: [http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade](http://encodable.com/tech/blog/2006/10/30/Ubuntu_Linux_Hard_Drive_Upgrade) wher ethe guy did it but that was before 7.04 was released and I want to make sure that nothing will get in my way with it. I just found that link above and it appears as though I will be ok as long as I change over all the stuff he missed before I swap.

---

### Post by kameleon25 on 2007-09-20
> **chrismine said:**
> Think about cloning the old drive to the new drive with G4U and the use gparted to rezise or create different partitions.

That is what I was looking for... I did not know about G4U. Thank you. I will look into that.

---

### Post by chrismine on 2007-09-20
If you do it like in my previous post you will not have those problems because G4U makes a sector by sector copy of the drive - everything will stay as is, you just need to resize the partitions because the partitions will be the same as on the old drive.

---

### Post by Pumalite on 2007-09-20
That's right. That's why I recommended saving /home and going for a fresh install.

---

