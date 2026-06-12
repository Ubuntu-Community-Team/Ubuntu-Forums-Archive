---
title: "Installing Ubuntu on a 500 GB Samsung 960 EVO"
date: 2017-07-08
forum: Installation &amp; Upgrades
---

### Post by eera5607 on 2017-07-08
Hello everyone! I'm trying to understand the best way to install Ubuntu on a brand new  Samsung 960 EVO SSD with 500 GB of total capacity. I also have a 1 TB Barracuda (7200 RPM). The first option that I had was to install Ubuntu the easy way (not manual partitioning) and save all my files into the SSD and use the HDD as a backup drive. Then I read that leaving free space on the SSD would contribute to a longer lifespan. After that I also noticed that it was not necessary to save all my music, videos and documents on the SSD and maybe leave some space unallocated also. I decided to do manual partitioning instead but I have 3 questions.

1. The disk has never been used. Do I need to create an EFI partition? (I'm installing on UEFI mode)
2. Do I need to create a swap partition? (My system has 32 GB RAM and I never hibernate it). 
3. Final and most important question. What is better?: 1. Using the installation wizard to mount all  /home on the HDD and not the SSD (meaning that** all config** files will be on the HDD) to save space in the SSD (creating a 250 GB for / on the SSD and leaving the rest unallocated)  or 2. From the installation wizard install all the system (/) including /home on a 250 GB partition on the SSD and then mount the HDD (using fstab) permanently and automatically at startup on /media/hdd/ (for example) and the change only the Downloads, Music, Videos and Documents (maybe other folders) path editing ~/.config/user-dirs.dirs to the HDD leaving **ALL** config files on the SSD for a faster access and big files on the HDD. 

Thank you very much for your help.

---

### Post by ubfan1 on 2017-07-08
1. Yes put an EFI partition on the SSD -- that will speed up the booting if used as the boot device.
2. Depends upon the workload, if you never see swap in use, then don't bother with swap on the SSD.
3. Config files on the SSD is best for performance.  Maybe two 50G partitions for roots (so you try a new one
before committing to it), a data partition for fast access, and links for Documents, Downloads, (var?) to a location on the hard disk.  There are lots of recommendations for disk partitioning, pick       the one that best meets your needs.

---

### Post by eera5607 on 2017-07-08
> **ubfan1 said:**
> 3. Config files on the SSD is best for performance.  Maybe two 50G partitions for roots (so you try a new one
before committing to it), a data partition for fast access, and links for Documents, Downloads, (var?) to a location on the hard disk.  There are lots of recommendations for disk partitioning, pick       the one that best meets your needs.
Thank you very much. That is a good idea, to create two boot partitions, I will definitely do that. I will also create the data partition for faster access and then create the symbolic links to the folders with bigger files leaving the config files on the SSD (not sure if this can be done from the installation wizard, I mean mounting specific folders like Downloads since the beginning). I will also consider mounting var on the HDD (are log files bad for the SSD?). Thanks again.

---

### Post by efflandt on 2017-07-09
I am not sure if unallocated space is rotated in for wear leveling. The main thing is to avoid totally filling up partitions on an SSD that are used frequently. There is a cron.weekly that does fstrim to clear blocks from deleted files for fastest write, but some people move that fstrim script to cron.daily.

I do not hibernate, so I did not use swap when I had 8 GB RAM and now have 16 GB (a vast majority is used for drive cache). The noatime mount option avoids writing to the SSD every time you access a file. And I use tmpfs (RAM) for /tmp, since contents of /tmp is erased every boot. So this is my /etc/fstab for a legacy BIOS system (pre-UEFI).```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=6787eaaf-0994-4467-897b-538f5c624731 /               ext4    noatime,errors=remount-ro 0       1
tmpfs /tmp tmpfs noatime,nosuid 0 0
```Actually I am not sure why the noatime is in the tmpfs line, but I guess it makes no difference. A live/install fstab shows an example of using tmpfs.

---

### Post by oldfred on 2017-07-09
I have several / (root) partitions on my SSD and include /home in /. But all data including some of the normally hidden folders like the Firefox & Thunderbird profiles are also on my data partition. (may make Firefox a bit slower). My original SSD was only 60GB and with 2 / partitions did not have much room. Still do that although now my newer SSD has more space. And I regularly houseclean profiles to keep them smaller.

       The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

One example of SSD & HDD partitioning. I only use gpt as a bit more reliable. 
Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 

      [http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by eera5607 on 2017-07-10
> **efflandt said:**
> I am not sure if unallocated space is rotated in for wear leveling. The main thing is to avoid totally filling up partitions on an SSD that are used frequently. There is a cron.weekly that does fstrim to clear blocks from deleted files for fastest write, but some people move that fstrim script to cron.daily.

I do not hibernate, so I did not use swap when I had 8 GB RAM and now have 16 GB (a vast majority is used for drive cache). The noatime mount option avoids writing to the SSD every time you access a file. And I use tmpfs (RAM) for /tmp, since contents of /tmp is erased every boot. So this is my /etc/fstab for a legacy BIOS system (pre-UEFI).```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=6787eaaf-0994-4467-897b-538f5c624731 /               ext4    noatime,errors=remount-ro 0       1
tmpfs /tmp tmpfs noatime,nosuid 0 0
``` Actually I am not sure why the noatime is in the tmpfs line, but I guess it makes no difference. A live/install fstab shows an example of using tmpfs.

Thanks! but with only adding that line to fstab are you storing the /var contents on RAM? There's no need to do anything else? 

> **oldfred said:**
> I have several / (root) partitions on my SSD and include /home in /. But all data including some of the normally hidden folders like the Firefox & Thunderbird profiles are also on my data partition. (may make Firefox a bit slower). My original SSD was only 60GB and with 2 / partitions did not have much room. Still do that although now my newer SSD has more space. And I regularly houseclean profiles to keep them smaller.

       The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 


Thanks! Is there a reason to mount the data partition on /mnt and not on /media for example? How do you mount specific config folders like .thunderbird or .steam or .cache (it includes several gigabytes of Spotify cache data). I was thinking in also changing that files to the HDD. NOTE:  As I was writing this post I checked and Spotify, Steam, Dropbox and Thunderbird (Local Folder) let you change the local folder path (from GUI) to any partition mounted on the system so, in those 3 cases is very easy. That's like 40-50 gigabytes of data in my system that can be easily moved to the HDD. Is that in some way over complicating everything and being a little bit paranoid as the majority of SSDs nowadays will have a long life on normal use?

---

### Post by oldfred on 2017-07-10
It may be over complicating things as SSD life is much better.
But I have a smaller SSD & large HDD. And I like to have multiple installs. Just to test next version or experiment with different configuration. I have at least one install on HDD also. 

For Firefox & Thunderbird, I just edit profile.ini. I then copy to my other system in Ill or in Fla, so I have same data where ever I am.

---

