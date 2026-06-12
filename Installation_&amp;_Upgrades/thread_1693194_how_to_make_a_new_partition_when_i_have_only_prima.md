---
title: "how to make a new partition when i have only primary partition ?"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by nevinnalwade on 2011-02-22
Hi Guys,

This is Naveen Kumar  From Bangalore,India


Can anybody help me or guide me  on creating a new partition when i have only primary partition on my [COLOR=Red]40gb harddisk[/COLOR].

what i did while installation was selected [COLOR=Red]**use entire partition**[/COLOR] and now i want a additional partition other than primary ? 

I want to assign 10GB for Primary one and wanna create Two 14GB partitions , I Also dont know what Swap partition Is.

Since i am a month old ( January 2011 ! ) UBUNTU user who hates MS Windows now !!! , if i gets this problem solved , i can convince more people to replace their OS to Ubuntu .:D


PLS Some body help me !!!

Thanks in advance !!!

---

### Post by howefield on 2011-02-22
Moved to "*Installation & Upgrades*". You'll most likely get more help here than in Tutorials & Tips.

(Also removed email address).

---

### Post by Mark Phelps on 2011-02-22
To do partitioning, you'll have to be able to boot from a CD -- because when you're using the PC, the parition is mounted and you can't make any changes to it.

Recommend downloading and burning a GParted LiveCD from distrowatch.com.

Once you have that CD, boot from it.

It will launch the Partition Editor (Gparted) which will provide you a graphical app for changing your partitions.

To create new partitions, you must first shrink the current one to make room.  You can do that from the menu in GParted.

You then can create a new partition, one at a time, again using the menu.

Be aware that "Primary" is a type of partition, as opposed to "Logical" -- which is another type.  You can only have four Primary partitions on a single drive.  But you can have as many Logical partitions you want.  Unlike MS Windows, Ubuntu doesn't require Primary partitions.

---

### Post by oldfred on 2011-02-22
Some info to review to help you understand partitions.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)


Swap is a partition ( or file) for memory overflow. If you have lots of RAM swap may not be used much. If lots of RAM then 2GB works. 
But if you want to hibernate, then you need swap at least equal to RAM.  If small amounts of RAM like 512MB then swap should be twice RAM.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

