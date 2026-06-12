---
title: "Gamer wondering how to partition drives for a dual-boot"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by Mr. Icarus on 2011-08-09
I've been using ubuntu exclusively on my two laptops lately, for coding and all of my other work.  I plan on installing it onto my desktop now for work as well, but I would like to retain Windows 7 so I don't have to worry about compatibility for all of the games I love to play.  My question is this:

When setting up my partitions, how much space (and what format) should I set aside for windows to write and read games from?  I have a 500GB hard drive currently, and was planning the partitions as:

1. Windows 7 (NTFS, setup with Windows installer) ~20 GB
2. File Storage (NTFS, set up with the Ubuntu install partitioner) ~452 GB
3. Ubuntu (EXT3, set up with Ubuntu install partitioner) ~ 20 GB
4. Swap (~2x the size of my RAM) ~ 8GB

The plan is to have Windows install and execute games from the NTFS File Storage partition, while being able to access  the same partition from Ubuntu for my documents, code files, music, etc.

I don't know if this would work, and I'm also not sure what my file system will be like (windows or linux-y?) if it did.  Will this work?  Or is there a more elegant solution?

---

### Post by Basher101 on 2011-08-09
do NOT give windwos 7 20 GB. Its by far not enough! I made the EXACT same partition setup: 
Win 7 (30gb)
ubuntu 11.04 (15 gb)
shared storage (545 gb)
and swap (4gb)

my hdd is total 640 gb big (but only uses 598 in binary calculation). I made a fresh install on windows, updated to SP1, and the other updates. Now Windows only leaves me 5 gb left on the partition (it uses 25 gb total with updates and some basic programs like adobe reader, MS office 2010, antivirus, opera). Give windows more air.

---

### Post by oldfred on 2011-08-09
Welcome to the forums.

I thought XP needed 20GB & Vista/7 needed 30GB as a minimum size. But NTFS needs 30% free to work well and windows makes it difficult to install progarms in the d: drive. I might make it 50GB or more.

I normally suggest / (root) for Ubuntu to be 10-20GB when you have a separate /home or are storing all data elsewhere so 20GB should be good. 

Swap only needs to be the same as RAM in GiB or slightly larger that GB,  if you want to hibernate and with dual booting I do not suggest hibernating as many users corrupt a system by modifying a file from the other system when the first is hibernated.

---

### Post by Mr. Icarus on 2011-08-09
Thanks for the heads up.  Do you happen to know if the games would have to be installed on the windows partition?  Or if all game applications can be installed on the shared partition?  The reason I ask is since you mentioned you used the win partition for office, adobe reader, etc. Do applications utilized by each OS have to be stored within that partition?

---

### Post by Basher101 on 2011-08-09
Not necessariley, but i installed them to the win7 partition becuz i made a backup of it after i configured and updated everything. I simply wanted to save time reinstalling all that crap again if my windows gets corrupted. All games are installed to the shared partition. I must try once to make a fresh install and see if the games still work (even without the registry keys).

---

### Post by Mr. Icarus on 2011-08-09
I'm going to give it a shot and see what happens, thanks to both you guys!

---

### Post by Basher101 on 2011-08-09
Mark the thread as [SOLVED] if it works for you. Otherwise post another question if something doesn't work. Always glad to help

---

### Post by Mark Phelps on 2011-08-11
If your goal of installing MS Windows games to a shared NTFS partition is to minimize the space demands on your Win7 OS partition, then that's a good thing.

But, if your goal of that is because you intend to run the SAME games both from MS Windows and from Ubuntu (using Wine or one of its derivatives), that is most probably NOT going to work.  I believe you have to actually install the game using Wine to run it in Ubuntu.

But ... I could be wrong -- seeing as how I found Wine to be a complete waste of time and do not use it.

---

