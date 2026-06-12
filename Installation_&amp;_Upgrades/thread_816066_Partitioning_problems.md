---
title: "Partitioning problems"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by Da'Jobat on 2008-06-02
I have recently installed a clean version of Ubuntu Hardy (8.04) on a new partition, however it installed to a very small partition for some reason. When I tried to resize it using the 50-odd Gb of extra space i had remaining where i wanted it to install, i was not able to. I think that this may be because it is on a different sda group, but i don't know what to do now. Here is the gparted output.
[IMG]http://i254.photobucket.com/albums/hh109/takingapoo/Screenshot.png[/IMG]

Thanks for your time
Jobat

EDIT: terribly sorry, the partition i want to resize is /dev/sda6, forgot to say

---

### Post by Partyboi2 on 2008-06-02
Make sure the partitions that you want to are unmounted first. Use the ubuntu live cd or gparted live cd to work on the partitions.  When gparted is open to umount highlight the partition and right click and choose  "unmount" Then increase sda2 to the left to use the 53.09 gig.

---

