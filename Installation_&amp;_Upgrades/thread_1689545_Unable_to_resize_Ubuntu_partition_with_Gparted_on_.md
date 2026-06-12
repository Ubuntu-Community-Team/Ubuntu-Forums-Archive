---
title: "Unable to resize Ubuntu partition with Gparted on Live CD?"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by sjpupal on 2011-02-16
Hi all,

 I recently got new hard drives for more space and copied all my old drives onto this one (everything mirrored, no problems)

The thing is, when I first setup my Ubuntu, I only allotted like 20GB because of space.

Now that I have new hard drives, I wanted to give it more space, roughly double it to 50gb.

The problem is, I am unable to resize it.

I have booted into the Ubuntu Live CD, and started Gparted. I see all my stuff there, including the unallocated space next to my ubuntu partition (I left it so i could fill it when I expanded the partition)

The problem is, I am unable to make it larger.  I right click, click on resize/move, but when I do, it just shows that I'm at my maximum size for that partition, I can only shrink it.

so my question is, how in the world can I extend that partition into the unallocated space?

I've tried formatting the unallocated space to ext3 to try and merge it, no success.

I tried moving my ubuntu partition all the way to the right (end of the disk) so maybe I could extend it to the left, nothing.

Any ideas here?

Thank you!

BTW I took a screenshot so everyone could more easily see what's going on.

The 881GB is my main HDD.  
The little red sliver is my linux swap.
The one just to the right of it is my ubuntu partition.
And the block all the way to the right is the space I want to   ....add to my current partition.

---

### Post by wilee-nilee on 2011-02-17
> **sjpupal said:**
> Hi all,

 I recently got new hard drives for more space and copied all my old drives onto this one (everything mirrored, no problems)

The thing is, when I first setup my Ubuntu, I only allotted like 20GB because of space.

Now that I have new hard drives, I wanted to give it more space, roughly double it to 50gb.

The problem is, I am unable to resize it.

I have booted into the Ubuntu Live CD, and started Gparted. I see all my stuff there, including the unallocated space next to my ubuntu partition (I left it so i could fill it when I expanded the partition)

The problem is, I am unable to make it larger.  I right click, click on resize/move, but when I do, it just shows that I'm at my maximum size for that partition, I can only shrink it.

so my question is, how in the world can I extend that partition into the unallocated space?

I've tried formatting the unallocated space to ext3 to try and merge it, no success.

I tried moving my ubuntu partition all the way to the right (end of the disk) so maybe I could extend it to the left, nothing.

Any ideas here?

Thank you!

BTW I took a screenshot so everyone could more easily see what's going on.

The 881GB is my main HDD.  
The little red sliver is my linux swap.
The one just to the right of it is my ubuntu partition.
And the block all the way to the right is the space I want to   ....add to my current partition.

Right click on the swap and turn it off, then delete the partition on the end. Then exspand the extended=sda2 to the end of the HD, then do the same with the Linux partition.

You can't merge partitions.

---

### Post by sjpupal on 2011-02-17
I right clicked the swap, but it was already off (only option is swap on)

I deleted the partition at the end, no problem.

The only place I do have a problem, is by extending the "extended=sda2 "

Are you getting at, that the linux swap and linux partition are INSIDE of that, and so I need to extend the extended to make room for them?

I can see how that makes sense, but I am unable to select the extended,  the linux swap and ext3 are seperate partitions, it will only let me individually select them.

Maybe I'm missing soemething, tomorrow I"ll boot into it again and try to finagle with it =D

---

### Post by wilee-nilee on 2011-02-17
> **sjpupal said:**
> I right clicked the swap, but it was already off (only option is swap on)

I deleted the partition at the end, no problem.

The only place I do have a problem, is by extending the "extended=sda2 "

**Are you getting at, that the linux swap and linux partition are INSIDE of that, and so I need to extend the extended to make room for them?**

I can see how that makes sense, but I am unable to select the extended,  the linux swap and ext3 are seperate partitions, it will only let me individually select them.

Maybe I'm missing soemething, tomorrow I"ll boot into it again and try to finagle with it =D

You have got it the extended is a partition itself, and contains the others.

If you right click on the extended in the text listing partitions on gparted there will be a resize choice for the extended. 

I wonder if your not able to re-size the mirrored partitions, I wouldn't think so it seems more of an understanding of using gparted.:)

---

### Post by sjpupal on 2011-02-17
Well, it seems this particular problem was due to user error xD

I didn't really recognise that those partitions were INSIDE of the other, and so I needed to extend that partition to allow for the expansion of the others...D'OH!

lol

BUT, alas there is another issue.

I extended the partition, and now have the ability to extend my ubuntu partition to fill the space.

The thing is, everytime I tried to enlarge it, it said the disk was busy or in use (even though it shouldn't be, I was on a live CD)

So I rebooted thinking it needed to refresh itself...but that brought about bigger problems.

As seen in the screenshot, now it gives me errors by my NTFS partition (windows) and the ubuntu.

The windows error says something about it can't find the drive, and superblocks is corrupt.

The ubunut one, well you can see in the screenshot what it says.

I then tried booting into my Ubuntu normally, but now it just hangs at the Ubunut loading screen, it never goes anywhere.

So I tried using Rescatux to fix the MBR, but it just added ANOTHER set of ubuntu and windows bootup options to the Grub Menu.

Now, whenever I try to boot into windows, it says my crap is all corrupt.

With ubuntu, it won't load at all.

I'm so glad I did this on my mirrored hard drive, so I'll just copy it all over again and try it anew. 

I really don't understand it though, I LOVE ubuntu, but it seems everytime I try anything simple it ALWAYS messes with something, be it the GRUB, MBR, now superblocks or whatnot......:(

If you have any advice I really appreciate it, in the meantime it'll take a good 5+ hours to copy it all over again to my other HDD to try again.

cheers!

---

### Post by oldfred on 2011-02-17
Since the extended partition is one of the 4 primary partitions any logical mounted in it mounts the entire extended and you then cannot edit it.
The little keys show it is mounted. Normally liveCDs mount swap to speed things up. You must not have done swap off.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by sjpupal on 2011-02-18
Thanks oldfred, but I was using the live CD and nothing was mounted, and as for the linux swap, it was off, I checked.

But yeah, I think something just got corrupt, I really don't know why, because I mirrored my good HDD to the other one and did the EXACT same thing as before, and it finally allowed me to resize the partition, and grow the linux partition!!

So yeah, idk why it wasn't working last time (or why it corrupted everything), makes no sense, but whatever this time it worked so I'm happy!

Thanks to everyone for their help!

---

