---
title: "Extend my ubuntu partition"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by dsub42 on 2010-08-02
Hi ,, please could someone help me, 

im new to linux... 

I have a disk partitioned, with windows on on one partition, ubuntu appears to be installed on an extended partition ... and iv run out of space... i need to extend the partition that ubuntu is installed on by 40gb

Iv been trying and asking on here for 2 days but have got no closer... 

I have tried downloading gparted... burning it to a cd and then booting from the cd .. but i get upto a message that says use at your own risk then my system just reboots ....

some one please help me, i just wank some more space as iv got a gig left and need another 40 .... how can i extend my ubuntu partiton ,,,, anyone? ... anyone atall?

---

### Post by dsub42 on 2010-08-02
I have finally got the cd to boot ... but how do i go about extending the partition....

it says there is no room for me to extend,  (i have free space)

please see the screen shots below:
[URL="http://s881.photobucket.com/albums/ac17/dsub42/?action=view&current=Screenshot-500GBHardDiskATASAMSUNGHD501LJ-dev-sdaDiskUtility.png"]http://s881.photobucket.com/albums/a...mMonitor-1.png

http://s881.photobucket.com/albums/a...iskUtility.png[/URL]

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

Since you have a dual boot system with Windows, you can boot to Windows & download Easeus Partition Master for free. You can use that to resize, create, delete, clone, and otherwise manipulate partitions.

[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

I am new to Ubuntu/Linux and am not familiar with G-Parted, sorry.

Alternately, you can save data files on a separate partition or even your Windows partition. Only use Ubuntu partition for the OS and installed packages.
 
Hope this helps!

---

### Post by dsub42 on 2010-08-02
I would not need to extend the partition if i knew where all my space had gone? :)

iv no idea how the ubuntu partition has gone ,,, is it possible that files that are removed from my tmp folder are being held somewhere?

where is the recycle bin equivelant in ubuntu?

---

### Post by Kakers on 2010-08-02
Ok so it looks like you have 3 partitions on your drive, here is from what I understand.

/dev/sda1 - media (Storage?)
/dev/sda2 - media (Storage?)
/dev/sda5 - ext4 - Linux 97%

When using the gparted program are you simple trying to extend the sda5 (ext4) partition without doing anything else?

As you will need to first reduce the size of one of the other partitions, most likely going to be sda1. As this space is allocated to this partition it can not be moved to another without first being unallocated.

Reduce the size of either sda1 or sda2, apply the changes and then this space should be listed as unallocated. Then increase the space on the sda5 drive and apply again. Unfortunately resizing partitions after data has already been put on there carries a small risk, I have not encountered it myself but be careful. :o

If you have already tried the above please let me know. As a side note by default on a Ubuntu installation the recycle bin is accessible at the bottom right of the screen.

---

### Post by dacman48 on 2010-08-02
partition magic, while good, sucks. is there a partition table already in the "free" space? if so , delete it

---

### Post by oldfred on 2010-08-02
More info on using gparted:

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Because of the way you have partitioned it will be difficult to move/expand your root. Have you thought about making the free space plus some of the available space if you shrink sda1 into a new partition and move either /home or all your data to that partition. IF you do not have /home in your root install root can be fine with 10-20GB.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by dsub42 on 2010-08-02
i have shrunk the size of sda1 so now there is about 80gb of unallocated space ....

but i still cant extend sda5 ....

any ideas?

---

### Post by oldfred on 2010-08-02
If you really want to expand sda5, you will also have to move sda2 all the way left. Plan on overnight as it will take many hours to copy & verify each sector. Then you will have to expand the extended partition into the free space. Then you can move sda5 left, plan on another overnight.

Do all of this one step at a time. Use check to run command from panel at top as nothing is done until you tell it. I still think a separate /home would be easier.

---

