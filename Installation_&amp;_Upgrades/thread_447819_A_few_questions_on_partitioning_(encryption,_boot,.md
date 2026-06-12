---
title: "A few questions on partitioning (encryption, boot, etc)"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Xbehave on 2007-05-18
im thinking of upgrading to feisty fawn(7.04) and i figure now will be a good time to sort out my partitions.this is what im thinking of setting up:

hard drive 1:(faster sata drive)
boot partition for grub (would 48k be big enough?)
swap 1(512k)
root partition(will 10G be enough as i intend to be compiling a lot more from source and running alot of stuff squid, web stuff + desktop stuff + science stuff)(encrypted this deniabilty isn't needed tho)
home partition(very large)(encrypted with deniability on certain parts)
hard drive 2:(slower pata drive)
boot partition for grub (id like to be able to run a system with either drive missing)
swap 2(512k)
windows partition(about 20G)(NTFS)
empty partition to test stuff(about 20G)

my questions:

encryption:
for my root partition loop-AES is the recommended method, is this right?
for my /home partition i was thinking of using truecryt or stegFS, which is recommended?
does anybody know what the performance hit is like with these?
for my swaps and temps would loop-AES allow a random key to be used on every boot?

other:
what format should my boot be?
is spreading out the swap file worth it?
what file system is best for root? i was looking at XFS or JFS but don't know what the effect will be on the root
im going to use JFS/XFS on my home because it will contain lots of small files, will this cause any problems?
if i put my /home in the same partition as / would i be able to use my /home from other boots?

sorry for the vast array of questions i have looked into these things but often my source has been closely tied to one of the products involved or old.help on any of the questions will be use full, im not hoping for a 100% expert on everything!

thanks in advance

---

### Post by tgm4883 on 2007-05-18
48k isn't big enough for your boot partition, i hear 100MB.  512k also seems pretty skimpy on your swap.  Although it is debatable and people use to (and still do, although I think its dumb) say 2X your amount of RAM.  Now if you had 4 GB of RAM I don't think you need 8GB of swap but thats up to you.  I always hover around 1GB usually because I think this is a safe number and HD space is cheap

---

### Post by Xbehave on 2007-05-18
oops i meant 512mb as i agree and go for 1gb of swap
i also meant 48mb as my current boot folder is 40 mb big

---

### Post by jerrylamos on 2007-05-18
I've got several Ubuntu installations.
They've all got two partitions:

Swap                       512MB at least, 1GB is O.K.

/                                everything else.

That's it.  I don't see any point in fragmenting Ubuntu.

Cheers, Jerry

BTW, I have one quad boot system, Windoze, Ubuntu 6.10, Ubuntu 7.04, Ubuntu partial 7.10.  The Ubuntu's really only need one Swap partition; whichever one is booted uses the same swap.  I find it handy having two Ubuntu's, one the current one that works and one to experiment with the next one down the pike.  It's easy to copy files between them.

---

### Post by tgm4883 on 2007-05-18
> **jerrylamos said:**
> I've got several Ubuntu installations.
They've all got two partitions:

Swap                       512MB at least, 1GB is O.K.

/                                everything else.

That's it.  I don't see any point in fragmenting Ubuntu.

having a seperate /home directory would help/make easier in saving your settings and files during upgrades.  It is one of the three partitions I have (swap, / , /home)


> **jerrylamos said:**
> 
Cheers, Jerry

BTW, I have one quad boot system, Windoze, Ubuntu 6.10, Ubuntu 7.04, Ubuntu partial 7.10.  The Ubuntu's really only need one Swap partition; whichever one is booted uses the same swap.  I find it handy having two Ubuntu's, one the current one that works and one to experiment with the next one down the pike.  It's easy to copy files between them.

They can use the same swap as long as you don't hibernate one then boot into the other.

---

