---
title: "Split Ubuntu on two drives."
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by elobee on 2010-10-25
How do i install ubuntu so that only the OS itself (hope you get what i mean) is on my C: drive and other files like applications etc is on my D:drive? I use a raptor on 74gb which is faster but smaller than a normal hdd that will also contain windows 7 and crunchbang so I just want the main parts of the OS on that hdd. If it's not possible on install, which maps should be moved from the C: drive to the D: drive if i want all applications and such on the D: drive? And how do i configure so future installations from synaptic or the apt-get command install files on the D: drive?

Thanks.

---

### Post by oldfred on 2010-10-27
Since you are referring to C: & D: are you thinking of wubi. I do not think wubi can be split. 

But if you want full installs you can split just about everything into different partitions, but I do not recommend separating system partitions on a desktop. But the entire system will fit into 10GB, I usually suggest 20GB, but with lots of apps installed I have only used about 6GB. You then can have either /home with your data or a separate /data partition (keeping a small /home inside the system partition). My /home is less than a GB but I aggressively move any hidden folders with data to my data partition. 

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Expanding/Resize an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by elobee on 2010-10-27
> **oldfred said:**
> Since you are referring to C: & D: are you thinking of wubi. I do not think wubi can be split. 

But if you want full installs you can split just about everything into different partitions, but I do not recommend separating system partitions on a desktop. But the entire system will fit into 10GB, I usually suggest 20GB, but with lots of apps installed I have only used about 6GB. You then can have either /home with your data or a separate /data partition (keeping a small /home inside the system partition). My /home is less than a GB but I aggressively move any hidden folders with data to my data partition. 

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Expanding/Resize an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

No I'm not installing from wubi (that ubuntu installer for windows thingy?), I don't even have windows at the moment. Referring to C: and D: when talking about drives but i guess it might have been alittle confusing with the information i gave.

**To clarify:** I have two HDD's, one is a 74GB Raptor and the other a normal 1TB drive. Can I in some way get all applications i install and all data for those stored on my 1TB drive automatically? Basically I want to have my /home and all applications and their data on my 1TB drive instead of the 74GB drive, I only want almost the pure OS on the 74GB drive.

I just have 41.2 GB free space on the 75GB drive right now so keeping it this way is not really an alternative.

---

### Post by oldfred on 2010-10-27
Applications do not take much space, as I mentioned I have lots of applications  and have used only 6GB. If you write a DVD tmp may want another 4GB, so you can get by with 10GB (I still like more) for the system. Then /home and/or /data has all your data and user settings. Just put /home and /data into the 1GB drive. If dual booting you may also want to add to the 1GB drive a shared NTFS partition for windows data which also can be read from Ubuntu. It is better not to write into the windows system partition. You can read the windows system partition, but writing can sometimes cause problems.

---

### Post by akand074 on 2010-10-27
> **elobee said:**
> No I'm not installing from wubi (that ubuntu installer for windows thingy?), I don't even have windows at the moment. Referring to C: and D: when talking about drives but i guess it might have been alittle confusing with the information i gave.

**To clarify:** I have two HDD's, one is a 74GB Raptor and the other a normal 1TB drive. Can I in some way get all applications i install and all data for those stored on my 1TB drive automatically? Basically I want to have my /home and all applications and their data on my 1TB drive instead of the 74GB drive, I only want almost the pure OS on the 74GB drive.

I just have 41.2 GB free space on the 75GB drive right now so keeping it this way is not really an alternative.

You have two hard drives, you want the OS on your Raptor, and everything else/data/config on your TB hard drive right?

- Put in the Ubuntu CD to install it, select "manual install"
- Your Raptor/1TB will be named one sda, one sdb, depending on which one you ran first, you can tell which is which by the size
- Set your entire Raptor as EXT4, and leave a bit of it for swap equal to the amount of RAM you have (optional, but I recommend that on your Raptor)
- Put the mount point for the big partition of your Raptor as "/"
- Now take your entire 1TB hard drive, set it as EXT4 with mount point "/home"

Now all your data/config files will automatically be stored on your TB hard drive, and just the OS will be installed on your Raptor. If your really want everything on your TB but your plain OS (I don't recommend it), you could make partitions for mount points "/usr", "/var", "/boot", "/etc" etc. on your TB but honestly they take up so little space and they will run faster on the Raptor that it would be smarter to just leave it with just the /home on your TB.

Hope that helps if thats what you meant.

---

