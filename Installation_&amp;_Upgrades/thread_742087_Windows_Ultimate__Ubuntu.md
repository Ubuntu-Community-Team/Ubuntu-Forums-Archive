---
title: "Windows Ultimate / Ubuntu"
date: 2008-04-01
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2008-04-01
I Have Windows Vista Ultimate installed and running on my computer. I now want to ADD and install Ubuntu on to my system. Both to be  running on the same hard drive. Is this possible ???. Do I have to partition ?? if yes to these questions, can someone guide me thr'o the process.The idea is if Ubuntu performs well for me - then I will scrap Windows,but want to test it all out first !!

---

### Post by forestpixie on 2008-04-01
Yes it is possible - it's dual booting - [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

You will need to have a partition to install it into - use the Vista resize tool to create the space. [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

Once you have some space you can use the partition editor on the buntu cd to create the partitions. This is worth looking at - 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Ideal@EFnet on 2008-04-01
Can you do it the other way around, Ubuntu first, and then install XP?

---

### Post by forestpixie on 2008-04-01
**Ideal@efnet** - Yes you can do that - but you will then need to reinstall grub as windows will overwrite it, it's easier to do in win/buntu order, but not mandatory. That's the way I would do it - if at present you haven't anything installed do all the partition work beforehand and then install.

---

### Post by Dyffo on 2008-04-02
Thanks for this guys. Unfortunatly Windows Ult is already installed and running. So Ubuntu will come in second !!
You have all given me loads to look at and think about - will come back to you and let you know how I get on.

---

### Post by forestpixie on 2008-04-02
Best way to do it I'd say. Good luck with it.

---

### Post by sholmes555 on 2008-04-04
Hey forestpixie, I'm a newbie too to this whole dual booting thing. I'm basically in the same boat as Dyffo is, vista ultimate, and I've got an ubuntu CD sitting right here on my desk that I'm eager to dual boot with. I tried visiting that vistarewired site but for some reason I'm either being stupid or something but I can't seem to get any of their links to work...it just keeps taking me back to their homepage. Anyway, my friend told me of something called wubi, but i'm not sure if that's for me? 
to basically install ubuntu, I just have to get vista to shrink up some HD space, and then stick in the ubuntu CD and install ubuntu onto that newly created space? It seems to be pretty straight forward...unless i'm missing something big.

---

### Post by forestpixie on 2008-04-04
No you're not missing anything big - unless you install it wrong :) Then you'd be missing everything - don't install to the whole disc - because that's what will happen.

---

### Post by sholmes555 on 2008-04-04
Thanks for responding! though...what do you mean by "don't install to the whole disc"? The ubuntu CD should notify me of my newly created space that i used vista to get and then i can just have ubuntu install safely in there, right? the rest of the partition(s) will belong still to my vista....i think...

thanks so much and apologies if the questions sound too newbie-esque...

---

### Post by forestpixie on 2008-04-04
Half way through the installation you get to the partitioning part - one of the choices is to install to the whole disc - do not do that.

Easiest way for you I would suggest is use vista to resize the vista partition and do not format the empty space - it won't format to a suitable file type anyway.

Boot the livecd - let it open - in the system >admin menu - open partition editor.

It will show the empty space - create an extended partition on it - then make 2 partitions inside the extended space - 

1 off which should be all of the space minus 1.5 x your RAM - format to ext3,
the other one the remaining space - format as swap.

When you get to partition in installation - choose manual

select the partition you have created and formatted to ext3 - edit partition and select mountpoint as /

That should be it - make sure you have backups before you start though.

---

### Post by sholmes555 on 2008-04-04
awesome, thanks forestpixie! i'll try that later today (at work now) and I'll let you guys know if there are still any problems/confusions. :)

---

### Post by sholmes555 on 2008-04-04
Hey forestpixie, i finally got a chance to try and follow your instructions and i'm getting a little confused. So I used vista's shrink and created an unallocated (and unformatted) space of about....190 gigs. Then i restarted and booted from the ubuntu CD, and opened up partition editor. it shows my two partitions which belong to my vista side of things, and it also shows me the newly created empty space. When i highlight that empty space box, and then click "New" under the partition editor, i get the little "create new partition" window that has me fill in some info. It's here that I'm stuck...

This is what I've got so far...
Free Space Preceeding: 0
New Size: 189999
Free Space Following: 0
Create As: Extebded Partition
Filesystem: grayed out
When I left it like this and just clicked "Add", i saw the extended partition space pop up in addition to an unallocated space (of nearly the same size) but I could not figure out a way to re-partition the extended space in the 2 ways you had suggested. please advise, thanks!

---

### Post by sholmes555 on 2008-04-04
Actually I think i may have got something but would still like your feedback (if you can give it) before I proceed:

I created a new extended partition of about 185.54 GB and the hierarchy goes as follows:
New partition #1         Extended         185.54 GB
   New partition #2      ext3                 182.52 GB
   New partition #3      linux-swap          3.03 GB

Is this what you had wanted me to do? Thanks so much!

---

### Post by forestpixie on 2008-04-05
Yea - small thing though - if you've got 64bit it won't matter, but if you've got 32bit - then assuming that you have 2Gb RAM - you can resize the swap to be smaller as it won't all be recognised - max of 4Gb.

---

### Post by sholmes555 on 2008-04-05
I'm not quite sure what version I have... I know my vista CD came with a 32-Bit DVD and a 64-Bit, and I opted for the 32-Bit since I don't go too crazy. I got the ubuntu live CD from amazon.com and It didn't specify on there (i don't think). 

Also..this didn't occur to me until recently when i started to search these forums, but...I just installed SP1 on my Vista Ultimate...and i can't quite tell from the forum postings, but it seems most people face problems when they already have ubuntu and they're trying to upgrade to sp1...since i already have it, i presume the ubuntu won't have an issue? any ideas anyone? 

and yes i do have 2 gb of ram, knowing those #'s up there, what would you recommend for my swap? thank you so much for all the help! 

(i'm new to this forum and it seems that this forum is pretty friggin' chill with ubuntu help for n00bs/guru's)

---

### Post by Tews on 2008-04-05
> Half way through the installation you get to the partitioning part - one of the choices is to install to the whole disc - do not do that.

Actually I did exactly that ... however I had 2 internal 160gb drives in my laptop and a 500gb external.  If you have the extra drives, I found that this was easier than creating the partitions.  Either way be sure you have your data backed up before attempting to re-partition.  

Welcome to Ubuntu!!  :lolflag:

---

### Post by sholmes555 on 2008-04-05
bump. eager to try and get ubuntu up and running but hesitant on moving forward since i'm not 100% sure what i'm doing...any help'll be cool!

---

