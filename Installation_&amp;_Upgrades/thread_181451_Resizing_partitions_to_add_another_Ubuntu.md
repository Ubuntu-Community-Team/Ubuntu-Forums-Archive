---
title: "Resizing partitions to add another Ubuntu"
date: 2006-05-24
forum: Installation &amp; Upgrades
---

### Post by markr on 2006-05-24
Hi,

I am looking to have WinXP, Dapper and Dapper+1 on my HDD, reason is that Dapper will be my stable environment,  but I can't wait to start playing with Dapper + 1, hence the need for another partition to install it onto (so I don't break my production system!)

Here is what I have:

NTFS (WinXP) - 10 gb
EXT3 (Data, Music etc) - 30gb
EXT3 (Dapper / incl home directory) - 10gb
SWAP Partition - 1gb 

What I would like to do is:

NTFS (WinXP) - 10 gb
EXT3 (Data, Music etc) - 30gb
EXT3 (Dapper / incl home directory) - 5gb
EXT3 (Dapper + 1 / incl seperate home directory) - 5gb
SWAP Partition - 1gb 

All my user data is on the 30gb shared partition so I can share between the two installs of Ubuntu.

Is this possible without reinstalling (i.e. deleting Dapper / and the swap)?

Thanks

Mark.

---

### Post by ssalman on 2006-05-24
Yes it is possible, but you need to resize your Ubuntu partition to 5 GB, and then create another 5 GB partition, you can do that with QTparted or with Gparted among other options, the trick is that you need to make sure you are not booting using that hard drive, i.e. boot using a live CD with one of the above applications, I think gparted is included in the Ubuntu live CD, but I'm not sure. I always use the System Rescue CD found [here]("http://www.sysresccd.org/Main_Page"). hope this helps.

---

