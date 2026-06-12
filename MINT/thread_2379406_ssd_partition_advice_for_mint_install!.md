---
title: "ssd partition advice for mint install!"
date: 2017-12-05
forum: MINT
---

### Post by kim3 on 2017-12-05
Hi folks,

I am keen to install Mint on my SSD which i formerly used for Windows System files and applications.

I have connected -

dev/sda
   dev/sda1 104mb
    dev sda2 127453
    dev sda 3 471

dev/sdb
 dev/sedb1 10000102mb

I save all my documents and videos and data to the other drive.

Want the SSD just for system/ applications/ maybe the swap ? (which I believe is like page file?)

There is 8gb ram and an i5 quad core 3.2ghz processor...its a few years old, but still going!

I just seek advice on how to partition the SSD?

My 'home' is essentially already set up with sdb which is half full of data so I do not wish to rename or repartition it.

Kindly advise!

Cheers,

---

### Post by howefield on 2017-12-05
Thread moved to the "*MINT*" forum.

---

### Post by oldfred on 2017-12-05
What is format of sdb1?
Better not to use NTFS, unless you have Windows or at least the Windows repair disk. It will need chkdsk or other repairs that you cannot do from Linux.

I typically have several / (root) partitions on my SSD and more on HDD. I prefer to have at least one install on every drive, even if just for emergency boot and not otherwise planned to be used.

You can keep /home inside / (root), but then link all the folders in your data partition back into /home. I use that configuration as then each of my installs can use same data, but have different settings in /home.

Still pretty current, other than actual installs have been updated & partitions relabeled:
 Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 

      
 The actual user settings are small. My /home is 2GB with most of that as .wine' Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home in my typical 25GB / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

