---
title: "Linking Folders In Vista/ubuntu"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by techgeek40 on 2007-12-26
I have a (C) drive (Vista) and my linux
But, I have pictures/documents folders in each - 
I do NOT want to copy the contents of the Pictures/Documents from my Vista side to Ubuntu - it's over 3 gigs in size

So is there a way to "link" the pictures and documents folders in Linux to "see" the documents and pictures on Vista? 

So that means if I click on Documents in Linux it would actually see the documents on the Vista partition

---

### Post by taurus on 2007-12-26
If you want to access your vista partition, you just have to mount it.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Hmarroqu on 2007-12-26
an easier way i think than doing the above would be creating a partition for both...FAT32, and using that as a shared partition, storing everything there and it would always mount when you set it as /media.  Thats what i have for my dual boot.

---

### Post by loudnlownoma on 2007-12-26
> **taurus said:**
> If you want to access your vista partition, you just have to mount it.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

That will just mount the whole partition/drive.  I believe the OP wants to be able to click on Documents in the Home folder and see the Documents folder from his NTFS partition/drive.  Not sure if it's possible, or how exactly to do it, but it seems like you would be able to change the folder's properties to point to the location of that folder instead, or something similar maybe.  I'd offer to test, but at work currently.  If still unanswered when I get home tonight, I'll poke around a bit to try and find out.

---

