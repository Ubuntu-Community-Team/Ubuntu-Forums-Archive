---
title: "Will install from USB erase my drive?"
date: 2014-04-10
forum: Installation &amp; Upgrades
---

### Post by husseinmoussa on 2014-04-10
My laptop:
acer 5750G
i5
4GB RAM
500 HDD

I have win7 (on partition C) and linux mint installed ***inside*** it (on partition D).

I have my HDD partitioned into: C (30 GB) and D (The rest)

I just made a USB Xubuntu 13.10 to try. My questions are:

If I wanted to install:
[CENTER][SIZE=3]1- Can I choose the partition D to install it on? and if I can.

2- Will the installation erase the whole partition?

3-Is there a way to install xubuntu (13.10 or 12.04.4) ***inside*** windows?[/SIZE]


============================================================================
I know they are noob questions, not saying that I'm an expert here, but sometimes you just can't find the exact answer you're looking for.
I hope I can find my answer.
============================================================================

**[SIZE=4]And please, explain as simply as possible[/SIZE]** :)
[/CENTER]

---

### Post by monkeybrain20122 on 2014-04-10
What do you mean installing inside Windows? If you mean WUBI the answer is no. It is no longer supported and frankly, if you want to use Ubuntu, at least have the commitment of giving it its own partition. Ubuntu is not a Windows software and is not meant to be run "inside" Windows. It deserves equal treatment.

WUBI was more of a marketing gimmick IMO in the old days when Ubuntu was unknown (and perhaps lacking in confidence) than a way to seriously explore Ubuntu and what it is capable of, it might have some useful purpose to expose Ubuntu to more people but IMO that time has long passed.

---

### Post by Devin_Carpenter on 2014-04-10
So you should be able to run Xubuntu just from your USB flash drive without having to actually give it a partition. Also, when and if you create a partition, you can only take space that is currently not being used. So if you wanted to put a partition of it on your D drive then you can just designate how many GB's of space you want it to have. If there is no free space on the D drive then you shouldn't try to partition Xubuntu on it.

If you want to try Xubuntu, just run it from a CD or the USB.

Hope that helped.

Edit: Said 'memory', meant 'space'

---

### Post by husseinmoussa on 2014-04-10
**First:**
*inside* windows is actually the exact expression that the iso uses when I run it.

**Second:**
I didn't mention anything about wubi.

**Third:**
Please understand that the world is full of simple users, like me, who don't have the "commitment" to try ubuntu. I came here because I read that ubuntu means something so humane and welcoming. I expect help rather than scolding.

Even if my questions sounded "offensive" (which I highly doubt they are!) you have to be patient with questions.
It might be offensive to programers or linux people to ask questions like mine. But they're well-intentioned.

A simple user asking such question usually knows nothing about the politics (and sometimes doesn't need to know!) behind anything related to the issues he's asking about or even his questions themselves! So please be patient with simple users.

But no hard feelings.

So you scolding me for not having full commitment still didn't give me a clear answer about the possibility to install the Xubuntu on D without erasing it? (Remember I didn't mention the word "wubi").

If you want to explain simply, please do.
Otherwise, I'll understand. And thanks for your comment.

---

### Post by husseinmoussa on 2014-04-10
> **Devin_Carpenter said:**
> So you should be able to run Xubuntu just from your USB flash drive without having to actually give it a partition. Also, when and if you create a partition, you can only take space that is currently not being used. So if you wanted to put a partition of it on your D drive then you can just designate how many GB's of memory you want it to have. If there is no free memory on the D drive then you shouldn't try to partition Xubuntu on it.

If you want to try Xubuntu, just run it from a CD or the USB.

Hope that helped.

Thanks :)

So this means if I continued with the installation process from the USB. I should just continue and create a partition from the space from D. Great! :) That's really great! :)
I didn't know it goes like that :) I do have plenty of space from D.

Thanks Devin :) I'll go do it now! :D :)

---

### Post by Mark Phelps on 2014-04-10
You need to know that "memory" has nothing to do with "disk space" -- so any advice that talks about memory in terms of disk space allocation isn't even using correct terms!

IF you're serious about installing Ubuntu in a dual-boot setup with Win7, then BEFORE you do that, be sure to read through the details below.  Some serious preparation is needed and if you don't take the time to do that, you can easily end up in a situation that leaves you with a nonworking PC.

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, and you are using MBR partitioning (not GPT) that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by oldfred on 2014-04-10
Ubuntu has to have its own formats for its partitions. It will read & write NTFS partitions just fine, but usually better not to have it set to write into Windows system partition as you can accidentally create Windows issues. The Linux NTFS driver is like turning on all the hidden files & folders that Windows tries to protect you from. 

Linux has to have its formats as it was designed originally as a multiple user  system. So you assign ownership & permissions to all Linux partitions. Default install sets that up for you for default partitions. Windows formats do not support Linux ownership & permissions so cannot be used. Part of the advantage of that is it is more difficult for rogue software to gain access to your system. You explicitly have to allow it, not saying some software may not try to convince you to install it and you still have to be careful of that.

If you just want to test Ubuntu, you can use the live installer from a flash drive. Not as fast as on your hard drive but you can and should try it. It helps to know if you will have issues with your specific hardware. With a flash drive you also can turn on persistence which lets you save some types of things, not not system related software.

From live installer, in a terminal you can post this so we can see if you have used all 4 partitions. Since Linux has so many choices on gui/desktops, we usually ask you to use terminal as that is the same in all versions. You can just copy & paste so should not be a huge issue to use.

sudo parted -l

---

### Post by husseinmoussa on 2014-04-11
To be honest, I'm trying to understand your advice.

Here's what I understood:

1- I understand that it needs preparation and that's what I'm trying to do. It's really good that I find help here. I'm grateful. :)

2- I do have more than 100 GB free on D partition. so My question is: Will the setup, from the USB onward, be able to take this free space and partition it? even though it is assigned to the partition D? Because as far I as understand (Maybe this is windows mentality and that's why I'm actually posting this whole topic) while partitioning, One needs to, like, de-partition the partition first then try to divide the space into new partitions which of course means erasing all the data on it.

My simple question is:

Is the setup going to do the same thing? or it just takes the space and creates a new partition for itself, I mean practically, regardless of if it's being a windows mentality or linux mentality.


I'm grateful for all the theoretical explanation. I'm really grateful :) But I'm a simple (not stupid) guy with very simple yes or no questions:

[SIZE=3]1- Can I choose the partition D to install it on? and if I can.

2- Will the installation erase the whole partition?

3-Is there a way to install xubuntu (13.10 or 12.04.4) ***inside*** windows?[/SIZE]

Regardless if the questions sound so naive and you feel the need for more explanation first before giving the direct answer. I do understand your point of view because sometimes when I answer things I feel the need to explain every little bit of detail for people before giving them the simple "yes" or the simple "no".

I've read a few articles about how linux sees drives and partitions differently. But practically, What would it do to the partition. That's my question and I just need simple direct answers.
Please if my inquiry isn't clear to you, ask me questions, so I can clarify my question more and more.

[CENTER]> [SIZE=3]**I have some space in the D and I need to install xubuntu on it without removing the whole D. can the linux setup "use" the space without "formatting" or "removing" it? Did anyone try that before? and did it work?**[/SIZE]

I hope I'm not offending any one with my questions or anything like that. I have a feeling (from your comments) that I don't understand the way linux works. although I read a few articles and tried the systems myself. Please if you think that there's something I'm missing. recommend some articles to read on certain topics so I can read later.
**But please keep in mind that I need answers for my questions first :)**
Thanks in advance and I'm really grateful for the help from each and every one of you :)
[/CENTER]

---

### Post by mastablasta on 2014-04-11
> **husseinmoussa said:**
> My laptop:
[SIZE=3]1- Can I choose the partition D to install it on? and if I can.

2- Will the installation erase the whole partition?
[/SIZE][SIZE=3]

yes and yes.

however, you can "carve" an unformated disk space (25-30 GB should be more than enough, min. recomended space is 8Gb though) using windows disk manager from your D partition. and then install xubuntu there. that will keep the rest of the data safe. make sure you defragment the disk and run chkdsk (checg disk) before changing partition.

> 
3-Is there a way to install xubuntu (13.10 or 12.04.4) ***inside*** windows?[/SIZE]


yes. see here how to do it: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

i followed this guide and i have 12.04 installed on a much weaker single core mashcine. it's running smoothly. i dedicated 8 GB hard disk to it. i need to clean kernels once in a while but it's good enough for testing some things.

---

### Post by sudodus on 2014-04-11
> **husseinmoussa said:**
> 

[SIZE=3]1- Can I choose the partition D to install it on? and if I can.

2- Will the installation erase the whole partition?

3-Is there a way to install xubuntu (13.10 or 12.04.4) ***inside*** windows?[/SIZE]


Hi husseinmoussa :-)

1 - Partition D will get another name in linux. Anyway, ***yes***, you can use that partition.

2 - ***Yes***, if you select the whole partition for linux, its content will be erased (or overwritten).

3 - ***Yes***, a wubi installation, but we do ***not*** recommend that, as you have already seen in previous replies. Or with ***Virtualbox***, as suggested by *mastablasta*. Virtualbox is much better than wubi.

* - I suggest (as also in previous replies) that you ***shrink that D: partition and use the space***, that is made unallocated (free), to create a large partition for the root file system of Xubuntu and a small partition for swap (virtual memory).

This means that you will create a dual boot system, that can boot Windows and Xubuntu.

---

### Post by husseinmoussa on 2014-04-11
> **mastablasta said:**
> [SIZE=3]

yes and yes.

however, you can "carve" an unformated disk space (25-30 GB should be more than enough, min. recomended space is 8Gb though) using windows disk manager from your D partition. and then install xubuntu there. that will keep the rest of the data safe. make sure you defragment the disk and run chkdsk (checg disk) before changing partition.




yes. see here how to do it: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

i followed this guide and i have 12.04 installed on a much weaker single core mashcine. it's running smoothly. i dedicated 8 GB hard disk to it. i need to clean kernels once in a while but it's good enough for testing some things.

Thanks so much :)

specially for the virtualbox bit. I read about this VM thingy. But the explanation is great :) thanks :)

---

### Post by husseinmoussa on 2014-04-11
> **sudodus said:**
> Hi husseinmoussa :-)

1 - Partition D will get another name in linux. Anyway, ***yes***, you can use that partition.

2 - ***Yes***, if you select the whole partition for linux, its content will be erased (or overwritten).

3 - ***Yes***, a wubi installation, but we do ***not*** recommend that, as you have already seen in previous replies. Or with ***Virtualbox***, as suggested by *mastablasta*. Virtualbox is much better than wubi.

* - I suggest (as also in previous replies) that you ***shrink that D: partition and use the space***, that is made unallocated (free), to create a large partition for the root file system of Xubuntu and a small partition for swap (virtual memory).

This means that you will create a dual boot system, that can boot Windows and Xubuntu.


Absolutely wonderful! :) Now I see the big picture :) and I can choose :)

I guess I'll go with the Virtualbox, seems safer for now. :) Plus I have mint installed already. I'll be greedy and have a third system installed on my machine! :)

But thanks everyone for all the help and the tips and the links and everything really appreciate it :)

---

### Post by Devin_Carpenter on 2014-04-14
> **Mark Phelps said:**
> You need to know that "memory" has nothing to do with "disk space" -- so any advice that talks about memory in terms of disk space allocation isn't even using correct terms!

Good call Mark.

I was using the terms in a very obvious context so I wasn't thinking of the terminology mattering as much.

---

