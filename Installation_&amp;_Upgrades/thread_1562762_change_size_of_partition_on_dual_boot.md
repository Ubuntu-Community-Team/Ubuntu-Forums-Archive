---
title: "change size of partition on dual boot"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2010-08-28
on a dual boot can one change the size of each partitioned section of the boot once both sides are installed ?

i have a 500GB disc and i have lucid on 307 Gb and maverick on 145GB 

i did this so i could test maverick


now i would like to change the split to say half and half


can i do this?

i have mountmanager installed but i am not sure how to proceed.   Any clues?

---

### Post by Ceedub2 on 2010-08-28
Gparted does this. They say that not to partition with in Ubuntu itself.

---

### Post by DemonBob on 2010-08-28
Boot with the [Gparted Live CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/"), then you can make those changes.

---

### Post by shantiq on 2010-08-28
> **DemonBob said:**
> Boot with the [Gparted Live CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/"), then you can make those changes.



hi bob   could you say a bit more about this way of doing it

a few tips/steps please


[good guide here  ]("http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/")   


ok got it installed from terminal not sure what to do next i want to reduce one and increase size of other

---

### Post by shantiq on 2010-08-28
ok managed to reduce the first one sda1 but as you can see now
i have 160 unallocated and want to move that to sda 6 but sda6 has got this padlock on   HOW do i unlock it? i am sure it is simple just cannot see how to


[CENTER][IMG]http://img202.imageshack.us/img202/5227/devsdagparted001.png[/IMG][/CENTER]

---

### Post by oldfred on 2010-08-28
The extended is all one partition with many logicals but it is mounted as one. You may need to click on sda7 and swapoff as most liveCDs use the swap partition to speed things up.

But before you do anything, are you going to keep several system installs? If so you may want to consider a separate /data partition that you can mount in each install and have all the same data. 

I have 9.10 my old install, 10.04 my current & 10.10 each in 20-25GB partitions with only about 6GB used. All my data is in a data partition and mounted into each so whichever I boot I have all the same data.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by shantiq on 2010-08-28
hi olfred thanx for input


basically i want to keep lucid for a while until i know maverick can do everything fine that i need it to do

so at the moment i want both on my machines and i have both

i was too conservative when i installed maverick and gave it too little space

so i want to shift a lot of the lucid space unto the maverick side

got the gparted live disc but it is scaring the shite out of me
not sure how to handle it

can i use it AFTER i have installed both lucid and maverick

the situation i am in now and MODIFY the split of space

i do not even know that

so as you see many questions

can i even do what i am trying to do with what i have got now?

---

### Post by oldfred on 2010-08-28
You can expand but you show lots of free space in both right now.
You have 115GB & 132GB unused. If anything I would shrink system partitions and make large data partition(s), then next Nov after your 10.10 is good but you want to test 11.04 you can still mount the same data into that system install.

---

### Post by shantiq on 2010-09-08
ok finally done it



it HAS TO BE off a live disc of gparted as the program will not run on the mounted disc you are already on and you are trying to reduce/increase in size    which makes sense like trying to move furniture you are sittin on



found a really clearly explained video on [youtube]("http://www.youtube.com/watch?v=8n6bKDww5jc&feature=related")


must not frget ```
 sudo update-grub
``` at the end to ring in the changes on the grub startup




and after a couple of attempts i got there

well worth the trip    saves reinstalling EVERYTHING




nota bene
--------


at the last stage on linux 0 will not do as an option as it expects windows to be there so 1 is the right 

choice to get the visuals   then the video linked explains the steps clearly

it now looks as in the attached image (maverick is on the right)  thanx for all pointers

---

