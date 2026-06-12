---
title: "Potential Ubuntu User - Installing on a separate hard drive"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by Sebastian12 on 2008-07-19
Hi,

I successfully copied the ISO file and tried out Linux on my laptop.  I'm extremely impressed and I'd like to fully install it, but I have a few questions first.

1. I'm almost already sure of the answer here but I need clarification: It will go much faster after being fully installed, right?  I have a dual-core processor and 2 gigs of RAM so my computer's up-to-date.  It would just be a little annoying if I had to wait a second every time I clicked on a menu command.

2. My laptop has 2 internal hard drives, and one is completely empty.  When I got to step four of installing it, I was given the option of installing it on the one that is mostly full of all my current files and Windows Vista or installing it on the empty one.  The only problem was that I couldn't tell which one was which.  It didn't say which hard drive had more files on it, it only stated the type and full file capacity of each hard drive, both of which is the same.  How can I differentiate?

3. To ensure myself, if something goes wrong on a separate hard drive, it won't affect/delete/mess up anything on the other one, right?  And if I want to remove Linux on that hard drive, is it easy and fully removable?
[U]
Thanks in advance[/U]! I'm exited to try out something besides Windows but want to proceed with caution.  Oh, and sorry if this belongs in a different category.  I'm new here.

---

### Post by Pumalite on 2008-07-19
This will help:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by ugm6hr on 2008-07-19
1. It is faster once installed.  The LiveCD runs a compressed image from a CD drive, whereas, once installed, the image is uncompressed and read from a HD.

2. Difficult, but not impossible.  I would suggest manually formatting and partitioning the HD for Ubuntu using GParted (Partition Editor); that way you will be able to identify the HD with the appropriate partitions using the "Manual" installation option.

3. Sort of.  The Ubuntu bootloader (called Grub) will need to be installed on the Ubuntu HD (not the Windows HD) to ensure that this is true.

The easiest way is actually to manually disconnect the Windows HD internally, install Ubuntu on the other HD, then plug the Windows HD back in.  This will ensure that everything works as you want.  After this, you just need to select the Ubuntu HD as primary boot device in BIOS, and make a small change to the /boot/grub/menu.lst file to allow Windows to boot without needing to manually change BIOS each time.

---

### Post by Sebastian12 on 2008-07-19
Alright, I generally get the idea but do I have to make Ubuntu the primary OS?

When I turn on my computer how will it function?  Will I have to change something technical or enter some code?

It seems that all of the instructions aren't fully laid out, and I have to figure this out on my own.  I'm just scared it'll override Windows when I may choose to go back and by then it'll be too late, where I have to go through Linux every time I have to use Windows.

---

### Post by Pumalite on 2008-07-19
If you follow the prior post; all you have to do is change the boot order of the hard drives in BIOS to boot Ubuntu. It will be separate from your Windows. You can also boot Ubuntu with Super Grub.

---

### Post by ugm6hr on 2008-07-19
> Alright, I generally get the idea but do I have to make Ubuntu the primary OS?
No.  Ubuntu will install itself as default on the Ubuntu HD.  Your options post-installtion:
1. Set BIOS to make Windows HD 1st boot device: this will default to Windows, and would require manual change in BIOS every time you want to boot Ubuntu.
2. Edit menu.lst file (to make Windows default) and make Ubuntu HD 1st boot device: this will bring up your boot options at each boot, giving you 10 seconds (customisable duration) to choose between Windows / Ubuntu, with Windows as default.

> When I turn on my computer how will it function?  Will I have to change something technical or enter some code?
See above - depends on which option you choose.

> It seems that all of the instructions aren't fully laid out, and I have to figure this out on my own.  I'm just scared it'll override Windows when I may choose to go back and by then it'll be too late, where I have to go through Linux every time I have to use Windows.
True. If you don't understand what you are doing, then get someone else to do it for you.  Although, as I said - if you disconnect the Windows HD before installing Ubuntu, there is no risk (and the instructions are simply to install to the only HD left).

---

### Post by Sebastian12 on 2008-07-19
Alright... I've studied everything and I've found out how to identify the specific hard drive.  Just a few specifics...

When one checks off the hard drive and selects something like "swap" or "journalistic storage" (may be something different), then it's only going to partition and commit a process on that hard drive, not the other one, right?

Also, what do all those things like "swap" mean?  Which one am I supposed to choose to effectively install Ubuntu?

---

### Post by ugm6hr on 2008-07-20
> **Sebastian12 said:**
> When one checks off the hard drive and selects something like "swap" or "journalistic storage" (may be something different), then it's only going to partition and commit a process on that hard drive, not the other one, right?
Where are you doing this?  In Gparted (partition Editor)?  If so - you specify the HD and the size / location of each partition.

> Also, what do all those things like "swap" mean?  Which one am I supposed to choose to effectively install Ubuntu?
Swap is for swap partitions - which are used for virtual RAM.  Unlike Windows, Linux requires a separate partition for virtual memory.  It is recommended to be 1.5-2x RAM size, with maximum about 1GB (unless you use suspend to RAM).

To install Ubuntu, you need 1 "swap" partition (sized as above) and at least 1 "ext3" partition (minimum 10GB) for "/".  However, it is better to have 2 "ext3" partitions with 1 swap as above) though - 1 for "/" (about 8-10GB is plenty) and another for "/home" (as much as you want for personal files).  You can use the "Manual" installation option to specify the partitions and their "mount points" (e.g. "/", "/home", "swap").

Remember to use the "Advanced" tab to specify which MBR (HD) Grub is installed on to.

---

### Post by Sebastian12 on 2008-07-20
I am using the partition editor that's included with the default installer, but the problem is that now whenever I partition a 1GB size of "swap area" is says that it's "too small size" or something to that effect even though the hard drive is completely formatted.

Is there any place I can get detailed instructions or a walk through on the Partition editor?  It seems like I would use it to make a swap area and then what?  Why doesn't it give me more information of the HD so I don't make a mistake?  After I make a swap area how to I make an ext3 partition?  Nothing seems to be fitting correctly... I think I'm missing something.

---

### Post by Pumalite on 2008-07-20
This is a good guide:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by Sebastian12 on 2008-07-20
I already checked the psychocats.net guide and it's not detailed enough.  It just gives suggestions for how to partition a hard drive but doesn't walk you through the process whereas I know exactly what I want but it isn't allowing me to do these things in the partition editor.

There's no guide to explaining what I see after I click "Manual" and then the options that come up?

---

### Post by Sebastian12 on 2008-07-20
Success!

I found out how to do it on my own by looking through everything you've all gave me, thanks so much!  (I ended up doing about 10 Gigs Ext3, a swap area of 1 Gig at the end, and the rest an Ext3 / home.)

It seems so interesting, now I need to figure out how to get the wireless working on it though (I'm typing this in Vista).

It's easy to switch between the two so now I can go to Linux to configure stuff but if it doesn't work out I can just come back to Windows when I need to.

:) Thanks everyone!

---

