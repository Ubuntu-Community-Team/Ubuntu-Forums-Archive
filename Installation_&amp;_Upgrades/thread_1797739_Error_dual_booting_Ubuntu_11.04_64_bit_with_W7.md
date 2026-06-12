---
title: "Error dual booting Ubuntu 11.04 64 bit with W7"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Jepumyr on 2011-07-05
While I have used Ubuntu before, this is the first time I've tried to install it. I was try to dual boot it via an ISO burned DVD with Ubuntu 11.04 on it and got a "Failed to copy files; fault CD/DVD or hard disk?" error message. Sorry I don't have the full message; I should have screenshot it. My system is 64 bit and I was trying to install the 64 bit version of Ubuntu (at least I intended to; now that I think about it I did re-download it, so I might have forgotten to say 64 bit the second time..).

I'd do the standard things like try to re-download and burn it, etc. But a problem I'm having right now is the fact that Ubuntu has left some extra partitions on my hard disk. I don't completely know my way around partitions, so I'm not sure how to get that sorted before trying again. I don't want to mess anything up.

```

Dell Inspiron 15R
CPU: Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz (Quad Core)
RAM: 8.00 GB
HDD: 600 GB

Ubuntu: 11.04
Windows: 7 Home Premium 64 bit SP1

Partitions:
volume:0 Windows FAT volume (100MB)
volume:1 Windows NTFS volume (14GB)
volume:2 Windows NTFS volume (441GB)
volume:3 Extended partition (140GB)
   logicalvolume:0 Linux filesystem partition (132GB)
   logicalvolume:1 Linux swap / Solaris partition (8097MB)
```I'm not sure if any other information is relevant. Any help is appreciated and thanks for reading. :)

---

### Post by FormatSeize on 2011-07-05
Don't worry about the partitions before trying again. Ubuntu will take you through a very easy, guided partitioning that is just click and drag when it comes to resizing the partitions, and the installation will take care of the details of the swap partitioning and other sorting of partions after you give a relative size of each your Linux and Windows partitions.

---

### Post by deeppow on 2011-07-05
To delete the partitions, once you've booted into Windows 7:

- Right click on "Computer" and select "Manage".  
- Part way down left side of the window that will appears is "Disk Management," click on it.  
- That will open a list of the partitions in the right hand part of the window.  You should see the new partitions in that window. 
- Point at one of them and right click.  CAREFUL not to select your Windows (NTFS) partition(s), it should be obvious what they are.
- Among the option that drop down with the right click is one to "Delete volume".  Pick it and that should free up the space and show it as unallocated.
- After you've delete all the partitions you don't want they should accumulate into unallocated space.  Leave them alone.

When you next install Ubuntu from the choices of where to install it, tell it to use the largest free space.  It should then use the unallocated space you've created (that assumes you don't have other free space setting around.)  :lolflag:

---

### Post by oldfred on 2011-07-05
I do not recommend using windows partition tools for Linux partitions. Better just to use gparted from the liveCD if you want.

The 32bit will install on you system, but you would do better with the 64Bit. I now prefer to use flash drives for an install as it is quicker and reusable.

You do not have to delete partitions if you are willing to manually specify partitions useing manual install "Something Else" in Natty. You just have to specify sda5 as / (root) and what format to reformat it. Ext4 is standard format now. It will find swap automatically. So the manual install is not much more complex than a auto install.

Heman has lots of detail in his install procedures, but not as complex as it seems.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu

---

### Post by deeppow on 2011-07-05
I've used Windows, including Win7, for several years as needed to delete linux partitions and it works fine.  I don't suggest you build linux partitions with it, let Ubuntu deal with that as it installs.

Anyway, to each his own.

> **oldfred said:**
> I do not recommend using windows partition tools for Linux partitions. Better just to use gparted from the liveCD if you want.

The 32bit will install on you system, but you would do better with the 64Bit. I now prefer to use flash drives for an install as it is quicker and reusable.

You do not have to delete partitions if you are willing to manually specify partitions useing manual install "Something Else" in Natty. You just have to specify sda5 as / (root) and what format to reformat it. Ext4 is standard format now. It will find swap automatically. So the manual install is not much more complex than a auto install.

Heman has lots of detail in his install procedures, but not as complex as it seems.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu

---

### Post by Jepumyr on 2011-07-06
Thanks everyone. I ended up re-downloading it, using a USB and doing it the 'Something Else' way. It's all working now. :)

---

