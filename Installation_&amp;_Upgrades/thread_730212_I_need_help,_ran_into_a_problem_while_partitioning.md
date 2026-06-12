---
title: "I need help, ran into a problem while partitioning"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by sunburstgl on 2008-03-20
ok, so i decided i wanted a dual boot of xp and xubuntul. So today I successfully installed xubuntu on a partition of what i thought was 17 gb...unfortunatly I installed xubuntu on the 80 gigs of free space from my xp partition. so I now have an 80 gig partition that boots xubuntu and an 17 gig partition that boots xp pro. I need some help with this. I want to know how I can edit the partitions so xp has 80 gigs of space and xubuntu only has 17 gigs.

your help would be greatly appreciated.

---

### Post by fela on 2008-03-20
Windoze only deserves that little...lol only joking!

You could use gparted (on the gutsy livecd I believe, in System > Administration > Partition Editor), but i [COLOR="Red"]**strongly reccomend backing up all your data first**[/COLOR].(and i think you might need to defrag NTFS partitions before editing them with gparted)

i hold no warranties for data loss and/or timewasting, I'm just trying to help :)

---

### Post by sunburstgl on 2008-03-20
ok thank you, i am currently trying to use gparted. for some reason there is a little lock symbol on all of the partitions, do you know how I can get those off of there so i can at least size down my ubuntu partition before I defrag and enlarge my xp partition?

---

### Post by dstew on 2008-03-20
You can only edit (resize) unmounted partitions. You will have to use gparted from a Live CD to change the partition sizes.

---

### Post by sunburstgl on 2008-03-20
alright thank you. I ran gparted from the live cd and I shrunk my ubuntu partition down to about 15 gigs. Now i have a 70 gig unallocated section. How do I get that section to be applied as free space to my windows xp partition? Do I have to defrag my xp partition first?

Detailed instructions would be nice, but anything will help

---

### Post by dstew on 2008-03-20
I think you can resize (expand) your XP partition now. I don't think you need to defragment first if you are expanding, but I am not sure. You might have to move your now shrunken Ubuntu partition over so that the XP partition can expand.

---

### Post by sunburstgl on 2008-03-21
Alright thank you, I will try that. I thought i might have to move the linux partitions over.

---

### Post by fela on 2008-03-23
yes, you certainly have to use a livecd to resize partitions. (have them unmounted anyway)

---

