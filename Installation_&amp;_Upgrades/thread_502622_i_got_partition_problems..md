---
title: "i got partition problems."
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by jjjhackkk on 2007-07-16
hi,

i cannot pass thru w/ partioning hard drives.

Pls help me.. :confused:

i used windows xp on my drive c: and iim planning to install ubuntu to drive d: (to make dual boot).  i'm a first time user of linux.. hopefully.

when installing the liveCD, i passed with time zone, keyboard and now partioning.. i cannot install it on my drive d: always looking for ROOT.  im getting frustrated, i thought its user friendly :confused: 

anyone pls help me how to do partioning? :confused:

one thread shows  how to do:

swap = /sda/hda3 :confused:
root  = /sda/hda4 :confused:

but how? where could i edit this partioning? where can i input this? how to make a SWAP and ROOT? 
format from wat extension file? ext3?ext2?nfts? etc.. :confused:

i tried exploring he GNOME partioning, but i dont know how to do, when i do formating, it shows only pending operations, but i dont see my hard drive is responding to this formating operation.. :confused:

any walkthrough? or screenshots? 

i would really appreciate.

thanks,
regards to all :)

---

### Post by ReaderRat on 2007-07-16
There's some good stuff here --->>> [[color=red]Ubuntu Tutorials[/color]](http://www.psychocats.net/ubuntu/index.php)
Check it out.

---

### Post by JesterDev on 2007-07-16
First off, calm down. :)

It&#347; not that hard to do this. In fact Im installing myself right now (got a new video card). So let me walk you through it. Choose manual, then click next. First off you want to create a swap partition. You'll want at least twice the size of your RAM. So for me, I have 1 gig, so I create a partition with 2gigs for swap. Once you have created that, just click on it, then on the bottom click edit (once the partition is highlighted edit will appear). Choose swap from the drop down menu. Use the rest for root, and follow the same path as above only this time choose / (root). I suggest ext3 for your file system. 

Next just click forward and follow the on screen prompts. 

Hope this helps!

---

### Post by jjjhackkk on 2007-07-17
thanks for fast reply.

im now doing the partitioning, how do i partition my harddrive?


device       type mount pt.     Size         Used
/dev/hda
/dev/hda5  ntfs /media/hda5 41900mb 38000mb
/dev/hda5  ntfs /media/hda5 38074mb 24500mb
free space                          8mb

what should i do?

i have 512mb of memory ram.

how do i configure mount point and root? 

thanks,
regards.

---

### Post by jjjhackkk on 2007-07-17
/dev/hda1 ntfs /media/hda5 41900mb 38000mb <----- OS wndows
/dev/hda5 ntfs /media/hda5 38074mb 24500mb <----- my free drive (d:)

---

