---
title: "how to partition for ubuntu(tryed everything)"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by Smithben1983 on 2008-06-24
i am having the hardest time trying to partition my drive. i have been using XP on this PC for sometime now, and want to use ubuntu as well. i have tried to partition in 2 ways [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing") (just using the installer) doesn't even give me the option to partition just to install or do it Manuel. [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition") (using gnome partition) i try to unmount my drive it thinks for a bit than nothing happens and i cant resize. please help me :)

---

### Post by avtolle on 2008-06-24
First, if you have not done so, defrag, defrag, defrag. Then, from Live CD, Alt+F2, gksudo gparted. Then, when gparted loads, shrink the Windows partition to create unallocated space. However, if using Vista, please use the Vista tool to resize the Vista partition. Then, go into the Live CD and proceed.

---

### Post by jpyanowski on 2008-06-24
....Eh...what he said...:wink:

---

### Post by Smithben1983 on 2008-06-25
okay i tryed that now and it went a bit better it let me at least think i could resize it but i got nothing here is a few screen shots of what it looks like.
[IMG]http://i300.photobucket.com/albums/nn2/smithben1983/Screenshot.png[/IMG]

[IMG]http://i300.photobucket.com/albums/nn2/smithben1983/Screenshot-1.png[/IMG]

[IMG]http://i300.photobucket.com/albums/nn2/smithben1983/Screenshot-2.png[/IMG]

---

### Post by thschiavo on 2008-06-25
Can you explain with more words your problem?... You wanna know how to proceed then, is it?

---

### Post by arpanaut on 2008-06-25
Did you read the instructions in the warning message?
There are errors in the WIN file system until those are corrected you are not going to be able to do anything with that disk.
Once you do as instructed, go back to the live cd and gparted and see if the triangle w/! is gone then you will be able to do operations on your disk.

How much free space is on your HD?

---

### Post by logos34 on 2008-06-25
like arpanaut said, do what the error message suggests--run chkdsk scan.

Boot back into windows, go to My computer>right-click on c:\>properties>tools>error checking with repair option

---

### Post by sam1948 on 2008-06-25
there is an error that i as a newbie (i still do) did

preface 
basically _every_ linux needs to partitions
1) **_ext3_** (or compatible other linux partition)
   with size of at least 2GB (i recommend 10)
2) _**swap**_ partition 
   with recommended size of 512 MegaBytes 
  (u'ld better make it 1Gb. the rule says twice of u'r memory size is good)  

there are 2 major ways u can implement these recommendations
_first:_
  make one primary partition with two inner logical partitions as explained 
_second:_
  make two different primary partitions as explained above 
******end of preface

now when installing the _gparted_ (or  other partition software) will automatically mount the larger partition into a directory that will looks like this "media\hdc1" or any thing like it (a bit different letters or mnt\hdc1 and so on) 
what u have to do is fo choose the partition and press the edit button
and choose "mount point" to be "/" 
then mark the flag in the column says "format"
this should do

---

### Post by avtolle on 2008-06-25
But first, he needs to correct the error shown before taking any further steps.

---

