---
title: "Installation - KnowNothing totally baffled"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by KnowNothing on 2007-05-25
I don't know anything but I am trying to install 7.04 off the CD as a dual boot with Windows.  For partitioning, I read there are supposed to be three choices but I don't have the "Guided" for dual boot -- the only ones I have are "Guided - use entire disk" and "Manual."  The one I really need just isn't there.

I have three Windows partitions: two FAT32 for system and back-up and one huge NTFS for data.  I have absolutely no clue whatsoever how to partition manually for Ubuntu.  I would very much appreciate help.  Sorry, but the help has to be very specific, assuming I was born yesterday--very late yesterday at that.

Sorry to be so lost.  I really appreciate anything anyone can tell me or guide me to.  I have searched for help but it all seems to assume some basic knowledge so I find it baffling.

Thanks very much in advance.

---

### Post by coffeecat on 2007-05-25
I'll post what I can, but it's late here in the UK at the moment and I shall be calling it a day soon. I'll pick up the thread tomorrow, but that will be some hours away. But first a few comments, a few questions and a couple of suggestions.

If you've managed to spread your Windows installation over three partitions, you know more than you give yourself credit for. But a question. What version of Windows is that you've got there? To be able to read an NTFS data partition, it's probably XP but it's most unusual for XP to be installed on a FAT32 partition. Are you sure it's not the other way around?

My guess is that the guided install for a dual-boot can't cope with three pre-exisiting partitions (it is unusual) and that is why you are not getting the option you need.

Anyway, a suggestion. Boot up the live CD and go to System > Administration > GNOME Partition Editor. See what that shows and post back the following information:

1 Total size of hard drive
2 Sizes and numbers of your three pre-exisiting partitions. The numbers will be something like hda1 or sda1, hda2/sda2 and so on.
3 Any unallocated space and if so, how much.

Explanation about partition numbers. You can have a maximum of 4 primary partitions (hda1,2,3,4). Windows C:\ has to be installed to a primary partition. Linux can go to a primary or logical partition. Instead of a primary partition you can have an extended partition which is a 'wrapper' for a number (can't remember the limit but it's quite a lot) of logical partitions. Hence primary or extended partitions will always be numbered 1,2,3 or 4. Logical partitions will always be numbered hda5/sda5 upwards.

In order to install Ubuntu you need to create two more partitions, one for swap (Linux uses a swap partition whereas Windows uses a swap file) and one for the root partition - the Linux equivalent to C:\, more or less. With three pre-existing partitions, you will first of all have to shrink one if there is no unallocated space, create an extended partition if there isn't one already, and create two logical partitions for Ubuntu. That's why we need to know the numbers of the pre-existing partitions - to see if they are all primary or a mixture of primary and extended/logical.

That's enough for now. Post back with the information and we can take it from there.

**Edit:** Do be careful while you are in the Partition Editor. Just look. Don't do anything. You can completely reformat your whole hard drive with a few injudicious clicks. :?  And..... if by chance you've got two hard drives there, they'll be called hda/sda and hdb/sdb, with numbers for the partitions - you get the picture. In the Partition Editor there's a little drop down menu top right to select which drive so that you can only see one drive graphically at a time.

---

### Post by KnowNothing on 2007-05-25
Thanks very much for the response.  I had nothing to do with the three Windows partitions--my computer came that way new.  I have no idea why the manufacturer did that but I suppose there is some reason.

Here is the info you requested:

Partition         Filesystem       Size              Used             Unused       Flags

/dev/sda1   !   fat32          19.53 GiB           ---                 ---              boot, lba
/dev/sda2       fat32            4.88 GiB         1.8 GiB          3.08 GiB      lba
/dev/sda3       ntfs          208.47 GiB      22.38 GiB      186.09 GiB

The "!" in the first line is inside of an orange triangle.

Should/could I rearrange the Windows partitions so they are simpler or is there some special way of installing Ubuntu along with this Windows set-up?

I really appreciate your help.

---

### Post by KnowNothing on 2007-05-25
I spaced that information out neatly but it didn't show up that way.  Sorry.

---

### Post by KnowNothing on 2007-05-25
Oops, forgot to mention it is Windows XP.  sda1 is the Windows XP system, sda2 is called "back-up" and sda3 is data.  Thanks again for your patience.

---

### Post by coffeecat on 2007-05-25
> **KnowNothing said:**
> 
Partition         Filesystem       Size              Used             Unused       Flags

/dev/sda1   !   fat32          19.53 GiB           ---                 ---              boot, lba
/dev/sda2       fat32            4.88 GiB         1.8 GiB          3.08 GiB      lba
/dev/sda3       ntfs          208.47 GiB      22.38 GiB      186.09 GiB

The "!" in the first line is inside of an orange triangle.


I don't know what the ! means. Perhaps it means an active partition with a boot flag, but this will only be relevant to Windows. Linux is aloof to such things. :)

Actually, your partition layout is exactly what I hoped. It makes it relatively easy. In essence, what you need to do is:

1 Shrink your sda3 partition **after** backing up all data thereon.
2 Create an extended partition in the freed space. It will be called /dev/sda4
3 In the extended partition, create two logical partitions as follows:
- swap. This could be sda5. The rule of thumb is twice the available RAM, but usually no more than 1 GB, unless you are going to use suspend/hibernate when swap must be equal to or slightly bigger than RAM.
- ext3 partition for Ubuntu. This will be sda6. 

I think this is as much as I can post now without making silly mistakes through tiredness. One last thought. It's a pity the data partition is NTFS. With a dual boot it's useful to have a shared data partition that both Windows and Linux can read and write to. It's quite possible to read and write to NTFS partitions now from Linux but the write part is fairly newly developed and a default Feisty install will only give you read access. It's just another complication setting up read/write. One alternative would be to create three new partitions, one a FAT32 for data - it's something to think about.

I'll pick this thread up tomorrow. In the meantime perhaps someone else will contribute.

**Edit:** Just noticed that you are West Coast, USA. That gives us quite a time zone difference. I'm getting jet lag here already. :wink: G'night!

---

### Post by merlinus on 2007-05-25
> 
It's quite possible to read and write to NTFS partitions now from Linux but the write part is fairly newly developed and a default Feisty install will only give you read access. It's just another complication setting up read/write


I have found it very simple to install the drivers that allow me to read and write to and from both ntfs and ext3 partitions, so don't let this stop you.

I would recommend setting up a /home partition as well as /swap and /root.  It will make it much easier to upgrade Feisty, and also give you space on Ubuntu for data files and folders.

Good luck!

-merlin

---

### Post by KnowNothing on 2007-05-25
Thanks tons to both of you for the help.  I will try to take the next step.  So these two new main partitions are to be named "/swap" and "/root"?

Very much appreciated.

---

### Post by merlinus on 2007-05-25
/swap and /root, and /home, if you choose to create a partition for it, are mount points.  You can set up the partitions beforehand, and when installing from the Ubuntu live cd and get to the partitioning screen, select the mount points from a dropdown menu.

Or you can do all this partitioning whilst installing.  Just be sure to defrag the ntfs partition within windows beforehand.  

-merlin

---

### Post by KnowNothing on 2007-05-25
Will do, thanks.  Any idea how much space to give each one?

Thanks so very much again--I'd be lost without all this excellent assistance.

---

### Post by confused57 on 2007-05-25
> **KnowNothing said:**
> Will do, thanks.  Any idea how much space to give each one?

Thanks so very much again--I'd be lost without all this excellent assistance.

Make sure to select (/) for your root partition mountpoint, not /root...

---

### Post by merlinus on 2007-05-25
Excellent point about / and not /root as mountpoint.

As for space:

/swap need not be more than a half gig, unless you have that or less for RAM.  In that case, double it.

The rest depends upon the free space.  I use about 18G each for /home and /, but then I do not have one of these megadisks!  

I also have a /storage partition, where I keep data that is accessed only occasionally.  But you could use your ntfs partition for this.

Good luck!

-merlin

---

### Post by KnowNothing on 2007-05-26
It worked!  I'm very excited.  I have root, swap and home partitions and the system is installed.  Thanks very, very much for all of your help--it was perfect advice and I would have been stuck without it.

Best wishes.

---

### Post by coffeecat on 2007-05-26
I'm glad it all worked OK. I hope you enjoy your time with Ubuntu/Linux. If you're anything like me, soon the only time you'll boot into Windows is to update the virus definitions in your AV software. :)

---

