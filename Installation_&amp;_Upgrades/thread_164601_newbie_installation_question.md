---
title: "newbie installation question"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by noize on 2006-04-23
i have 2 hds. both 80gb
i want to know how to best partition the drives.
ubuntu will be my primary os, whereas windows will only be used for gaming. 

question: should i be installing ubuntu on my primary hd to increase performance? or just keep it on my 2ndary hd? and how would you partition the drives? 
btw, i'd like to have one fat32 partition to share files between the 2 os.

im new to this, any advise would be greatly appreciated. thnx in advance!

---

### Post by woedend on 2006-04-23
I am not sure about which hard drive to use as which will make a difference speed wise, as I have never done it(but would like to).  
As far as partitioning, on my 120 gig hard drive, when I was sharing files with windows i did
50 or 60 gig fat32 partition
2 gig swap
rest as ext3 for linux

some suggest making a separate /home partition, but I never have liked that idea, and getting it all set back up doesnt take me longer than an hour on a new install.

In my setup, I would keep all mp3's, pictures, documents, videos, deb files or programs I had to download off the internet(for future reinstalls) on my fat32 partition.

If you plan on putting your shared fat32 partition on your ubuntu 80 gig, i'd probably do 40 gig share, 1 gig swap, rest for ext3.

---

### Post by LoclynGrey on 2006-04-23
if both of your 80GB hdds are of equal spec then it doesnt matter which one hosts the primary OS. Or if one hdd has a bigger cache like 8ms / 9ms then go with that as your main drive (master)

I'd set Ubuntu up on the master drive and Windows up on the slave.
With the windows drive I would Partition it to like 20GB NTFS for the OS and then the remainder of the partition for the data (60GB) but in Fat 32.

When you are in your main OS (Ubuntu), mount the Fat 32 partition so that you can access. Obviously you would put shared data onthe Fat 32 partition such as music or docs etc, that way when in Ubuntu or your Windows OS you have access to that data. (You can mount NTFS drives in Linux but its not a goodthing to write to them asit can cause some problems)

To do a dual boot between two drives, you need to modify your grub boot loader settings under your Ubuntu OS. There are plenty of forum posts on how to do that. But here's my windows settings for the grub boot loader, these settings work for me.
:)

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
makeactive

---

### Post by Sef on 2006-04-23
> some suggest making a separate /home partition, but I never have liked that idea, and getting it all set back up doesnt take me longer than an hour on a new install.

I like having a home partition.  If I need to reinstall my os or update it from a clean install, it saves me some work and my hide sometimes.  At times I have tried to do something, but have ended up with part of the system inoperable, so delete and reformat the other partitions, but leave home as is.  So nice not having to reinstall all my files.

---

