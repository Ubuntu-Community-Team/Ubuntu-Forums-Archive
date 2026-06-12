---
title: "ubuntu, ubuntu /home partitions"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by Shakey Hands on 2012-07-06
i want to make a separate partition for my /home. ive read its a good idea, as it allows system upgrades or re-installs without deleting your preferences, music etc.

i Couldnt find anything in the forums or help.ubuntu etc. :-k

i have 90ish gig of data on my HDD which i would like to keep. i asume i would be needed to copy this across to the new partition somehow? etherway the important stuff is backed up so if it all must be wiped in the process so be it.

Thanks

---

### Post by Bucky Ball on 2012-07-06
> **Shakey Hands said:**
> 

i Couldnt find anything in the forums or help.ubuntu etc. :-k



They are only two options. Try a general search:

[http://au.search.yahoo.com/search?p=create%20home%20partition%20ubuntu&fr=altavista&fr2=sfp](http://au.search.yahoo.com/search?p=create%20home%20partition%20ubuntu&fr=altavista&fr2=sfp)

Good luck ... ;)

---

### Post by oldfred on 2012-07-06
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


I still recommend a separate /home for most users, but have converted to moving data, but not the /home to separate data partitions. That is primarily because I do clean installs to a new partition and still have old one working. I only then copy some of the settings in /home over to the new install. My /home is between 1 & 2GB with most of that .wine for Picasa.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6 (older read only post)
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Bucky Ball on 2012-07-06
Similar to oldfred, I have 10.04, 10.10 and 11.04 installed on separate partitions and all using the same /home partition (which has three separate user directories, one for each install). I was using 10.10 until end-of-life then swapped to 10.04. The folders in the 10.04 user directory in /home are symlinks to the existing ones in the 10.10 user! ;)

I'm presuming, oldfred, you have the user directories for each install as symlinks to one set of 'actual' directories on a separate partition?

@Shakey Hands: If you're not too far down the track configuring your install it might be just as easy to re-install and set things up exactly as you want them re. /home partition and anything else now that you've looked around a bit. You could, though, simply put all your personal data from the /home directory on a separate partition, delete the directories in your /home directory and create symlinks to the real directories on your separate data partition, if you follow me. Creating the links is a cinch. :)

---

### Post by oldfred on 2012-07-07
Slightly different but there are many ways to do it.

I do not use the same /home but use /mnt/data for Linux data in a ext3 partition and /mnt/shared for data in a NTFS partition. 

I then use symlinks to link all the folders like Music, Documents etc that are just data back into each /home. Even some hidden folders with lots of data get moved to the data partition like Firefox & Thunderbird profiles. I then use profiles in XP and every Linux I boot.

---

### Post by Shakey Hands on 2012-07-07
thx for all the info. 

tomorrow will be the next chance i can delve into all this, however i will quickly add to the thread my 'grand plan', if anyone wants to give me more advise?

A windows partition (it wont need to be too big, for my purposes), and a ubuntu partition (which will be my primary OS). but as i stated above i got the idea of a third small partition for a purely Ubuntu OS files purpose. that would only be large enough for the OS itself.

Im a newbie, so i have very little idea as to what HDD overall organisation designs work/dont work, so anymore idea/ advise as to HOW i can actually do this or anything better (im talking nitty gritty eg. any all terminal commands) i love input. 
ill be reading this tomorrow morn, once again thx for everything so far.

---

### Post by Bucky Ball on 2012-07-07
Put simply, for what you are suggesting with a separate /home, you would want three partitions something like this:

/ = root; this is what you are imaging to be 'a third small partition'. This *is* where the OS lives and you don't need more than about 15Gb (less or more depending on your purpose and flavour). Apps and the OS go here. You could add a separate /boot partition I guess. 
/home = your personal stuff, documents, vids, music, etc. Big as you like.
/swap = swap. 2Gb fine.

All these partition mountpoint names are there as defaults when you choose 'Something Else' at the partitioning section of the install and partition manually.

Point to remember is that you can only have four primary partitions on one drive so make an extended partition - into which you can, theoretically, put as many logical drives as your comp can handle - and put the three Buntu partitions in there. Ubuntu fine in a virtual partition inside an extended. Win not.

Example: Win on first partition (primary); extended partition with the free space on rest of drive and three Buntu partitions in there. Good luck. ;)

PS: No terminal input required for this. All done during the partitioning section of the install.

---

