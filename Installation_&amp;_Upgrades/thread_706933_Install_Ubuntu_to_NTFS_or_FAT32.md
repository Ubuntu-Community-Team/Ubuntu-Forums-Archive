---
title: "Install Ubuntu to NTFS or FAT32?"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Reinie on 2008-02-24
I created an Ubuntu 7.10 install/boot CD.
I have a 250G HD from which I currently boot Windoze XP.
I have 5 partitions on this drive. XP is on an NTFS partition, and the other 4 are FAT32.
(When I created the partitions a year ago, it appeared that Linux did not work well with
NTFS.)
7.10 appears to be OK with reading/writing NTFS, but is it OK to install Ubuntu 7.10 to an NTFS
partition, or should I leave it as FAT32?
I looked through the documentation (but didn't see anything) and searched the forums, (but got so much it was overwhelming). Does the search mechanism use REs? (Even so, searching XP, boot, NTFS got me an overwhelming amount of posts.)

      PReinie

---

### Post by hugmenot on 2008-02-24
Both are a bad idea. Format as Ext3 or Reiser. Linux file systems (need to) have features, like permissions, that those don't support.

---

### Post by Reinie on 2008-02-24
Are those an option on the install CD?

---

### Post by mrsteveman1 on 2008-02-24
The real issue here is that the in kernel NTFS driver can't write safely, hence Linux cannot root itself from an NTFS volume.

You can root from FAT32 but its not a good idea.

Just reformat one of the partitions as ext3.

---

### Post by Partyboi2 on 2008-02-24
> **Reinie said:**
> Are those an option on the install CD?
Yes the options are there to format partitions as ext3. With those 4 fat partitions are you planning on changing them to ext3 and installing ubuntu?

---

### Post by Reinie on 2008-02-24
Ext3 seems to be what is used (recommended) here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).

I think I found documentation about formatting as ext3 and it appears to be on the Ubuntu 7.10 install CD. [https://help.ubuntu.com/community/Installation/I386](https://help.ubuntu.com/community/Installation/I386) which leads to [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition).

I'm not sure why I didn't see that documentation before I asked y'all.

I also read somewhere about which flavor of Ubuntu to use, and realized that I'd better get more RAM than the 256Meg I currently have!

---

### Post by Reinie on 2008-02-24
WRT Partyboi2's post...
My primary disk is partitioned as follows:
10G FAT32 and blank.
18G NTFS booting to XP. This will be kept.
46G FAT32 all Windoze programs not part of XP OS.
127G FAT32. Data for XP and a Linux.
35G, currently FAT32, for a Linux OS.

I also have a 2ndary disk which had W2K Pro, until it refused to boot, but seems OK for data:
19G NTFS
19G NTFS

I plan to keep all partitions as-is, except I don't care about the 10G partition, and I'll do what's best for the Linux 35G partition.

   PReinie

---

### Post by hugmenot on 2008-02-24
Actually the 10Gig partition would be optimal for the Linux system files.
You will likely never use more than that for program installs.
You could make one of the other ones your /home partition, so that you have a separation of user and system data. This is very useful in case of a reinstall, because you can wipe the system without touching your personal files or settings at all.

In the manual installer I would format it like

10 GB to   /
35 GB to   /home


and just mount the other partition later as /media/windows, or so.

---

### Post by Partyboi2 on 2008-02-25
If you are going to manually create the partitions you will also need to make sure you have a /swap partition which should be about x2 the amount of ram you have in your system. But don't go past 2gig as then you would be just wasting space. So like hugmenot suggested it would be something like this:

10 GB to   /
34 GB to   /home
1 gig /swap (if you had 512 ram)

---

### Post by Reinie on 2008-03-02
The partitions sound kinda OK, but I was planning on keeping the 10Gig blank or trash data. My intent, although I should have made it smaller, like 2gig, was to confuse hackers, which mostly seem to hack Windoze, by looking at the C: drive. If there is nothing there, it may slow them down.
Can I reformat C into
2gig (swap) and
8gig Ubuntu, or does Ubuntu need more?

---

### Post by hugmenot on 2008-03-02
LOL. Seriously?

You can certainly subdivide the 10 gig. If you have 2G of Ram you might not even need a swap partition. If you have 1G another 1 is plenty.
Teh "twice the amount" ruls comes from former times.

---

