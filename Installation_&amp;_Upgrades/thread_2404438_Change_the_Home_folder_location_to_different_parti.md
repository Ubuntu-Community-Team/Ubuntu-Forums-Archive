---
title: "Change the Home folder location to different partition?"
date: 2018-10-24
forum: Installation &amp; Upgrades
---

### Post by vampyra666 on 2018-10-24
Hello again. 
Last question, I hope, after upgrading to 18.04.

I used to have the 14.04 LTS before, and have 3 separate partitions. One is for the Ubuntu installation, the other is Windows, and the other is a "fuse" file system format (?) that I use in both Ubuntu and Windows. In the fuse partition I had a folder with my Home folder files (Documents, Pictures, Music etc) for both Windows and Ubuntu. I had (somehow) set the Home folder to store things in the fuse partition and it worked like a charm. However, after the format and clean install of the 18.04 I cannot manage to set it like this again... I've searched everywhere and have not found a way to do it. 
Any idea how it can be done? 
I already have the fuse partition with the previous installation Home folder already there (all files inside), so I just need to set the new installation Home folder to point at that location instead of the local one. 

Thanks in advance.

---

### Post by dino99 on 2018-10-24
The bklid output and fstab must matching.
Have you set a crypted 18.04 installation ?
To be safe, you might want a /home for ubuntu only, that can be shared with the windows one.

---

### Post by vampyra666 on 2018-10-24
Unfortunately I don't understand the bklid and fstab things...
No, it was a normal installation. 
That sounds right, how can I do that? It must be in the second partition, where it is now.

---

### Post by dino99 on 2018-10-24
I mean:
> sudo bklid
> cat /etc/fstab

Declare the new path inside fstab (sudo gedit ./etc/fstab) if you move the /home partition (or create a new one.
[https://superuser.com/questions/1211606/partitioning-for-dual-boot-with-shared-data-on-a-single-drive](https://superuser.com/questions/1211606/partitioning-for-dual-boot-with-shared-data-on-a-single-drive)

---

