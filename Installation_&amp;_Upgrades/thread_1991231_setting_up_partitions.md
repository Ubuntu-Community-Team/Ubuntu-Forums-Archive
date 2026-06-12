---
title: "setting up partitions"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by varunit on 2012-05-30
Hi all,
I am currently running windows 7 according to the partition setup shown in the image

[IMG]http://i.imgur.com/VuJSF.jpg[/IMG]

Now I would like to install ubuntu. I have around 70 FB free space from the large partition. I want to know the best method to complete installation without losing my data. I came to know about another method of installation by shrinking c drive. I don't know much of the process.. Any help would be appreciated. Thanks :)

---

### Post by dino99 on 2012-05-30
remember that windows stop working if the %free space is < 10% , so you cant shrink c: too much; and the first step is always to clean the room: removing all the crap around there (ccleaner is a good tool for such job), then run defrag and finally shrink.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Jose Catre-Vandis on 2012-05-30
In that screen you are on,right click on the big partition and select Shrink Volume, wait a while then accept the value offered or change it (It may not be as big as you hoped for due to the location of files on the disk).

Once finished you should have some unallocated space.

You can now boot up with your live cd and install ubuntu to the empty space, and install grub bootloader - this should find your Windows 7 install!!

---

### Post by varunit on 2012-05-30
Can you please suggest the best way to install (no loss of data) with my current config scenario? 
Like the steps to get free space from that big partition
Thanks for the time

---

### Post by jadtech on 2012-05-30
best way to do this with no loss of data would be to start out   running dskchk  and defrag before you shrink the volume of the window partition to make sure all the data  is together and not scattered over the drive .. 

you have to know how much free space your windows partition windows always need 10% free space that nothing is ever stored on   just to run you get below that it will stop running .. 

ok moving on from that assuming the room is there to free up your 70gb of space for ubuntu  just return as stated before to the area  of your Image right click for the amount you want to shrink type in 70000  keeping in mind you   the measure  is in  mb 1000 mb is 1gb so 70,000 is 70gb ..

from that point  boot from the live cd

---

### Post by varunit on 2012-05-30
okay.. thanks. going to defrag my partitions now

---

