---
title: "Should I make a partition on my Portable HDD for Ubuntu?(10.10)"
date: 2010-12-26
forum: Installation &amp; Upgrades
---

### Post by Se7enex on 2010-12-26
Hey guys:D I recently installed Ubuntu(10.10) on my Portable HDD and now Windwos won't read it! I figured this would happen and i was wondering, if I partition and install on the partition will i be able to use the remaining space for storage? (Thank you in advance!)

---

### Post by tommcd on 2010-12-26
> **Se7enex said:**
> Hey guys:D I recently installed Ubuntu(10.10) on my Portable HDD and now Windwos won't read it! 
How did you install Ubuntu? Did you install Ubuntu inside Windows using Wubi? Or did you install Ubuntu the real way to a dedicated linux partition on your hard drive?
In any case, Windows can not read linux file systems. Ubuntu (and other linux distros as well) can read Windows NTFS and FAT32 file systems though.
> **Se7enex said:**
> 
... if I partition and install on the partition will i be able to use the remaining space for storage? 
If you want to have a partition for data storage that can be read and written to by both Ubuntu and Windows, then format that storage partition as NTFS from Windows. You can then store data on that storage partition that you can read and write to from both linux and Windows.
Your Ubuntu root partition should be formatted in a native linux file system like ext4, which is the default on a Ubuntu install.

Write back if you need more help.
And welcome to the Ubuntu forums!

---

### Post by Se7enex on 2010-12-26
> **tommcd said:**
> How did you install Ubuntu? Did you install Ubuntu inside Windows using Wubi? Or did you install Ubuntu the real way to a dedicated linux partition on your hard drive?
In any case, Windows can not read linux file systems. Ubuntu (and other linux distros as well) can read Windows NTFS and FAT32 file systems though.

If you want to have a partition for data storage that can be read and written to by both Ubuntu and Windows, then format that storage partition as NTFS from Windows. You can then store data on that storage partition that you can read and write to from both linux and Windows.
Your Ubuntu root partition should be formatted in a native linux file system like ext4, which is the default on a Ubuntu install.

Write back if you need more help.
And welcome to the Ubuntu forums!

I installed via USB Live CD :)
I'm wondering if i choose to install Ubuntu to a partition on my HDD will the remaining space still be available?
(sorry for any trouble, i'm a noob :b)

EDIT: the HDD is portable(USB).

---

### Post by tommcd on 2010-12-26
> **Se7enex said:**
> I installed via USB Live CD :)
Do you mean you installed Ubuntu *from* the live CD *to* a usb flash drive, or to the usb connected hard drive? 
Or did you install Ubuntu *from* a usb flash drive *to* your hard drive?
It can be done both ways. I just want to make sure we are both on the same page here.
In any case, Windows will not read linux file systems no matter where you have installed Ubuntu.
> **Se7enex said:**
> 
I'm wondering if i choose to install Ubuntu to a partition on my HDD will the remaining space still be available?

If you choose manual partitioning, you can install Ubuntu to any size partition you want; and the remaining space wil be availabe and can be partitioned any way you want. I would recommend 10 GB for your Ubuntu root partition. You could get by with less if you are tight on space.
On the other hand, if you have lots of space available, then go with 15-20 GB for the Ubuntu root partition. 
For reference, my Ubuntu root partition has never grown larger than about 4-5.5 GB in size. The only exception to this was when I had installed some big games on my Ubuntu root partition like Doom3 or Quake4.
For some very detailed tutorials on dual booting Ubuntu + Windows, see Ubuntu forums member Herman's site:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
Here is another great site to help you get started with Ubutnu:
[http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)

---

### Post by Se7enex on 2010-12-26
> **tommcd said:**
> Do you mean you installed Ubuntu *from* the live CD *to* a usb flash drive, or to the usb connected hard drive? 
Or did you install Ubuntu *from* a usb flash drive *to* your hard drive?
It can be done both ways. I just want to make sure we are both on the same page here.
In any case, Windows will not read linux file systems no matter where you have installed Ubuntu.

If you choose manual partitioning, you can install Ubuntu to any size partition you want; and the remaining space wil be availabe and can be partitioned any way you want. I would recommend 10 GB for your Ubuntu root partition. You could get by with less if you are tight on space.
On the other hand, if you have lots of space available, then go with 15-20 GB for the Ubuntu root partition. 
For reference, my Ubuntu root partition has never grown larger than about 4-5.5 GB in size. The only exception to this was when I had installed some big games on my Ubuntu root partition like Doom3 or Quake4.
For some very detailed tutorials on dual booting Ubuntu + Windows, see Ubuntu forums member Herman's site:
[http://members.iinet.net/~herman546/](http://members.iinet.net/~herman546/)
Here is another great site to help you get started with Ubutnu:
[http://psychocats.net/ubuntu/](http://psychocats.net/ubuntu/)

I installed Ubuntu Live CD to a flash drive then used that to install it to my USB hard drive :).

So, if I make a manual partition the rest of the drive will remain unaltered?

Thanks for all this info!

---

### Post by tommcd on 2010-12-26
> **Se7enex said:**
> I installed Ubuntu Live CD to a flash drive then used that to install it to my USB hard drive :).
That is fine. For future reference, you could have installed Ubuntu directly from the live CD to the usb hard drive without going first to the usb flash drive.
> **Se7enex said:**
> 
So, if I make a manual partition the rest of the drive will remain unaltered?

Yes that is correct.
As an example, lets say you have 100 GB on the hard drive. If you choose to install Ubuntu to 20 GB of that hard drive using manual partitioning, then the remaining 80 GB will remain unallocated.

---

### Post by Se7enex on 2010-12-26
> **tommcd said:**
> That is fine. For future reference, you could have installed Ubuntu directly from the live CD to the usb hard drive without going first to the usb flash drive.

Yes that is correct.
As an example, lets say you have 100 GB on the hard drive. If you choose to install Ubuntu to 20 GB of that hard drive using manual partitioning, then the remaining 80 GB will remain unallocated.

my laptop has no CD drive. thats why. :P

---

### Post by dino99 on 2010-12-26
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Se7enex on 2010-12-26
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

...what?!

---

### Post by tommcd on 2010-12-27
> **Se7enex said:**
> ...what?!
What Dino99 was pointing out there is a possible partitioning scheme for Ubuntu that includes three partitions:
1. Root. This is where the Ubuntu operating system lives.
2. Swap. This is hard drive space that is reserved for 'swapping out' processes from the computer's memory to the hard drive if the available memory is all in use. This is analogous to virtual memory in Windows.
3. Home. This is where all your data and your user specific configuration settings are kept. 
See this tutorial for partitioning the hard drive during installation. It covers the ideal setup of three partitions: root, swap, and home:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
That entire website has lots of beginner friendly tutorials. It is an excellent place to get started learning Ubuntu.

---

### Post by presence1960 on 2010-12-27
> **dino99 said:**
> [http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

That is **_ONLY ONE_** viable way to install Ubuntu. It is by no means "How To Install Ubuntu"

To the OP: Welcome to Ubuntu Forums. I see you describe yourself as a noobie. Continue with tommcd's suggestions. There are quite a few different ways to configure a linux installation, however in your case I would opt for simplicity.

---

