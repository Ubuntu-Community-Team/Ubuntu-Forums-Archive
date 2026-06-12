---
title: "partitioning question"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by kidob on 2007-06-08
I'm just about to install 7.04 and I wanted to ask a couple questions before-hand just to be sure and start right. My main question is about partitioning. I've read lots of threads and instructions but some personalized advice would be much appreciated. 

I'll be installing a dual boot on an XP system with a single 40 GB HDD. The suggestion is at least 10 GB for the Ubuntu partition and I'm planning to go for 15 GB (wish I could spare more! Maybe after I finally uninstall my MS Word). I believe I should also set up a "swap partition" of about 500 MB (just out of curiosity, what exactly is the swap partition for??). Some people seem to suggest setting up an additional "FAT32" partition, and some seem not to. I'm not sure what FAT32 is, but I believe it's something both Windows and Linux can write to? Should I set one up? My drive is already on the small side as it is, so I'm thinking I should do without this if I can. And finally, I'm a bit confused about how and whether I'll be able to use particular programs from both operating systems. For example, right now I have Firefox installed for Windows. Will I be able to use that from Ubuntu, or will I have to install it separately on the Ubuntu partition? And the OpenOffice suite?  I definitely don't want to use any virtual Windows stuff, I'm aiming to eventually become totally Windows-independent!

I know that's a big pile of annoying questions, but any tips on any or all of the above would give me so much peace of mind for the installation process, so thanks in advance!

---

### Post by merlinus on 2007-06-08
The swap partition is used when you run out of RAM.  ubuntu writes stuff to disk temporarily.

A good rule of thumb is to give swap about 1.5 times your RAM.

Firefox and Open Office are installed automatically.  You will be able to retrieve your bookmarks.html file from the windows installation, however.

There are drivers that will allow you to read and write to and from ubuntu (ext3) and windows (ntfs) partitions, so there is no need to set up FAT anything.

Good luck!

-merlin

---

### Post by kidob on 2007-06-08
Thanks merlin, that answers all my questions plus some questions I didn't even know I had! I'll probably install on Tuesday...

---

### Post by davec64 on 2007-06-08
Just a quick addition, you might want to consider setting up your /home folder on a separate partition. This is just a practical suggestion really which allows you format the partition holding Ubuntu and keep all your saved data. great if you really cock things up!! And also good if you want to try a different distro!

I appreciate space is at a premium, so it might be something to bear in mind for the future! It is possible to create a partition and move your /home directory over to the new partition.

All the best

---

### Post by kidob on 2007-06-08
> **davec64 said:**
> Just a quick addition, you might want to consider setting up your /home folder on a separate partition. This is just a practical suggestion really which allows you format the partition holding Ubuntu and keep all your saved data. great if you really cock things up!! And also good if you want to try a different distro!

I appreciate space is at a premium, so it might be something to bear in mind for the future! It is possible to create a partition and move your /home directory over to the new partition.

All the best



Actually that makes a lot of sense, I'll definitely do that. I've never used Linux before but I'm guessing the /home directory is like the "my documents" folder in Windows, where you keep all your text and multimedia stuff. In that case it would make sense to devote at least 5-7 GB to that. It hadn't occurred to me, but if I move all my multimedia stuff out of the Windows partition I should be able to free up at least 20 GBs for Ubuntu, maybe do a 10/10 split. But should both partitions be "primary" partitions or should the one for the /home folder be logical? Thanks!

---

### Post by davec64 on 2007-06-09
If memory serves me right you can only have 2 primary partitions on a disk. So if you're dul booting with windows  then /home would have to go on a logical partition.

All the
best

---

### Post by kidob on 2007-06-09
Ah, I thought it was 4 primaries max, so that clears things up. NOw I've got it all planned, Tuesday's the day!

-kidob

---

### Post by merlinus on 2007-06-09
4 primaries, and a huge number of logicals in an extended.  One of your primaries can be made into an extended.

-merlin

---

