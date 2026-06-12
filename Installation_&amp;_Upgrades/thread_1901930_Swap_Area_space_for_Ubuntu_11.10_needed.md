---
title: "Swap Area space for Ubuntu 11.10 needed ?"
date: 2011-12-29
forum: Installation &amp; Upgrades
---

### Post by hujal on 2011-12-29
Hey,

I have windows 7 and I partitioned the disk space (allocated 50GB) to install ubuntu 11.10. 
While installing Ubuntu 11.10 on the partitioned space, do I need to partition it once again  and allocate some space for swap area? 

If yes, then how much space should I allocate? 

Currently RAM in my laptop is 1G but I plan to upgrade it to 3G.

Thanks in advance for the help!

---

### Post by kerry_s on 2011-12-29
nope, with 1gb your good. you could just in case add 1gb swap. it's not like you can't spare the space.

---

### Post by Elfy on 2011-12-29
If you plan to hibernate I would allocate as much as you intend to upgrade it to.

Whne you say you partitioned the space - I assume you mean the empty space is there - windows won't format to a suitable type - you'll not install in NTFS.

---

### Post by mcduck on 2011-12-29
I recommend leaving the space you intend to use for Ubuntu as unpartitioned free space. You can't format the partitions from Windows anyway, as it doesn't support Linux filesystems, and that will also allow you to simply tell Ubuntu's installer to use the unallocated space and it will create all the partitions automatically for you.

---

### Post by hujal on 2011-12-29
> **mcduck said:**
> I recommend leaving the space you intend to use for Ubuntu as unpartitioned free space. You can't format the partitions from Windows anyway, as it doesn't support Linux filesystems, and that will also allow you to simply tell Ubuntu's installer to use the unallocated space and it will create all the partitions automatically for you.


Thanks for your response. Currently I've alerady formatted it as NTFS. Win 7 has a wizard which helps you do it. Considering this, how should I proceed?

---

### Post by hujal on 2011-12-29
> **kerry_s said:**
> nope, with 1gb your good. you could just in case add 1gb swap. it's not like you can't spare the space.

Thanks for your response. I've already ordered the RAM so will be upgrading to 3GB in total. (1 - already present + 2GB - ordered)  I read somewhere that if I create a swap space, performance will degrade if RAM > 1 GB.

Is that true? Please help.

---

### Post by mcduck on 2011-12-29
> **hujal said:**
> Thanks for your response. Currently I've alerady formatted it as NTFS. Win 7 has a wizard which helps you do it. Considering this, how should I proceed?

Just delete the partition. :) Ubuntu's installer will detect the unpartitioned space and do everything for you.

And no, having much swap will not degrade your performance. Swap is only used when it's needed, in which case you would of course get bad performance (since hard drives are much, much slower than RAM is) but that's still better than what you'd get without the swap in the same situation ("out of memory" error or a crash).

If you want to be able to suspend the machine, you'll need as much swap space as you have RAM. If you don't need suspend, then something around 512MB-1GB of swap should be enough, with 4GB of RAM it's unlikely your system would ever need the space for actual swapping.

---

### Post by hujal on 2011-12-29
> **mcduck said:**
> Just delete the partition. :) Ubuntu's installer will detect the unpartitioned space and do everything for you.

And no, having much swap will not degrade your performance. Swap is only used when it's needed, in which case you would of course get bad performance (since hard drives are much, much slower than RAM is) but that's still better than what you'd get without the swap in the same situation ("out of memory" error or a crash).

If you want to be able to suspend the machine, you'll need as much swap space as you have RAM. If you don't need suspend, then something around 512MB-1GB of swap should be enough, with 4GB of RAM it's unlikely your system would ever need the space for actual swapping.

Thanks a lot! I shall proceed as you've said, but just so that I have understood correctly 
"Ubuntu's installer will detect the unpartitioned space and do everything for you."

So original disk space is 130GB on which Win 7 installed. I don't do anything to it.
Just install Ubuntu and while doing so, select the option: 

"Use the largest continuous free space"  ? Would it automatically partition the 130GB and do everything for me...

Thanks again in advance ! Help appreciated...

---

### Post by efflandt on 2011-12-29
Swap is not necessary to suspend, only to hibernate.  Suspend just puts RAM, cpu and whatever else in a low power state, but keeps RAM alive.  Hibernate saves RAM to swap and shuts down completely.  So you only need swap at least as large as RAM if you want to hibernate.

My 8 GB desktop has no swap at all, because waking from suspend or hibernate takes longer than cold boot from SSD (maybe something to do with video drivers).

---

### Post by UbuNubi on 2012-01-07
I just signed up and decided to do a search instead of start a new topic on this. This is my issue as well. I currently have Windows 7 and I want to create a partition and install Ubuntu using Wubi. I've read a lot of sites and I've watched a lot of youtubes about it. I see people who simply make the partition and do it and some who say  you have to make the partition for Ubuntu AND a partition for "swap  space". So I was wondering if it's even necessary.

I was planning on getting an ssd and cloning what I hope to be my win 7/ ubuntu dual boot operating systems, but I may have to wait a bit longer to do it because my win 7 os and applications alone are about 60gb and I wanted to give room to grow for both OS' with apps (maybe 100gb for Win7 & 50 for Ubuntu). I planned on getting a 128gb ssd, but that doesn't seem like it will be enough and those things are costly.

But anyway, for now I have a 1.5 tb hard drive with 16gb of ram. Do I need to do this swap space thing? And if so, I'm hoping the Ubuntu installer(wubi) will know how to go about all that because I have no idea what I'm supposed to do with the swap space. 

Thank you.

---

### Post by kerry_s on 2012-01-07
just create 1 partition & point Ubuntu to it, it will split it up to what's needed

---

### Post by UbuNubi on 2012-01-07
Thanks Kerry!

---

### Post by bcbc on 2012-01-07
Ubunubi, if you install with Wubi it won't do anything with your partitions. Wubi uses a virtual disk.

If you want a traditional dual boot with a separate partition for swap you need to install from an Ubuntu cd/usb.

---

### Post by UbuNubi on 2012-01-11
Thanks BCBC.

I went ahead and installed using a disc. Everything looks fine. Only thing that makes me wonder is why my fan is always blowing when I'm on Ubuntu. My computer is perfectly silent when in Win 7....

---

### Post by bcbc on 2012-01-11
> **UbuNubi said:**
> Thanks BCBC.

I went ahead and installed using a disc. Everything looks fine. Only thing that makes me wonder is why my fan is always blowing when I'm on Ubuntu. My computer is perfectly silent when in Win 7....

I suggest you create a new thread "Why is my fan always running". List your full specs (brand/model/graphics card(s) etc.) and the release of Ubuntu you are running. That will help to identify a solution if there is one.

---

### Post by UbuNubi on 2012-01-11
Ok, BcBc, will do!

---

