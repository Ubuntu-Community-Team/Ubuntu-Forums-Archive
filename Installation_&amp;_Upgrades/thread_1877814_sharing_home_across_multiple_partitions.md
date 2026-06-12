---
title: "sharing /home across multiple partitions"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by eweber on 2011-11-08
Hello,

Disclaimer:  new to Linux, sorry if its a dumb question.

I was going to install Ubuntu 11.10 server onto 3 hdd's in the following configuration...

HDD #1 - 32GB
/root
/boot
/swap

HDD #2 & HDD #3 - 1TB, RAID 0
/home (documents, pictures, music, movies)

But then I thought (always a scary proposition) that my small files (documents and pictures) don't really need the benefit of RAID 0.  So maybe the following configuration would work better...

HDD #1 - 32GB
/root
/boot
/swap

HDD #2 & HDD #3 - 1TB, RAID 0
/home (music, movies)

HDD #4 - 200GB
/home (documents, pictures)

Questions:

1)  is it possible to have 2 home directories spread over 2 partitions?
2)  is yes, then how would i specify which home directory I'm using?
3)  which home directory would contain my .profile file?
4)  from everything i've read, /home is the (only?) place for all personal files.  Is this true?  If it's not true, then I could put /home on the RAID partition, and then /media on HDD #4.  Is there some reason that all personal files need to be in /home?

thanks in advance for your feedback!

eric

---

### Post by eweber on 2011-11-08
Just spoke to someone here at work.  Sounds like there's nothing special about /home.  I could probably do something like this...

HDD #1 - 32GB
/root
/boot
/swap
/home/eric

HDD #2 & HDD #3 - 1TB, RAID 0
/music
/movies

HDD #4 - 200GB
/documents
/pictures

any thoughts to the contrary, please let me know.

---

### Post by oldfred on 2011-11-09
If you / (root) is not in the RAID, you probably do not need a separate /boot. Servers often need a separate /boot just to have it outside the RAID or LVM or other special configurations.

I use data partitions as I have multiple installs in my desktop. Since I used to dual boot with XP(still use it very occassionly), have data in both NTFS and ext3 partitions. I mount those in every install and link folders into /home.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

