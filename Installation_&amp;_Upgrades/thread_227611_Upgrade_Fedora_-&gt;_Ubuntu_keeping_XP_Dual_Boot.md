---
title: "Upgrade Fedora -&gt; Ubuntu keeping XP Dual Boot"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by Megamanic on 2006-08-02
I have a laptop with XP in the (20Gb) default boot partition, a 40Gb NTFS "Shared Data" partition the remaining 20Gb devoted to Fedora Core 5 which was the most up-to-date distro on my disk pile when I came to upgrade from SuSE 9.3 which was not particularly stable on my hardware.

Anyway, long story short, not happy with FC5 - tried Dapper Live CD & like what I see so I want to effectively install Dapper into the space Fedora's taking.  When I installed FC5 it gave me the option of installing over the existing Linux installation it found (SuSE 9.3) which it then proceeded to do flawlessly.  

Ubuntu des not have a comparable option & it does not look to be straightforward.  Of the partitioning options I'm being offered the only one that seems to make any sense is me manually deleting the two Fedora partitions & recreating Ubuntu friendly ones.  That I can handle, what would concern me is the existing Grub configuration handling the dual boot & whether or not it will be blown away by doing this. Or more to the point how well Ubuntu will install itself & detect the presence of XP.  I'm seeing postings in this forum from people with Dual boot problems & I don't want to be one of them :wink: 

I REALLY don't want to have to do a complete re-install of XP.  Yes I will still need to have XP available for the forseeable future...

How smart is Ubuntu in this regard the install options look a little too "hands on" for me to feel confident.

---

### Post by wieman01 on 2006-08-02
Unless you install Ubuntu on top of the existing XP installtion, you don't have to worry. Ubuntu recognizes XP/Windows and updates GRUP accordingly. After the installation you will be given the option to boot either of the OS.

Secondly you can configure/manipulate GRUB at any given point in time after you have installed Ubuntu. It's fairly simple, you merely need to add 1 or 2 lines, that's it.

No worries, Ubuntu may not be straightforward in all respects, but this one - by all means - is a go.

---

### Post by Megamanic on 2006-08-02
> **wieman01 said:**
> Unless you install Ubuntu on top of the existing XP installtion, you don't have to worry. Ubuntu recognizes XP/Windows and updates GRUP accordingly. After the installation you will be given the option to boot either of the OS.

Secondly you can configure/manipulate GRUB at any given point in time after you have installed Ubuntu. It's fairly simple, you merely need to add 1 or 2 lines, that's it.

No worries, Ubuntu may not be straightforward in all respects, but this one - by all means - is a go.

Thanks for that - I found another post that links to this [article]("http://www.psychocats.net/ubuntu/installing.html") which showed me the steps **after** the one that caused me to panic & bail out this morning - that made me feel more confident as well.

Ubuntu goes on the next time I boot my laptop.

---

### Post by Megamanic on 2006-08-07
So, I kept my promise & Ubuntu went on Friday night.

I manually deleted the two Fedora partitions & recreated a 2Gb Swap and 18Gb EXT3 root partitions.

Or I would have if Ubuntu would have let me.  It kept erroring out trying to create partitions saying something like "the filesystem cannot be read".  Now remember this is EXT3 not anything weird & wacky.

Deleted the partitions leaving 20Gb empty & went back and let Ubuntu try to load into the empty space.  Same sort of errors.

Looks like the disk I'm booting from can't read ANY filesystem except NTFS) ](*,) 

The disc I was using came from an APC (Australian Personal Computer) cover DVD.  Is there a known fault with this disk?

I've got a shipit consignment on the way so I'll give it another crack then but for the moment I'm back on Fedora which had an installer that let me just boot & get back to a working system...

---

### Post by wieman01 on 2006-08-07
Weird, but similar thing happened to me while I had to reinstall Linux. So eventually I decided to format all Linux partitions with PartitionMagic (Windows tool)... No issues after that.

---

### Post by Megamanic on 2006-08-07
Thanks, don't have "Partition Magic" & I don't want to buy it just to install Ubuntu - remember Fedora Core 5 installed flawlessly & I'm back to square one.

What we've got is a weird situation where the partition tool fails but Fedora's still works.  Can we get a developer to look at this?

---

### Post by wieman01 on 2006-08-07
Proper root cause analysis & correction action would certainly be nice, but I am not sure how we can draw their attention to this thread. :-)

Since that won't resolve your immediate problem would you be able boot Windows 98? If you still have a copy of it on a CD (I still do) then you could use "fdisk" to format your partitions (FAT) so that Ubuntu will recognize them. Just a thought.

But I agree that this is a hassle, my installation of Ubuntu did not go without glitches either.

---

### Post by Megamanic on 2006-08-07
You can still do all that while installing XP from scratch.

What I've got at the moment is a working XP/Fedora Core 5 dual boot.

How I got there was torturous.  I set up XP with 4 20 Gb partitions XP(NTFS)/NTFS/FAT32/Empty.

I then installed SuSE 9.3 Professional into the empty partition.  Had numerous problems probably due to the age of the distro but also due to lack of net connection.

I don't have a net connection to upgrade on so I moved over after a couple of months to FC5 which installed over SuSE. Simultaneously I combined the middle two partitions to one 40Gb NTFS partition using the XP tools.

FC5 won't allow you to add or remove programs from the install media - only over the internet :confused: so that was a no-go.  There's a vague workaround but unsatisfactory so I tried the Ubuntu Dapper distro off of the APC DVD.

Much better,  tried to install...

First "problem" it should offer to replace Fedora (or any other existing linux distro it finds).  No question, that's a missing option in the installer.

Second problem - showstopper.  Ubuntu's partitioner simply does not work on my system.  It deletes partitions ok but can't create any partition I tried.  I went for LinuxSwap, EXT3, EXT2 & possibly ReiserFS though I forget (I'm trying to forget Friday :().

In an ideal world I'd like the following:

15-20Gb NTFS XP/40-50Gb(ish) EXT3 Shared data / 15Gb(ish) for Ubuntu  (or the way this is going, Mepis ;))  I don't trust Ubuntu not to stuff that up most heinously though...

---

### Post by Megamanic on 2006-08-07
[This ]("http://ubuntuforums.org/showthread.php?t=230551")thread has more info - looks like Gparted is rubbish :)

Might go back & try FDisk...

---

### Post by Irony on 2006-08-07
You could just unallocate the space via XP then install Ubuntu to the free space.

---

### Post by Megamanic on 2006-08-07
So you're saying kill the Fedora partitions using the XP disk management utilities?

---

