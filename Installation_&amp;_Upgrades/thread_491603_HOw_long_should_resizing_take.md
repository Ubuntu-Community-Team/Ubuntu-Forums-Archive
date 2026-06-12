---
title: "HOw long should resizing take?"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by BigSteve on 2007-07-03
HI, newbie here, need help. 

Bought UBUNTU LINUX FOR NON-GEEKS. 

Reloaded Windows XP SP2 on my computer to have a clean load there, no defragnecessary.

Trying to install Ubuntu form Live CD.  Got to the Resizing screen to create Dual Boot.  Has been on Prepare Disk Space screen  for several hours.  

NOt sure if I should cancel and try again, or will I jsut restart a long process?

HELP

btw:  60GB drive, resizing to 18.2 GB
HP Pavillion

Steve

---

### Post by coldstatue on 2007-07-04
Well, Steve, I'm not going to be much help here, but I can tell you that simply resizing (not moving any data) only takes me about a minute or 2. Are you shifting the partition with data on it, or just moving the end of it back? Sounds like you've got a lot of empty space at the end with a clean install there. When you say no defrag necessary, do you mean you tried it in Windows, and it said it was not fragmented, or just that it isn't necessary? because Windows will say that untill it gets to a certain fragmentation percentage. Ii am not sure what it is, but Win doesn't make you defrag until it reaches a certain point. There could be data there. Still, not sure if a fresh install would do that, but if you were fragmented befrore the new win install, there could be problems.

---

### Post by srunni on 2007-07-04
> **BigSteve said:**
> HI, newbie here, need help. 

Bought UBUNTU LINUX FOR NON-GEEKS. 

Reloaded Windows XP SP2 on my computer to have a clean load there, no defragnecessary.


A clean install probably means no data on the partition...

@BigSteve:
Try the alternate CD if you're having problems with the main install CD - I've had to use it on some older computers, and now I prefer to use it on all installs.

---

### Post by coldstatue on 2007-07-04
Did you format the win partition during the fresh install?

---

### Post by BigSteve on 2007-07-04
Welllllll,

As I read more I suspect that my problem is in the XP install.  There is only one partition on my C: drive.  (all 59 G or so.)

When I start diskmgmt.msc to add a partition, it does not show add a partition as a possiblity. Is that because I should have set it up for dual-boot when I installed XP?

Some questions:
 1. The partitioning must be doen from within WIndows or when booted into Ubuntu from the Live CD?  My guess now is "from within Windows"
2.  Do I need to reinstall Windows differently?  I hope not.
3. What alternate CD?  The book came with one disk only. "Ubuntu Desktop CD 6.06 (Dapper Drake) for x86 PCs"

Thanks for the patience.
Steve

---

### Post by coldstatue on 2007-07-06
> **BigSteve said:**
> Welllllll,

As I read more I suspect that my problem is in the XP install.  There is only one partition on my C: drive.  (all 59 G or so.)

When I start diskmgmt.msc to add a partition, it does not show add a partition as a possiblity. Is that because I should have set it up for dual-boot when I installed XP?

Some questions:
 1. The partitioning must be doen from within WIndows or when booted into Ubuntu from the Live CD?  My guess now is "from within Windows"
2.  Do I need to reinstall Windows differently?  I hope not.
3. What alternate CD?  The book came with one disk only. "Ubuntu Desktop CD 6.06 (Dapper Drake) for x86 PCs"

Thanks for the patience.
Steve

The reason you do not have add a partition as an option is probably because there is no space to do it. You said ALL 59 gig. If the whole disk is in one partition, there is no place to create another partition. you have got to resize first, then create new.

Questions
1. I always format/size/do all partition work with the Gnome Partition Editor (GPartEd). You don't have to do it in Win.
2. No, there shouldn't be any reason to do a different kind of install. I don't remember how much space a win install takes, but 59G is way more than enough.There is nothing special you need to worry about Windows except that it is leaving enough space, which I am sure it is.
3. The alternate CD is for people who have problems with the live CD, or are making custom installs for multiple systems and such. i think there are some other reasons to use it, but you shouldn't need to worry about that. If the live CD keeps hanging on resizing a partition, the alternate would be a good thing to try.

I would try to resize again with the live CD, then try alternate. There is no reason to format or size in Win, and it causes lots of problems. When I first started my then-quad-boot system, I was resizing and formatting in win with i don't know what program, but the sizing was sloppy and giving inaccurate readouts. Someone here told me not to bother with all the win formatting/sizing/boot managers. Nervously, I let go of my dependencies and did everything Linux. It all worked. I won't say flawlessly, but alot better than it did when I was trying to use Windows programs. (BTW, my quad boot - suse, ubuntu, fedora, win is now a tripple-boot: win, ubuntu, ubuntu studio.) I just wanted you to know, that in my opinion, you have found the best linux distro, so keep working with it. It IS worth it.)

Try to resize again with the live CD, then if it doesn't work, with the alternate CD (no graphical mode). Let us know what happens. You may want to start a new thread and link to this one, just to be sure it gets the right attention, because alot of the experts (including the beginner team) are always trying to help with the unanswered threads.

---

### Post by coldstatue on 2007-07-06
Don't forget to be very careful about the partitions you select for formatting and install once you get 2 partitions.  It was scary for me. Just go slow, and keep a pen and pad of paper handy to write down partition's names to ease your mind. Still, with a fresh Win install, at least you won't be losing years of work or anything if you mess up.
Thankfully, GPartEd gives a good graphical display of your disk.

---

