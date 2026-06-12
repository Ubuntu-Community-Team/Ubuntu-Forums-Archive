---
title: "multiboot install problem"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by ddevore on 2005-11-23
I am running into a problem installing with windows. I don't think that it is a windows problem but that is what I am blaming it on. I think the blame falls there because windows does not like being installed on a partition other than the first partition.

This is what I have done with my results. 

1. Installed windows on the first partition of the first HD, I tried to create a small partition for /boot but windows wanted to install on it which wouldn't have worked. 

2. The current setup is (first HD):
partition 1 - windows 26gb
partition 2 - /boot 512mg
partition 3 - /home (fat32)
partition 4 - logical
locical 1 - swap
logical 2 - / for linux install 1
logical 3 - / for linux install 2
logical 4 - nothing

When I install the system it will not stop going through the user setup screen and when it gets to the second step it goes through a lot more manual setup and has a problem with my video. If I install it on my second HD, swaping them out and making the second the primary, the install goes without a hitch and loads the x system properly with only 1 question through the second stage. It is a beautiful thing. 

My question:
Is my partitioning on my main HD a problem? 

Do I need the /boot at the begining or is there something else I need to do differently? 



Thanks

---

### Post by yesplease on 2005-11-23
I noticed that /home is Fat32 on disk one and this could give problems [http://ubuntuforums.org/showthread.php?t=89992](http://ubuntuforums.org/showthread.php?t=89992) I am not sure if that applies here.

Do you mean to say that you have 4 primary partitions? Anyway, there is no need for that, I think. Why do you do that?

---

### Post by ddevore on 2005-11-23
Because that is what I have always done in partitioning. I could use the LVM for all but the main partitions but just didn't do that. I figured that it would be better to do the /boot and /home as primary.

I am going to try the ext3 for the home and will throw it in the LVM because I can't figure any reason for not putting it there and I can resize it then.

Thanks

---

### Post by yesplease on 2005-11-23
Logical Volume Manager? Is that a windows tool for partitioning? Better use the Live CD (gparted) or the install CD.

boot can be logical (bootable flag on), /home doesnt benefit from being on primairy as far as I know. Good luck.

---

### Post by ddevore on 2005-11-23
Yes I would use the LVM from the install disk. The windows thing is not good for that kind of thing.

---

### Post by ddevore on 2005-11-23
I have changed my home directory to be ext3 and it seems to work. 

Now for the rest of the system.

Thanks for your help.

---

