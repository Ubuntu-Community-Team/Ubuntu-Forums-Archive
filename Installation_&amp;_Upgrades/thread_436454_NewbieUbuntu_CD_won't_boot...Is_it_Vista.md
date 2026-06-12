---
title: "Newbie/Ubuntu CD won't boot.../Is it Vista?"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by Brightbelt on 2007-05-07
Hi, 
I'm a real Newbie who is maybe on the verge of trying Linux for the first time.  I'm not the geekiest guy but I'm fairly bright. I learn steadily but surely.

So I downloaded Ubuntu Feisty Fawn and I made a CD of it. I am on a Gateway M675x Laptop upon which I installed Vista Home Premium 32-bit as an experiment. Actually Vista is running fine -  this is also an older Pent4 laptop that I can use for experimentation, so I'm thinking of using it to try Linux.

For some reason, my CD won't boot into an install mode or at all really - I've tried setting my F10 settings to have the laptop boot from a CD, but Nada. If I go to my Vista desktop and go to the Rom drive in My Computer, the computer doesn't respond correctly when I double click the Rom drive with the Ubuntu CD.

Is Vista keeping something from happening here? 

Also I might want to partition my drive to keep Vista in case this goes awray, but I don't have a clue how I would do that....

I appreciate any suggestions or guidance, Thanks, Frank

---

### Post by confused57 on 2007-05-07
Is this how you burned your iso "as an image" to cd?:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
main points are to do a md5sum on the iso, burn as an "image"(not data or bootable cd), and at a low speed(8x or less).

Vista wouldn't prevent your Ubuntu install cd from booting...if you get your Ubuntu cd working, make sure not to use the Ubuntu install cd to resize your Vista partition, use Vista's builtin partitioner.

Here's an excellent guide for installing with the Desktop cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
just don't resize Vista with the install cd...

---

### Post by Brightbelt on 2007-05-08
Thanks for the tips...Could you tell me, does the Vista Partitioner automatically come up as
option during the install? Or is there a special way I need to access it?

Many Thanks, Frank

---

### Post by confused57 on 2007-05-08
> **Brightbelt said:**
> Thanks for the tips...Could you tell me, does the Vista Partitioner automatically come up as
option during the install? Or is there a special way I need to access it?

Many Thanks, Frank

I think you'll need to boot into Vista & use Vista's partitioning tool:
[http://www.pro-networks.org/forum/viewstory.php?t=78111](http://www.pro-networks.org/forum/viewstory.php?t=78111)

Once you free up "unallocated" space for Ubuntu after resizing Vista, then boot up with the Ubuntu install cd & install on the freed up space.

---

### Post by Brightbelt on 2007-05-08
Ok, Yes That's done. I figured I'd need to partition with Vista First. Now....

the only problem is, I get part ways through the Ubuntu install and I get to the partition section where I choose where I want Ubuntu to go (I'm Not using Ubuntu to modify or create any partitions as you suggested) and I merely choose the partition I already prepared with Vista, and Ubuntu pops up a window and says "No root file system specified; complete this in the partition menu". 

But I already have the cursor highlighting the right partition and it has been formatted with FAT32 already. Why is Linux talking about a root file system? Is it because the partition drive letter is not C? (This partition happens to be named D:\)

Many Thanks for your continued help, Frank

---

### Post by Brightbelt on 2007-05-08
By the way, I am at least able to boot with the CD and have tinkered around on the Ubuntu Desktop.

It's kind of exciting ! I never thought I'd see Linux running on any of my machines....

I do appreciate any continued help on my above question. Thanks, Frank

---

### Post by confused57 on 2007-05-08
> **Brightbelt said:**
> Ok, Yes That's done. I figured I'd need to partition with Vista First. Now....

the only problem is, I get part ways through the Ubuntu install and I get to the partition section where I choose where I want Ubuntu to go (I'm Not using Ubuntu to modify or create any partitions as you suggested) and I merely choose the partition I already prepared with Vista, and Ubuntu pops up a window and says "No root file system specified; complete this in the partition menu". 

But I already have the cursor highlighting the right partition and it has been formatted with FAT32 already. Why is Linux talking about a root file system? Is it because the partition drive letter is not C? (This partition happens to be named D:\)

Many Thanks for your continued help, Frank
You might want to "play" around a little with the live cd, before you actually install.  While you're booted into the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"
this will show how your hard drive is currently partitioned...if you notice, Ubuntu will designate the partitions as sda1, sda2, etc...instead of Window's method, i.e. C:/, D:/, etc.   You will need to be familiar with how Ubuntu designates partitions when you do the actual install.  Also, Ubuntu uses ext3 filesystem type, it cannot be installed on a FAT32 filesystem ...however, the installer can reformat the partitions to ext3.

Here's an excellent guide for installing with the live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Since, you formatted the free space as FAT32 after resizing Vista, you will probably need the "Manual Partitioning" in order to delete the FAT32, then repartition.  You'll need a root partition, formatted as ext3, mountpoint as root (/), set the bootflag on...size could be all but about 1 Gb, which you'll set up as a swap partition, which is formatted as swap, mountpoint selected as swap.  Just make sure not to select format for your Vista partition. 

I would still suggest that you use the live cd for a little while, read through the forum, especially posts pertaining to installing or partitioning...once you feel comfortable, then go for the install.  Don't hesitate to ask if you have questions, before you install.

Added:  If you've already started installing that's fine...if you haven't, I'd recommend that you make the root partition a primary partition and the swap partition a logical partition.  You can have a limit of 4 primary partitions on a hard drive, so having an extended primary  partition will allow having several logical partitions within it.  Even if you make root & swap primary partitions, you should be able to create a 4th one as extended, if you ever needed to.

---

### Post by Brightbelt on 2007-05-08
Many Thanks for all your suggestions. I think the CD plan you gave is a very good idea - it takes a little while for these terms to become more comfortable etc. 

I'll be reading....Thanks !  Frank

---

### Post by confused57 on 2007-05-08
The installed Ubuntu should be significantly faster than using the cd, but it' still probably wise to use the live cd for a few days or however long you want, until you feel comfortable with it.
There's some good reading in this sticky in the "Beginner Section":
[http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

Here's a subsection in the above sticky, that might have some useful info:
[http://ubuntuforums.org/showthread.php?t=142716](http://ubuntuforums.org/showthread.php?t=142716)

I've really enjoyed my experiences with Linux and I believe you will too...I didn't even know what a partition was before I started using Ubuntu(Breezy5.10).

---

### Post by Brightbelt on 2007-05-09
Hi Confused57,
I just wanted to say Thanks! And what an excellent resource you were in helping me. 

I have already installed Ubuntu and I now have a dual boot situation with Vista. I've double-checked and I can say that I can successfully boot to both OS's just fine.

Again many Thanks,

Frank

---

### Post by gjtoth on 2007-05-09
> **Brightbelt said:**
> Hi Confused57,
I just wanted to say Thanks! And what an excellent resource you were in helping me. 

I have already installed Ubuntu and I now have a dual boot situation with Vista. I've double-checked and I can say that I can successfully boot to both OS's just fine.

Again many Thanks,

Frank

I just installed Ubuntu on a system belonging to a friend.  Same as you... dual-boot.  It was a brand, spankin' new machine with Vista "pre-installed".  Funny thing -- he has yet to boot into Vista!  When I last spoke with him he said, "After watching how slow it was after you FINALLY got it to work somewhere near right, why would I want to mess with it?  Ubuntu is much faster.  I'm more than happy just the way it is."

Hope you'll feel the same after a week or three... \\:D/

---

