---
title: "Screwed up  the partitions, How to restore"
date: 2005-03-26
forum: Installation &amp; Upgrades
---

### Post by Klemm on 2005-03-26
Hello, new here.

Very bad that my first post starts with a cry to help....

I read some days ago about ARK linux and decided to fire it to my spare partition. It was not so easy. It messed up the partitions and my system does not boot up any more.....

Is there any tools or ways the previous partitions can be restored. ?  Or is it even possible to restore anything.   I dont care about the root partition, system can be reinstalled and so on, but I want to restore my data files from the place that used to be /home   untill I fired the ARK cd in my box 


Kristjan

---

### Post by Xian on 2005-03-27
[QUOTE=Klemm]It messed up the partitions and my system does not boot up any more.....[/QUOTE]
Are you sure some of the partitions are not still there? Just because your system won't boot doesn't mean that you wrecked you data. Try booting with a LiveCD and use that to see what is still on your HD.

---

### Post by Klemm on 2005-03-28
[QUOTE=Xian]Are you sure some of the partitions are not still there? Just because your system won't boot doesn't mean that you wrecked you data. Try booting with a LiveCD and use that to see what is still on your HD.[/QUOTE]
How do I see it ?

HD is total 40Mb
I had partitions like those:
previusly I had partitions as following
hda1 =  /  (ext3) (~8,5Mb)
hda5 = swap (517mb)
hda6 = /home (ext3)
hda7 = /home/__username__/archive  (~6Mb)


Now I have them 
hda1 - 321mb  swap
hda2 - 39mb (ext2)
hda3 - the rest of disc


I scanned the harddrive using gpart and it told the following

Possible partition(Linux swap), size(321mb), offset(0mb)
Possible partition(Linux ext2), size(39mb), offset(321mb)
Possible extended partition at offset(9091mb)
   Possible partition(Linux swap), size(517mb), offset(9091mb)
End scan.


With ad offset of 9091mb + 517mb the previous home should start.
I dont catre about the system area I had. its no problem to reinstall (especially ubuntu), but I care of the area that used to be my /home and I really want to get the data out that was there...
Only question to me is still how to restore the data ?

I feel sort of dumb in this area, it is comlicated thing, have not had anything to deal with restoring systems, but I'd like to learnd it and do it untill I have some hope to restore the data files

What is a chance to recover from this mess? or what is what I should do actually to try restoring the data

---

