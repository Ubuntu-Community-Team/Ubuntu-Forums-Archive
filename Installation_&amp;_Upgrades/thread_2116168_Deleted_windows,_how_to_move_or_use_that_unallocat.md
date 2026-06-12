---
title: "Deleted windows, how to move or use that unallocated space in my ubuntu"
date: 2013-02-15
forum: Installation &amp; Upgrades
---

### Post by macishayne on 2013-02-15
Hi, I installed Ubuntu, and moved all my windows pictures and  files to my ubuntu space. I removed windows, but now I want to make  ubuntu my primary. It still has 500gb of unallocated space from where my  windows was, and I want to use that space to extend my ubuntu space.

---

### Post by ali abry on 2013-02-15
you can't do it because your unallocated space is out of your extended space.

its not good to give the hole hard drive to Ubuntu be cause next time you want to install Ubuntu and if installation cause formatting the partition you get in trouble of loosing data because of reformatting. 
theres some options that might help like moving your entire home directory to that unallocated space .

---

### Post by macishayne on 2013-02-15
> **ali abry said:**
> you can't do it because your unallocated space is out of your extended space.

its not good to give the hole hard drive to Ubuntu be cause next time you want to install Ubuntu and if installation cause formatting the partition you get in trouble of loosing data because of reformatting. 
theres some options that might help like moving your entire home directory to that unallocated space .


How do I move it?

---

### Post by slickymaster on 2013-02-15
I'm assuming that you have a dual boot windows-ubuntu computer and your ubuntu installation is posterior to the windows one, which causes the windows partition to be on the left of ubuntu partitions.

Personally, I am not a fan of resizing left or moving partitions unless you have to, but if you really want to do it, you will have to resize partitions from a liveCD, and right click on swap -> swap off, as you cannot work with mounted partitions.

If you decide to move partition left and expand right, I strongly advise you to do a full backup of all your important data before doing it.

Moving partitions can take a while depending on how full they are.

---

### Post by schragge on 2013-02-15
[post]12510349[/post]

---

### Post by oldfred on 2013-02-15
+1 on slickymaster suggestions.

I also do not like moving left, but if you really want to you can. It just is somewhat higher risk as any power failure orinterruption in the middle corrupts system.

I might consider full new install. Then you can repartition as you desire. Full backup required regardless of what you choose.

Or just make the space a data partition. My normal suggestion is smaller / (root) of 10 to 25GB and separate /home or what I use which is separate /mnt/data partition and link folders from the data partition back into /home so system looks just like one larger system.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by slickymaster on 2013-02-15
> **oldfred said:**
> I also do not like moving left, but if you really want to you can. It just is somewhat higher risk as any power failure or interruption in the middle corrupts system.

I might consider full new install. Then you can repartition as you desire. Full backup required regardless of what you choose.

Precisely.

I strongly recommend you, macishayne, to consider oldfred's advice.

> **oldfred said:**
> Or just make the space a data partition. My normal suggestion is smaller / (root) of 10 to 25GB and separate /home or what I use which is separate /mnt/data partition and link folders from the data partition back into /home so system looks just like one larger system.

Without intending to depreciate this approach, nor to question its merits (which are immense), I do not advise it so much due to the fact that it requires a certain degree of expertise.

P.S.: After reading my last sentence I realize that it may be misread as arrogance. I apologize for that, even though that was not my intention.

---

### Post by oldfred on 2013-02-15
No slickymaster you are correct.

I often suggest the separate /home and the instructions on moving it are straight forward but a lot of command from terminal. On a new install it is easier, but you still have to do manual partitioning. And not everyone understands partitions.

The separate data partition is a lot more complex and requires mounting partitions  in fstab with proper ownership & permissions. Then creating folders in the partition and creating links. Not really for a new user.

---

### Post by macishayne on 2013-02-16
> **oldfred said:**
> No slickymaster you are correct.

I often suggest the separate /home and the instructions on moving it are straight forward but a lot of command from terminal. On a new install it is easier, but you still have to do manual partitioning. And not everyone understands partitions.

The separate data partition is a lot more complex and requires mounting partitions  in fstab with proper ownership & permissions. Then creating folders in the partition and creating links. Not really for a new user.

I tried using the startup disk creator in Ubuntu to make another bootable usb, but it gave me this error when I clicked on format, I've included a screenshot. 

[ATTACH]231492[/ATTACH]

I have used different programs to create a bootable usb, but nothing works. The usb is fine. I have tried other usbs, but it's the same. And when I manually erase the files, and repeat, it gives me another error. 

[ATTACH]231493[/ATTACH]

When I click yes to retry, it gets past where it was and then gives me another error.

[ATTACH]231494[/ATTACH]

---

### Post by oldfred on 2013-02-16
Many suggest this:
       [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
    
How large is flash drive, is it already formatted. Most of the installers reformat entire flash drive to FAT32.

---

