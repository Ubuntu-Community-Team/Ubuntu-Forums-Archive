---
title: "Problem with partitions"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by PrvSAT on 2010-01-06
Hello guys,

I am very new to Ubuntu and this forum and hope I will get some advice to my problem:

Installing Ubuntu fresh, using the entire disk, there is no problem.

I have a HTPC with dual core, 2Gb DDR3 and 1.5TB empty disk. I plan to have two partitions on it, one for the operating system (probably around 30Gb max) and the rest, second partition for movie storage.

So after initial installation, I tried to use gparted to create the second partition and I couldn't. By mistake I erased the system partition... :(

Then I started again from unformated disk and during installation I created three partitions, one of 30Gb to monut at "/", second a 5Gb for swap file, and third partition, the remaining space for movie storage with mount point at "/boot"
At 96% of ubuntu installation I got "Executing 'grub-install (hd0)' failed' This is a fatal error"

Could you please help me how to install Ubuntu as described above with two main partitions?
I have done some reading, so what should I use, EXT3 or EXT4 please and where I can select this option during install?

Thank you for reading this message. :)

---

### Post by Cheesemill on 2010-01-06
Don't use /boot as a mount point for user data, this is where Grub gets installed to.
Try using:

30GB - /
2GB - swap
Rest - /mnt/data

---

### Post by eltama on 2010-01-06
I would give:

20GB to /  for the system (it's hard to use 10GB)
3GB  for swap (enough to hold all your memory, but not much more)
rest on /home

that way if you later want to upgrade the system, all your data will be safe in your home directory.

Since you have so much space I would also leave some space to try new versions or other distros, but of course that's up to you.

---

### Post by tachuela on 2010-01-06
+1

---

### Post by Ginsu543 on 2010-01-06
Partitioning schemes depend mostly on how you intend to use your system. If you want to run your computer simply as an HTPC (perhaps as a MythTV or some other media center box) and don't intend to install a lot of application programs on it, then you may not even need 20 GB for the / partition. In most cases IMO, it is preferable to have the / and /home on different partitions. The only question is whether you want to create a third partition for your movies. As eltama suggested above, you could keep all your movies on the /home partition and it will work great. But if it were me, I would set it up as follows:

5 GB swap
20 GB / partition
75 GB /home partition
1.4 TB NTFS partition (for movies)

I prefer to keep my data separate from / and /home so that I don't have to worry about it if and when I want to upgrade the OS. I also like to keep a backup copy of the /home partition on a separate drive (should things go south, this helps speed up the process of getting my system back up and running) and I don't want to have my data files mixed up in that. I like to keep my data files (primarily music, pictures, and movies) on an NTFS partition because then I can access these files in Windows as well as Ubuntu. You may never need Windows access to these files, but I just find this configuration the most flexible.

---

### Post by PrvSAT on 2010-01-06
Thank you all for the great advices that helped me go through!
I will use this system for HTPC, most likely with XBMC so three partitions are good, one for the OS, one for swap and one for storage/movies.
I already installed ubuntu, updated, loaded half of my movies and I am very happy about it.

Long live ubuntu!!!

Now I am in the point of adding a new drive for movies storage too. :popcorn:

---

