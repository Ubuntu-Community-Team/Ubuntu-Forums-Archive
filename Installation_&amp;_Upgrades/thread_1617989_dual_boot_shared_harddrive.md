---
title: "dual boot shared harddrive"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by mackubex on 2010-11-10
Greeting , 

I'm kinda new to this awesome world of linux , I decided to tk tha plunge with ubuntu ! 

For this I repartitioned my harddrive (erasin org windows) into 3 drives. : 
Drive1 : 40gb to load windows 7 
Drive2: 40gb to load ubuntu 
Drive3 : 60gb 

Now I want to use drive 3 as a common drive (music and pictures nd documents). Bet windows and linux 


Some1 plz advice how ?

---

### Post by sikander3786 on 2010-11-10
Hi. Welcome to the forums :popcorn:

We need some info. Please post the output of

```
sudo fdisk -l
```

from an Ubuntu terminal. You'll find it under Applications > Accessories > Terminal. Your password will not show up as any character or asteisks * when you type it. Just type and hit Enter blindly ;-)

Linux support NTFS drives and you can mount them in Ubuntu. But it would be better to know your setup.

See this link for a workaround.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

