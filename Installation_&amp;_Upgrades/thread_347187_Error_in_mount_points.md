---
title: "Error in mount points"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by RDUBBALO on 2007-01-26
Ok I am going to install I partitioned the drive into 4 parts 1. 5 gb 2. 39mb 3. 53gb 4. 92 gb. Ok I am at the screen for preparing the partition mounts and dont know what to do i tried to set one as swap ond one as home , but everythime it goes to do the install it stops and says error and to go back. How do i set up the partion mounts? Please help me out thanks.

---

### Post by RDUBBALO on 2007-01-26
Oh yeah i already have windows xp on the HD as well.

---

### Post by meng on 2007-01-26
You should set one as swap
one as home (/home)
one as root (/)
and the other one - do whatever you want with it.

Make sure you have one set as the root partition /

---

### Post by RDUBBALO on 2007-01-26
cool ok so do you have any idea as to which to set them as. The root only needs to be a small one right and swap should be like 2 gigs I dont know I was just saying, but as for the fourth what do i do with that, and which one has my other OS on it.

---

### Post by meng on 2007-01-26
Well, first make sure you don't overwrite or format your Windows partition!
From the other three partitions, 2 GB is ample for swap.
I would give at least 5 GB to the root partition, the base install will be 2+ GB and then you may want to add install additional packages afterwards.
Then /home can be the remaining partition.

---

### Post by RDUBBALO on 2007-01-26
should I format them all I formated the one i created and when I go to make the others swap or /home it wont let me because of the file tyoe,.

---

### Post by meng on 2007-01-26
swap should be of filesystem type swap. You don't need to format it.
/home should be of filesystem type ext3. You should format it.
/ should be of filesystem type ext3. You should format it.

Do not format your Windows partition (I assume you have Windows already installed, but I could be wrong.)

---

### Post by Pobega on 2007-01-26
You also may want to defragment your Windows partition, if you don't do this before partitioning data loss can occur.

These are my opinions on partition size:
Swap should be RAM*2
/home should be 60%
/ should be 40%


So apparently you're working with a 200 GB HDD, and from what I understand you want to keep Windows installed? I'll also assume you have 1 GB of RAM. So I would say:

80 GB for Windows
2 GB for swap
68 GB for /home
50 GB for /

Root holds everything that isn't in your /home, so it shouldn't be as small as you're thinking. It holds all of your binary files, executable files, pixmaps, and system sounds (Among tons of other things). /home just holds your settings, and traditionally your music/pictures/documents. If you have a lot of music I would suggest a large /home partition, but if you really aren't a music partition maybe switch /home and / (Making / bigger than /home).

---

### Post by RDUBBALO on 2007-01-26
AT and NTFS filesystems may not be used on filesystems used by the system (/, /boot, /home, /usr, /var, etc.). It is usually best to mount them somewhere under /media/.

---

### Post by RDUBBALO on 2007-01-26
> **RDUBBALO said:**
> AT and NTFS filesystems may not be used on filesystems used by the system (/, /boot, /home, /usr, /var, etc.). It is usually best to mount them somewhere under /media/.

whats this mean

---

### Post by meng on 2007-01-26
See my earlier post. You have to choose Linux-compatible filesystems for the partitions you are mounting to / and /home. I recommend using ext3

---

### Post by RDUBBALO on 2007-01-26
> **RDUBBALO said:**
> Ok I am going to install I partitioned the drive into 4 parts 1. 5 gb 2. 39mb 3. 53gb 4. 92 gb. Ok I am at the screen for preparing the partition mounts and dont know what to do i tried to set one as swap ond one as home , but everythime it goes to do the install it stops and says error and to go back. How do i set up the partion mounts? Please help me out thanks.

this is how it is partitioned I guess windows is on the 92gb part.its a 160 gb hdd. I have 39mb for the swap.

---

### Post by meng on 2007-01-26
At only 39 MB for swap, it's probably not worth having swap! Perhaps 512 MB, 1 GB or even 2 GB would be a better size.

---

### Post by RDUBBALO on 2007-01-26
> **meng said:**
> See my earlier post. You have to choose Linux-compatible filesystems for the partitions you are mounting to / and /home. I recommend using ext3

ok so should i do the partitioning over again because one is fat 16 and one is fat 32 and one is ntfs and the last is ext3

---

### Post by meng on 2007-01-26
Yes, but where is your Windows installation? You previously said it was on the last partition, but it can't be because it has to reside on NTFS.

---

### Post by RDUBBALO on 2007-01-26
yes its on the ntfs the bigger partition i re partitioned the rest to ext 3 now the only question i have is when it starts to install it says no mount selected for number 2 should i just continue it says it wont be used

---

### Post by RDUBBALO on 2007-01-26
i guess its the one that has windows

---

### Post by meng on 2007-01-26
Is number 2 the WIndows partition? Don't guess, you'll regret it. If so, it's fine to leave it unmounted for now.
Swap must be made as a swap partition, not ext3. The others can be ext3.

---

### Post by RDUBBALO on 2007-01-26
well i went to go back and i did it over again so now it is going through the install and is almost halfway done it didnt give me that option to continue anyway. oh well i am not too worried if i lose windows i backed up the important stuff and i really dont like windows anyway.but hopefully it work out ok

---

