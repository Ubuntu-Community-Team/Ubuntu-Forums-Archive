---
title: "Fresh Install of 13.04 - Questions on Partitions and Mount Points"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by Centropolis on 2013-05-07
I want to install 13.04 on my laptop tonight.  Other than the boot and swap partitions, I want to create another primary partition solely to mount to /home/<myusername>/Documents.
 
I am wondering if I should be created all three partitions using GParted running from LiveDVD first before I actually start the installation process or will I have the option to do all this during the installation process?
 
Also, is mounting /home/<myusername>/Documents to a separate partition a good idea?  I just thought that if I was to try a different distro later, I wouldn’t lose the user files if I saved them all in that directory.

---

### Post by dino99 on 2013-05-07
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by oldfred on 2013-05-08
I use a /mnt/data partition with many folders in it like Music, Documents, Videos etc and link all of them back into /home. I use linking to make folder seem like it is in /home, others use bind.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

---

### Post by vanadium on 2013-05-08
> 
I use a /mnt/data partition with many folders in it like Music, Documents, Videos etc and link all of them back into /home. I use linking to make folder seem like it is in /home, others use bind.

In this respect, there is a huge annoyance now with nautilus 3.6 in the latest ubuntu 13.04. Nautilus follows links more in an "ms windows" way, such that once you navigated the link, the parent folder is the parent folder of the target rather than that of the link. Because of this, you are confined to a "mount bind" to really make it act and look as if the data is right underneath your home folder.

In that respect, the terminal, fortunatelly, still behaves the same way as it always did.

To answer one of the OP's question: yes, you can do any custom partitioning and mounting from within the installation procedure. No need to partition on beforehand with gparted, although you can do that, of course.

---

