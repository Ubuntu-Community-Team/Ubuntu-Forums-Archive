---
title: "Partition editing"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-12-19
Hello; I have done some editing to my partition table and now have this; screenshot.
   There is currently nothing installed on,/dev/sda7, i was thinking of using this  for a
separate home partition.  Would appreciate some instruction on this.
 Regarding the unallocated space, my thinking here was to use this space to install other
distro's i wanted to try,specifically Sabayon X/KDE.  I thought by keeping this separate
from the other, a later uninstall might be easier?
    I realize i will have to create a partition in this space, and apparently it will be primary
as that appears to be the only option available from gparted.

Or would it be better to expand my extended partition and create another logical
one within it?
All advice welcome.

---

### Post by oldfred on 2012-12-20
Since you want to experiment, I would extend the extended partition to include all of the unallocated. then you can create as many logical partitions as you want.  

I normally suggest a separate /home, but if multi-booting you may prefer a separate data partition that may work with other distributions. The only issue with other non-Debian distributions is UID & GIDs may be different and have to be reset to allow sharing data.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

    
       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by offgridguy on 2012-12-20
Thanks for the reply ,oldfred.  I will go the route you suggested and extend the
extended partition.  Experimenting is helping me to learn.
I should add i get a lot of help reading other threads regarding partitioning.

---

