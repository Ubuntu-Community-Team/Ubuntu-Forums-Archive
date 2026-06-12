---
title: "Partitioning/Mounting Problem"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by nyijedi on 2006-07-01
Hello everyone. I want to preface this by saying I did search for help on this problem (not only on this forum), but have not yet found a solution. I'm trying to install ubuntu 6.06 on an existing hard drive with windows xp already installed (dual boot).

When I initially tried to install ubuntu, I chose to manually edit the partition table. I first resized the existing NTFS partition (w/ Windows already installed) in partitionmagic. I then used the ubuntu partitioner to format the remaining, unallocated space of my HD in the following way:
1. Created a partition for ubuntu (ext3)
2. Created a partition for linux swap (linux-swap)
3. Created a partition of remaining space in FAT 32 for shared files

After specifying these partitions and moving on, I have problems on Step 5 when I am asked to prepare mount points. On this screen, I have one drop-down menu for "Mount Point", nothing is listed for "Size," and the drop-down for "Partition" is EMPTY. I've tried this numerous times, and get stuck at the same point every time.

Frustrated, I decided to use the option to simply use the largest amount of continuous space to install ubuntu. When I do this, everything installs fine until the very end, when I then get an error that GRUB could not be installed on hd0. The installation definitely tried doing something on my MBR, b/c after this happens, I am unable to load Windows (error loading OS) - I have to use GAG to then get into windows.

My first preference is to be able to format the partitions manually, so if anyone knows what I'm doing wrong, I would appreciate any input. Also, is there any way to install ubuntu w/o installing GRUB, since this is where I'm having a problem? Is there a way to simply use GAG as my boot loader instead of GRUB?

Thanks so much for all of the help.

---

### Post by rcarring on 2006-07-02
Might I suggest that you use partition magic to create a primary partition with fat32 file system after the XP partition, then leave the remaining space unallocated.

Boot with the Dapper alternate cd and let it use the free space. It should create two partitions, one for the /root and one for swap.

---

### Post by Lin-X on 2006-07-02
I also had problems with the partitioner during install. I had the swap and the ext3 partition but when I told the partitioner how to use them (as swap and as root), it would not continue. Instead, it kept telling me that I had not chosen anything for the root system. I would go back, do it again, and get the same result, around and around in a circle. Very frustrating! (I had other problems with that partitioner too, but we need not go into that now.)

This what I did to solve it: I exited the installer, found the partitioner in the System- Administration menu, fully prepared my partitions with it, and then ran the installer. For some reason, then everthing went fine. When I told the partitioner which partitions I wanted for root and swap, it worked great. I recommend that you use any other partitioner, external to the installer. The one on the live cd worked for me, but you could use Partition Magic or its Linux clone QTParted.

I wish you luck. You will not be disappointed once you get Dapper installed.

---

### Post by nyijedi on 2006-07-04
Thanks so much for the suggestions guys.  I'm going to give it all a try again over the next day or two, hopefully with a little more luck.

---

### Post by Globe_Trekker on 2006-07-31
> **nyijedi said:**
> Thanks so much for the suggestions guys.  I'm going to give it all a try again over the next day or two, hopefully with a little more luck.

So how did it go?  I had the same problem, and thanks to Lin-X's suggestion of partitioning in advance have now gotten to the point where it has my root and swap partitions set up, and my Windows partition has been labeled "/media/hda1".  I've heard stories of the installer screwing up the Windows MBR stuff so I'm still a little hesitant.  OK to proceed?

It's my sandbox PC (my daughters) anyway, so I guess it's no big deal if I hose her Windows.  I'm just a lazy man and don't want to redo it!  :)

---

