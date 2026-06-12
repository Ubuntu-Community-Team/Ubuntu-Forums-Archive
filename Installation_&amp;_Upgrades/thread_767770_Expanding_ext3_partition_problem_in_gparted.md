---
title: "Expanding ext3 partition problem in gparted"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by GreenNet_user on 2008-04-25
Hi there,

I have a 40 GB hard drive with a dual boot windows XP and Ubuntu hardy heron installed.

Everything works fine.

The first section of the drive is a 15GB NTFS parition for windows. the middle section is/was a 15GB NTFS partition with only files stored on it. then comes a 1GB linux-swap and the last 9GB's or so has linux. 

I want to make the shift to linux more permanent and only boot into windows for specialised programs (adobe, illustrator, dreamweaver, etc.), so I'd like to use the 15GB NTFS partition in the middle and add it onto the last section which is the ext3 partition for linux.

When I use gparted it won't let me 'move/resize' the last patition (ext3), the only one I can modify is the middle NTFS partition, which I've now formated to ext3 to match the last partition.

Any suggestions as to how I can get around that? Or if I can just transfer the last partition with ubuntu installed onto the middle partition?? or merge them somehow?

Hope someone can make sense of all this... 

thanks.

---

### Post by Pumalite on 2008-04-25
Post a screen shot of Gparted.

---

### Post by GreenNet_user on 2008-04-25
[IMG]http://moogerfooger.gn.apc.org/screenshot_of_gparted.png[/IMG]

there you go. hope that helps.

---

### Post by Pumalite on 2008-04-25
Delete sda5 and swap. You'll have a large unallocated space. Then resize sda7 to the left. You can always put /swap at the end later, if you want. sda7 has to be unmounted at the time of the operation and prior to all this backup everything.

---

