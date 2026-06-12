---
title: "partion and dual boot , how to, please help me"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by robbie carrobie on 2007-05-05
hi every one, i installed unbuntu on my laptop, after instalation i think that i partioned the whole hdd as my xp is nowhere to be seen, if this is the case how do i find out? any advise on how to partition the hdd to create a dual boot system would be helpful as would any advise on the partition ratios, my hdd is 100gb. Secondly the installed unbuntu on my hdd is not working as good as the live cd, can i reinstall over this with no further dire consequencies.  My brother who really loves linux and the unbuntu ethos suggested that i try it and after i decided that i really like it i find myself completely out of my depth after being conditioned to windows for so long - kind regards robert

---

### Post by neouser99 on 2007-05-05
to determine if you didn't write over your windows partition, there are a couple of ways. some where in the administration menu of gnome, there is a disk manager, and that should show you what partitions you have and what they are formatted with. if you are feeling brave, ```
fdisk -l
``` on the command line will give you the text version of your harddrive.

the easiest way to dual boot is at least 3 partitions, windows, swap, root. i would recommend something like this
40gigs windows ntfs
2gigs (depending on memory, 2x of total memory if memory <= 512mb, or same size if total memory greater. this might bring down a storm of responses, but i find this the best) swap
~58gigs root ext3, reiserfs, etc. (ext3 is probably your best bet for a desktop)

install windows first. when it's partitioner comes up, wipe the whole drive, and only allocate the first whatever gigs you decide upon, and install on that. then install ubuntu. when it's partitioner comes up, you can manually choose something or choose use all 'Free Space'. this will setup a custom partition table which is predetermined, and install ubuntu. IIRC grub will even detect that you have windows already installed, and will give windows xp as a boot option in it's own menu.

if you install windows second, it becomes a pain in the *** because it overwrites grub (linux boot loader) without even asking, and you have to go into a livecd and reinstall it, which isn't fun.

-neo

---

### Post by robbie carrobie on 2007-05-05
my friend thank you so much, its replys like this that make the transition from windows to linux so much easier, please be patient as i am probably pre destined to be a super noob for ever.

---

### Post by robbie carrobie on 2007-05-05
dude i found the disk utility and there is no sign of xp, my first partiontion is about 90 gig, my second about two and my third about two, so i can take it from this that i have made one mega pertition - what a slap head, slap slap slap

---

### Post by neouser99 on 2007-05-05
not a problem, good luck

-neo

---

