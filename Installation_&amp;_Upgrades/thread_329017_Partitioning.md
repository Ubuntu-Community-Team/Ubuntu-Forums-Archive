---
title: "Partitioning"
date: 2006-12-31
forum: Installation &amp; Upgrades
---

### Post by sir_lazer on 2006-12-31
Does repartitioning a HD delete all the files on that HD?:confused:

---

### Post by Bartender on 2006-12-31
No, not necessarily.  The term does get used a little loosely, but generally speaking you can create a partition on a HDD without losing data.

However, the devil's in the details.  

My favorite partitioner is [GParted]("http://gparted.sourceforge.net/livecd.php")LiveCD.  You download the latest .iso and burn it to a CD like you would a Linux distro.  Boot from the CD.  Works great.  There are screenshots at the GParted home page, and even a forum!

---

### Post by sir_lazer on 2006-12-31
Is GParted the same partitioner used on Ubuntu?

---

### Post by NeoLithium on 2006-12-31
Yes, I believe it is.

---

### Post by Bartender on 2006-12-31
From what I've been able to figure out, the GParted Live CD (GPLCD) is the "everything but the kitchen sink" version of the stripped version on the Ubuntu LiveCD (ULCD).

I'm not sure why it is, but the stand-alone GPLCD just seems to work better than the partitioner on the Ubuntu CD.  Some people have said it has something to do with partitions already mounted by the time you get to the partitioning step.  I honestly don't know.

All I know is for me, it's less scary to do the partitioning first with the GPLCD, then toss in the Ubuntu CD and go for the "manually partition" option.  It's reassuring when you get to the partitioning map and the Ubuntu CD shows the same thing you saw in GPLCD.

---

### Post by sir_lazer on 2006-12-31
How long does GParted take to finish partitioning? (One task)

---

### Post by NeoLithium on 2006-12-31
It generally depends on the partition size, and the tasks required, formatting the information, etc; but I've found it to work rather quick

---

### Post by Bartender on 2006-12-31
I was just partitioning a 120GB Seagate with GPLCD on an old PIII 450MHz PC a coupla days ago.  Formatting about 55 GB as ext3 took four or five minutes.  Formatting the swap only took a few seconds.  I turned away to write down a couple of notes, and it was done before I looked back.

It only took a second or two to create the extended partition. 

Of course, all of that would go quicker with a faster CPU.

---

### Post by sir_lazer on 2006-12-31
Thanks, ppl! I've just partitioned my 80 GB drive, worked perfectly.[:-D] Now I'm just defragmenting (C:); after that, Ubuntu Installation.

---

### Post by Bartender on 2006-12-31
Generally, you defrag *before* partitioning :)  to get that pesky Windows data shoved to the left but if you're doing OK so far that's good!

---

### Post by sir_lazer on 2006-12-31
Status Update: Ubuntu installed, with a 20 GB partition and a 55 GB partiton for windows. Seems fine, so far so good!:-D

---

### Post by Bartender on 2007-01-01
Congratulations, sir lazer, I raise a flask of grog to thee  :D

---

