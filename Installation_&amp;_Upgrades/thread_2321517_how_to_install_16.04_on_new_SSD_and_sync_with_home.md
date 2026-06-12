---
title: "how to install 16.04 on new SSD and sync with /home on HDD"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by mjolnar on 2016-04-22
I am getting a 240GB SSD, I want to only do system and apps on it.  All data files can be held on my 1TB HHD.  What is the best way to sync the SSD with the /home partition?

---

### Post by oldfred on 2016-04-22
I keep /home inside / (root), but mount a data partition at /mnt/data and then link all the standard folders like Documents, Music etc plus others I create back into /home. My data partition is on HDD.

I just reinstalled 16.04 on my SSD, but still have my old working 14.04 install. I keep two main working installs on SSD and usually have another couple test installs on HDD. That is why I use linking as then all installs have same data. Also same Firefox & Thunderbird profiles, but use profile.ini to find profile on HDD.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[URL="http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata"]http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata

[/URL]
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 

[URL="http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata"]
[/URL]

---

