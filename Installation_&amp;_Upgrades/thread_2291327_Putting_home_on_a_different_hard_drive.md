---
title: "Putting /home on a different hard drive?"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by andrew251 on 2015-08-19
Hey guys, I'm considering moving my main desktop onto Ubuntu like my laptop.
It has two drives. One is a 250GB Samsung SSD and the other is a 3TB HDD.
What I want to know is should I put swap and / (root) onto the SSD and put /home onto the HDD.
Because a 200GB+ root does seem pretty big, and also what is stored on root and what is stored in home? Where does Steam (and Steam when using Wine) store my games?
What would be the best way of doing this?
Thank you, Andrew

---

### Post by apmcd47 on 2015-08-19
Root will contain your system filestore while /home will contain your user filestore, including all your pictures, work files, etc.

I don't know steam, but it will probably be in /home, under your account. I imagine your SSD will be a lot faster than your HDD, so I would be asking how much  filestore do you really need, and will you notice the difference in performance of the two disks?

I might be inclined to use the SSD for root and home (separate partitions of course) while partitioning the HDD into a backup area and a place to keep other files, such as media files. If you decide you want to use the 3TB disk for your home directory I would suggest multiple 50GB partitions on the SDD to allow re-installing Ubuntu on fresh partitions (ie for testing a new Ubuntu or other Linux before moving over). Fresh installs are always cleaner than upgrades. Plus you could immediately install a second, emergency repair, root partition, in case you screw the initial installation.

I hope this helps.

Andrew

---

### Post by Bucky Ball on 2015-08-19
> **andrew251 said:**
> 
What I want to know is should I put swap and / (root) onto the SSD and put /home onto the HDD.

Yes. :)

I would put the /swap on there, too. When you get to the install section, choose 'Something Else' and manually create the partitions /, /home and /swap and put them where you like. Those mountpoints you will find as defaults so you just need to select them when creating the partitions (EXT4 and swapspace). You really only need about 20Gb / partition if you are running with a separate /home.

There are options. Creating a /home partitions means your user settings will be on the HDD. I have numerous installs so I have the /home partition default to /, then delete the /Documents, /Videos, etc. folders in /home and create symlinks to a large /data partition which has /Documents, /Videos, etc. folders. That way all the installs access the same data but have their own settings still on /. You have the perfect setup to do the same but better. Your installs are on the SSD and your /data would be on the HDD. 

To backup just your personal data you would backup the SSD. To clone your install for backup you would backup the SSD. :)

Good luck and let us know how you go.

---

### Post by dino99 on 2015-08-19
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

usually / (root) is about 20 Gb and store the OS packages
/home is where your find all your settings/data . So Steam will use it; think to drop /home on the ssd, and swap too (if you have a large amonut of ram, then swap is not that usefull; many users dont set one)

---

### Post by oldfred on 2015-08-19
My SSD is only 128GB and I wonder what to do with all that. 
I normally use 25GB for / and include /home inside /. But my /home is 2GB because of .wine and Picasa. If your games also use .wine then a bigger / or /home may be needed.
But keep both / & /home on SSD, but link all other data from hard drive data partition.

I left room on SSD for another / or two so I could experiment or test another install. Then on hard drive I have a partition for many ISO so I can boot them directly from grub, backup of data from /home and other partitions as well as a large /mnt/data partition.
Installing to SSD from ISO on fast hard drive booted directly with grub is very fast. 

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

