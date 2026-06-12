---
title: "dual boot partitions"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by superhaus on 2007-12-21
I am setting up my new laptop to dual boot XP and Ubuntu. I will use Ubuntu most of the time, with XP pretty much only for some games. It has 2GB RAM and 120GB HDD. What do you think of these partitions?

40GB Windows
60GB NTFS for both OSes
20GB Ubuntu

I know that the numbers don't work out exactly, but you get the idea.

About partitions...

The 20 GB Ubuntu partition should be / right?
Should the 60 GB be /home?
I need a small /swap in there too, right? What do I need for that? 1-2GB?

Any advice would be helpful, You can even call me an idiot as long as you post something helpful as well!

---

### Post by zach12 on 2007-12-21
Looks good to Me

---

### Post by Herman on 2007-12-21
```
 About partitions...

The 20 GB Ubuntu partition should be / right?
``` Yes, that looks right to me.
>  Should the 60 GB be /home? No, that will just be a shared data partition if I understand correctly what you are intending to do. I'm not too sure what you need to do in the new LiveCD partitioner & installer for that, mount it as /data maybe or /windows, something like that. Or just ignore it and mount it yourself after the installation is over.
>  I need a small /swap in there too, right? What do I need for that? 1-2GB? You would never need a swap area larger than 1.0 GB. I just make all mine 1.0 GB because it's a good round number. The size of the swap area is not so critical in most new computers nowadays. WIth over 1.0 GB of RAM your swap area won't likely even be used, but it doesn't matter anyway, because there are such large hard disks on the market, that no-one even notices the allowance of a whole 1.0 GB for a swap area.

Not so long ago, when most computers might have had 64, 128, 256 or up to 512 mb of RAM, the amount fo swap area to allocate was a hot topic here in Ubuntu web forums.
I have read that most computers can't utilize a swap area of more than about three times the size of the installed RAM, so if someone only had 128 MB of RAM, it would be a waste of hard disk space to make the swap area any larger than  400 MB.
At the same time, swap are is _critical _in a Linux computer with only 128 MB of RAM.  I have an older computer running here right now that has 128 MB of RAM at the moment. It really needs all the swap area it can get.  When that old computer was new it only had a 6.0 GB hard disk in it! That was considered huge ten years ago I would imagine. Deciding whether to sacrifice a 'whopping 400 MB' of a precious 6.0 GB would have been cause for some concern and  deliberation. 

Not so long ago it was quite a lot more complicated to resize partitions once they were made too. Now it's possible to resize partitions easily with GParted Partition Editor in Ubuntu or with a [GParted -- LiveCD]("http://gparted.sourceforge.net/"). 

1.0 GB for swap should be fine.

Regards, Herman

---

### Post by superhaus on 2007-12-21
Thank you.

Yes, the idea is to have a large (60GB) partition that will share data between both OSes. I was excited to see that Ubuntu supports NTFS now which makes this a lot easier.

As far as /home is concerned, should I make that a separate partition or not?

---

### Post by forestpixie on 2007-12-21
if you're going to be keeping your data on a separate shared partition as you've said - don't worry about home, just go with the one that'll get made inside / - it'll just have your ubuntu conig files in

---

### Post by logos34 on 2007-12-21
> **Herman said:**
> [code]You would never need a swap area larger than 1.0 GB. I just make all mine 1.0 GB because it's a good round number. The size of the swap area is not so critical in most new computers nowadays. WIth over 1.0 GB of RAM your swap area won't likely even be used, but it doesn't matter anyway, because there are such large hard disks on the market, that no-one even notices the allowance of a whole 1.0 GB for a swap area.

Not so long ago, when most computers might have had 64, 128, 256 or up to 512 mb of RAM, the amount fo swap area to allocate was a hot topic here in Ubuntu web forums.
I have read that most computers can't utilize a swap area of more than about three times the size of the installed RAM, so if someone only had 128 MB of RAM, it would be a waste of hard disk space to make the swap area any larger than  400 MB.

At the same time, swap are is _critical _in a Linux computer with only 128 MB of RAM.  I have an older computer running here right now that has 128 MB of RAM at the moment. It really needs all the swap area it can get.  When that old computer was new it only had a 6.0 GB hard disk in it! That was considered huge ten years ago I would imagine. Deciding whether to sacrifice a 'whopping 400 MB' of a precious 6.0 GB would have been cause for some concern and  deliberation. 

Interesting...glad you set the record straight, Herman.  (although wouldn't the exception be video editing and graphics design?)  I recently shrank my swap down a few hundred megs because I have never, ever seen it use more than like ~350 mb.  And with ram dirt cheap these days seems everyone is loaded up with 2GB+, so they'll probably never even use the swap, let alone all of it, unless they hibernate or have 50 apps open simultaneously.  Like you said it the huge size of disks that make it easy to toss off one or two gigs space for swap.

---

### Post by Herman on 2007-12-21
:) Yes, logos34,
The quickest way to see how much of your memory and how much of your swap area is in use at any time is to use the 'top' command, (as you probably know already, but for the benifit of new users...).
I imagine it would be interesting to open some large files in video editing and graphics design programs and then watch what happens in 'top' and then decide if more swap area will be needed.

In my old 'Book PC', (the computer I have with 128 MB of RAM, I only have a couple of terminal windows open right now, one with a man page open and the other for the top command. It shows,
```
Mem: 124972K total   91460k used   33512k free,   2956k buffers
Swap: 176672K total    36720K used   140300k free   27216 cached 

```I don't know exactly how the operating system decides what data will be stored in the memory and what can be directed to the swap area,. As I understand it, the swap area is like a 'slow lane' for the memory, and it's still a good idea to have one even if we think we don't need it. As you can see, my system in the above example did use some swap area even though the main memory isn't full yet. I guess the stuff in the swap area is what the system decided won't be needed in a hurry, leaving some spare room in the memory modules for shuffling something else around quickly.

---

### Post by logos34 on 2007-12-21
> **Herman said:**
> ...As I understand it, the swap area is like a 'slow lane' for the memory, and it's still a good idea to have one even if we think we don't need it. As you can see, my system in the above example did use some swap area even though the main memory isn't full yet. I guess the stuff in the swap area is what the system decided won't be needed in a hurry, leaving some spare room in the memory modules for shuffling something else around quickly.

That's how I understand it too.  I think it puts the least active processes in the swap--it will never load up the ram more than around 80% in my experience (depends on the swapiness setting too).  Maybe I'm just lucky because even on the little ram I have (512) I routinely have ten to a dozen apps/windows open at a given time and I rarely get hard drive thrashing.

---

