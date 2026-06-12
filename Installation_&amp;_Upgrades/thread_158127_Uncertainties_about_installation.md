---
title: "Uncertainties about installation"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Rhapsody on 2006-04-10
Alright, I've decided I want to migrate over from Windows XP to Kubuntu Linux (various reasons, dislike of Microsoft primary among them) and I'm fairly confident that it will go smoothly, but some uncertainties have stalled my plans for the last two weeks.

Firstly, I want to dual-boot for a while to ensure that everything works fine under Kubuntu before switching for good. Now I have two drives to install on, C (a 74.5GB FAT32 drive with 25.6GB free, Windows and most of my applications are installed here) and E (a 232GB NTFS drive with 144GB free, various data that I'd very much like to keep is on this). My plans are to install Kubuntu on a new partition on drive C, after I've checked for errors and defragmented of course.

Now, will I be able to keep all of the data on my current partition or will I be seeing the last of it if I try this? I can probably get around this if that will happen, but I really need to know incase I'm looking at a working plan here.

Also, as an aside between my two questions, will I be able to make a swap partition on my NTFS drive or will it have to go on my FAT32 drive?

Second, my future plans are to kill off Windows XP entirely in the future and have my PC running solely on Linux. My plans in the future are to end up with two or three partitions on my main drive. Now, will I be able to delete my old Windows XP partition and expand the Kubuntu partition to fill the space left, or will I have to start the partition from scratch again?

This is a more minor question since I anticipate starting over after having experience with Linux, but it's still something that's bugging me.

I hope to have answers soon, after which I hope I can finally start making progress on this project.

---

### Post by aysiu on 2006-04-10
[QUOTE=Rhapsody]
Firstly, I want to dual-boot for a while to ensure that everything works fine under Kubuntu before switching for good.[/quote] Even before that, you should use a live CD to see how well Kubuntu detects your hardware *and* to familiarize yourself with the interface (see if this is what you really want to install and configure). > Now I have two drives to install on, C (a 74.5GB FAT32 drive with 25.6GB free, Windows and most of my applications are installed here) and E (a 232GB NTFS drive with 144GB free, various data that I'd very much like to keep is on this). My plans are to install Kubuntu on a new partition on drive C, after I've checked for errors and defragmented of course.

Now, will I be able to keep all of the data on my current partition or will I be seeing the last of it if I try this? I can probably get around this if that will happen, but I really need to know incase I'm looking at a working plan here. Yes, but you should back up your data anyway, especially since you don't know what you're doing.

This will help you dual-boot:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

> 
Also, as an aside between my two questions, will I be able to make a swap partition on my NTFS drive or will it have to go on my FAT32 drive? You can carve a swap out of either.

> 
Second, my future plans are to kill off Windows XP entirely in the future and have my PC running solely on Linux. My plans in the future are to end up with two or three partitions on my main drive. Now, will I be able to delete my old Windows XP partition and expand the Kubuntu partition to fill the space left, or will I have to start the partition from scratch again? You can expand at the end of a partition but not  the beginning. If Windows is *before* Kubuntu, you can create a new data partition out of it, but you can't just add it to the Kubuntu partition.

---

### Post by Rhapsody on 2006-04-10
[QUOTE=aysiu]Even before that, you should use a live CD to see how well Kubuntu detects your hardware *and* to familiarize yourself with the interface (see if this is what you really want to install and configure).  Yes, but you should back up your data anyway, especially since you don't know what you're doing.[/QUOTE]
Well I already tried an Ubuntu live CD and it seemed to detect everything without any trouble, but then I decided I prefered KDE over GNOME and made a Kubuntu install CD. I assume there'll be no difference in hardware compatibility, and I'm sure I'll get accustomed to KDE in time. It's supposed to be easy to use, and I have a knack for getting to grips with new interfaces very easily.

[QUOTE=aysiu]This will help you dual-boot:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)[/QUOTE]
That looks very helpful. There's some stuff I may not have thought about on there. Thanks.

[QUOTE=aysiu]You can carve a swap out of either.[/QUOTE]
I'd probably want to use my larger drive then. It's newer and has oodles of free space.

On a somewhat related subject, my plan for this NTFS drive is to keep it around unmodified and use Captive NTFS for writing new data to it. How reliable and easy a solution is this likely to be? Bear in mind that although I can backup my current partition to this drive, there's far too much data on my large NTFS drive to effectively backup to anywhere (there's always the option of DVD-Rs, but I'd like to not be spending all that money).

[QUOTE=aysiu]You can expand at the end of a partition but not  the beginning. If Windows is *before* Kubuntu, you can create a new data partition out of it, but you can't just add it to the Kubuntu partition.[/QUOTE]
Right, and Windows will almost certain end up before Kubuntu. Is there any way around this? I can easily make the Kubuntu partition 20GB in size, which is enough for installation and a load of applications, but I'd much rather have the entire drive for that partition at some point.

---

### Post by PriceChild on 2006-04-10
[quote=aysiu]You can expand at the end of a partition but not  the beginning. If Windows is *before* Kubuntu, you can create a new data partition out of it, but you can't just add it to the Kubuntu partition.[/quote]

Today i managed to delete my windows partition, then copy my ubuntu partition into the space before it, delete the origional ubuntu partition, then expand the new ubuntu partition all the way to the end of the hard drive. After that i just needed to spend a while sorting out the boot/grub/menu.lst

I didn't worry too much as i haven't got too much vital to keep as it was all backed up, and my windows partition was bigger than my ubuntu which made it easy. However it took several attempts to sort out the grub menu.lst because of my silly typos :) All this was done in the Live Cd

Thought i'd let you know it is possible :)

Pricey

---

