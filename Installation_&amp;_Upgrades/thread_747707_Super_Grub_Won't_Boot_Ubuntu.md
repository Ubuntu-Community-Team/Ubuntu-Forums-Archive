---
title: "Super Grub Won't Boot Ubuntu"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by Brightrock on 2008-04-06
Hi,

I installed Ubuntu the other night.  I got a grub error 18.  I used Super Grub to fix the MBR for windows.  But I can't get to the ubuntu install (or fix the grub).  I've searched the forums and the ideas.  I tried changing the BIOS to try to get at the partiion before I used supergrub... but no luck.  I'm not sure where to go from here.

I used the "Manual" option in the partitioning section of the install process.  I may have made a mistake there.  Anyhow, I'd like to be able to get to my Ubuntu partition... anyone have an idea what I should try now?  

Thanks,

BR

p.s.  Pardon the very quick unpunctuated and random caps... I'm heading out the door...

---

### Post by metalf8801 on 2008-04-06
here see if this helps 
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by Pumalite on 2008-04-06
If the following applies to you, this might imply creating a /boot partition:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by Brightrock on 2008-04-07
I think that will help.  It also helps me understand the problem. Looking at the instructions it looks like I need to specify three different labels to the partitions.  I only labeled \ and swap.  So this is my guess about what I did wrong, perhaps you can tell me if I'm right.  You need to label your Window's partition as \ and your Ubuntu partition as \boot and swap as swap.  Is that right?  The Window's partition contains the MBR sector of the disk that can then point to the grub on the Ubuntu partition.  Is this correct?  Is that possibly why I got the Grub error18?  If not which partitions need which label, I think that is the source of my original problem  

Thanks for the quick reply.  These Ubuntu forums are great, because of you people who answer questions so quickly.  I sure appreciate it. 

BR

---

### Post by Brightrock on 2008-04-07
Also, I'm reading the Grub page right now, so I might figure this out on my own... but I don't mind help, either. 

Thanks Again,

BR

---

### Post by Brightrock on 2008-04-07
Ok, so I've looked into it more and the fundamental reason I cannot boot Ubuntu is that I have installed it after 137GB BIOS limit on my 250GB hard drive I installed just recently.  I have a 100GB data partition before it.  I want both Windows and Ubuntu to access the data partition.  In the past I've always put the data partition between the Windows and Ubuntu partitions.  Is there any reason why I shouldn't put the ubuntu partition before the data partition?  Will this cause any problems with Windows accessing the data partition?  Anyone have any experience with this.

Thanks,

BR

---

### Post by Herman on 2008-04-07
It sounds like a good idea to me.
There shouldn't be any reason for both operating systems not to be able to access your data partition regardless of its actual physical location on the hard disk. 
Maybe try resizing Ubuntu just a little bit first and making a small data partition at the end of your disk and test it first to make sure Windows can read it before you make the major changes?

---

