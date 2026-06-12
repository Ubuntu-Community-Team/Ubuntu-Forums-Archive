---
title: "Yet another partitioning thread..."
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by audax321 on 2005-04-12
I just did a reinstall of hoary yesterday with the following setup:

hda1: root (10GB) - ReiserFS
hda2: /home (29 GB) - ReiserFS
hda3: swap (1 GB)

hdb1: /media/windows (200 GB) - FAT32 - Storage for a LOT of crap that needs to be shared with Windows if I ever need to install it again...

Right now, with everything setup, my root drive is using only 1.7GB/10 GB and my /home is using 15.6GB/29.0GB.

However, I have a WindowsXP Professional installation using VMWare on my /home set to use a max of 6GB (but I need to change that to 10GB or maybe more). Also, whenever I install games, I always install them to /home because this is a single user system and having them there lets me keep all my settings and completely avoid reinstalling them ever again :)

Now, would it be a good idea to reinstall hoary with a 5 GB root partition instead, so I can gain an extra 5 GB for the /home partition or will this be toooo small for future upgrades?

Also, while I'm on the subject of partitioning, ReiserFS or ext3?  I've heard bad things/horror stories about both of them (as with any file system), but since I'm a recent convert to Ubuntu from SuSE, I'm just used to using ReiserFS.... is there any reason I should consider switching to ext3?

Thanks :)

---

### Post by alastair on 2005-04-12
5 GB should be OK. The biggest thing people tend to forget is /var/cache for cached packages. But it is manageable.

As for filesystem - ext3 should be fine (it''s standard/safe/default). But I assume Reiser is fine as well.

---

### Post by audax321 on 2005-04-12
Thanks... I'll probably have to format then, no point in wasting space the root partition isn't going to use.

Another question is that now since I'm primarily using Linux and running Windows in VMWare, how do I defragment my 200GB FAT32 drive? Is there a program that will let me?

---

