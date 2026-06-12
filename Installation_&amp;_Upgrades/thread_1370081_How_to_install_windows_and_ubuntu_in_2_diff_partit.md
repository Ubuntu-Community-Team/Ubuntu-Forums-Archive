---
title: "How to install windows and ubuntu in 2 diff partitions???"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by tattushenoi on 2010-01-01
I have an 80 Gb Samsung HD.I have created 3 partions .

20Gb , 8 Gb , and rest 40 Gb.

I have installed Windows Xp in 20 Gb. I want to install Ubuntu 9.10[kramic koala] in 8 Gb partition...but when I try to install...

1.the 8 Gb partition is never selected automatically...
2.When I try to give it manually..the error message 'NO ROOT FILE SYSTEM DEFINED .CORRECT FROM PARTITION MENU' is displayed.
3.When i give largest cont space ..it selects [obviously] 40 Gb.

i have tried creating 5 partions of 8 Gb and one of 10 Gb...so that it selects 10 Gb...but it does not...what should i do to get windows in my c:[with 20 GB] and ubuntu in my D:[8Gb]...and rest 40 Gb of data...???

---

### Post by phawnex on 2010-01-01
which version of ubuntu are you using?
i just installed 9.10 this morning and it works fine. the partiton question asks to put it side by side when u restart your computer. it works fine. but i have an apple, so i dont know how it would be 100% on a pc.

does your pc actually show you partitioned your disc in three parts?

weird that it would do that. try fiddling with the manual option with different gig sizes...

---

### Post by tattushenoi on 2010-01-01
Partions====partitions*

---

### Post by tattushenoi on 2010-01-01
i am using 9.10

---

### Post by northrup on 2010-01-01
In my experience, 8 GB is pretty small for an Ubuntu installation, which is likely why it's not being autoselected.  I'd dip a little bit into either the Windows XP partition or the data partition to give it a little headroom; you'll need to take another chunk out of your partitions anyway for your swap partition, if you haven't already.

---

### Post by tattushenoi on 2010-01-01
yes...the side by side thing gets linux and windows in one partition and then separates.them...but when i formatted windows[i regret that now] linux also went off.....when i tried to install linux again...it doesnt select 28 Gb I reserved for windows and linux....linux goes into 40 Gb....

---

### Post by phawnex on 2010-01-01
yea 8gbs is pretty small.  i gave ubuntu 19 gbs. it says on the ubuntu site and other tutorials ive seen about installing ubuntu that it usually demands 8-10 with all the software packages it includes.

---

### Post by tattushenoi on 2010-01-01
i tried 10 Gb too....swap area is 1 Gb...

---

### Post by pastalavista on 2010-01-01
Choose MANUAL mode of installation again and at the partition menu select the 8gb partition and designate it as "/" in the format select area with an ext3 or ext4 file system to be the Linux root directory.

---

### Post by phawnex on 2010-01-01
weird... have you tried to totaly back up your disk? then totally reformatting and cleaning your disc so its just one   unit?  then repartition with 2? one with linux and one for ur windows?   im not familiar with pc backup utlities but maybe that would work? maybe someone else knwos a better option i had to back up my mac intel with time machine before partioning.

---

### Post by -=hazard=- on 2010-01-01
Did you formated it in ext3 or ext4? After the format did you pointed the partition on  /  ?

---

### Post by kansasnoob on 2010-01-01
I like to prepare my partitions using Gparted and then use the manual option to install as shown here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

