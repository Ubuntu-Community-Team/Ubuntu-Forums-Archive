---
title: "[SOLVED] Grub partition table invalid or corrupt"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by skintythe1andonly on 2008-09-15
Hi 

I was dual-booting but currently my laptops hard drive seems to be totally messed up and cant boot into either windows XP or ubuntu.

I was using kubuntu with kde4.1 but decided to change back to ubuntu as there were too many niggly things i didnt like about kde4.1. I had my home directory on a separate partition and thought that installing ubuntu wouldnt be really a problem and i could then just mount the same partition and i would still have all my files. I put in the 8.04 live CD and went into the installer. I said to format the kubuntu partition and use the other partition as home with my files in but i didnt format it. Maybe I shouldnt have done that? The installation failed. I cannot remember why now as I got distracted by my gf nagging and just cancelled the install. I thought I had just set up the install wrong and it hadnt started and i would come back to it later.

When I went to boot my laptop i get that it is starting Grub 1.5 and then "error 5". I looked this up in the manual and it says
"partition table invalid or corrupt. This is not good". Nothing happens after this message.

I have essential files backed up on the pc im using now but there are still some i would like (photos and stuff) on that ext3 partition. I can get at the windows files using a live CD and get all of them. The linux partition doesnt seem to appear then when i use that though. If i go to use the installer again. The whole hard drive appears as freespace. The windows partition doesnt even show up. Any ideas?

---

### Post by Herman on 2008-09-15
[TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk")

TestDisk is the best software for fixing  a corrupted partition table.
You can temporarily install TestDisk in your Ubuntu Live CD and it will remain as long as you have the CD booted. Otherwise, TestDisk is in [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/"), [System Rescue CD]("http://www.sysresccd.org/Main_Page"), [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"), [knoppix ]("http://www.knoppix.net/")and many others.

Be sure to take the time to read the documentation in the TestDisk site, [TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk"), it is very well explained.
Here is an additional page you can look at to see what running TestDisk might be like, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html")

I have had a corrupted partition table twice, once from trying out too may different kinds of partitioning programs, and another time from using a CD/DVD drive with a dirty optical lense.

TestDisk can scan your hard disk and find your partitions by searching for their first sectors and file system blocks, and it can write a brand new partition table for you based on the partitions you select.
It has saved a lot of people's data.

---

### Post by skintythe1andonly on 2008-09-15
Thanks....I managed to recover the data I was looking for. Im going to use this opportunity to give up the dual boot and totally switch. I may install Xp under vitual box this time.

---

