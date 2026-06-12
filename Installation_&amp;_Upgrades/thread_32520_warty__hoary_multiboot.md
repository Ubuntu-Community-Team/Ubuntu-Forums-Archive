---
title: "warty / hoary multiboot"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by strawberry on 2005-05-08
I hesitate between warty and hoary. I think warty some more stable and fits better to my configuration but hoary boots faster and looks better.
I've installed both and made partimage files of them.
I have two old drives. One of them is hda (primary master) the other is hdd (secondary slave). I install the actual system to hda and the partimage file goes to hdd.
Now I have warty in hda and an image-copy of hoary in hdd. I would like to compare the two ubuntu realize and try to tune hoary as fine as warty now. 
I edited grub so I can multi boot warty or hoary. It seems work but I'm not sure it is the proper way. I mean the hoary was installed on a 'hda' drive or '(hd0,0)' and now it is on a 'hdd' and '(hd1,0)'. I'm afraid there are lot of system files refers to hda/(hd0,0) and it can cause some trouble.
For example /etc/fstab file points to wrong location. This trouble I can correct editing the fstab file. (I hope I could clarify the matter.)
I would like to find and correct all wrong refers if it is possible. I need some clue where I should look for these system/application files. 
Thanks in advance. If I wasn't clear please ask :)

---

### Post by defkewl on 2005-05-08
Have you fixed /etc/fstab so it refers to the same harddisk as in grub?

---

### Post by strawberry on 2005-05-08
'Have you fixed /etc/fstab so it refers to the same harddisk as in grub?'

Yes I have. I changed 'hda1' to 'hdd1' for root system and also append a line that mounts 'hda1' to /mnt/disk. 
This time I'm writing from hoary. So it works so far...

---

