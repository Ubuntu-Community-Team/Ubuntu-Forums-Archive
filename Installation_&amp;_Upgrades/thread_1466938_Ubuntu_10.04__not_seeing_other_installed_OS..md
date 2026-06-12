---
title: "Ubuntu 10.04  not seeing other installed OS."
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by ds77 on 2010-04-30
I am installing 10.04 on my laptop which currently has Windows 7.  I plan on dual booting my laptop and figured that just like prior releases it will detect my Windows 7 OS and say "Hey I found Win7, do you want to wipe the partition or install side by side and use grub?"  

Well in this case, its telling me that no installed operating systems have been found and I only get the option to use the whole disc or I can go ahead and use gparted to create my own partitions.  

Any ideas would be appreciated.  Searching the forums for the last hour and I have not found this issue.

Thanks!

---

### Post by kansasnoob on 2010-04-30
That's downright scary!

If I were you I'd resize Windows with it's own partitioning tools and then boot to the Live Ubuntu Desktop, use Gparted to create the partitions for Ubuntu (I prefer a root "/" no smaller than 6GB, a SWAP slightly larger than total RAM, and a "/home" using the rest of the free space).

Then write down the new partition designations, eg: /dev/sda5, /dev/sda6, etc. and select "manual" from the installer menu. The following guide gives a basic idea what things will look like:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Although that shows using Gparted to resize Windows and I'd never do that with Vista or Win7! It also does not show creating a separate /home, so it's just a "general" guide so you'll know what the various steps look like.

I multi-boot a lot and this is what mine looks like:

[ATTACH]154832[/ATTACH]

Of course my /home partitions are small because I use separate data partitions that are symlinked to my home folders but that's overkill for a simple dual boot.

---

### Post by ds77 on 2010-04-30
Thanks for the tips kansasnoob!

After trying to install and partition using different methods for the last 3hrs,I now notice others with this same issue.  I have tried the install with 2 different memory sticks (patriot and sandisk) as well as from CD and gparted crashes everytime. :(

---

### Post by ds77 on 2010-04-30
I have downloaded the latest .iso and it gparted crashes again.  Is there a work around for this problem? I can't seem to find any resolution.

---

### Post by blueridgedog on 2010-04-30
> **ds77 said:**
> I have downloaded the latest .iso and it gparted crashes again.  Is there a work around for this problem? I can't seem to find any resolution.

Gparted is a graphical front end to fdisk, which is a text tool that will allow you to do the same thing.  

This is a great tutorial:

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Caution:  There are no frills and the assumption is you know what you are doing.  I ALWAYS write down (on paper) the partitioning schema that I am intending to create when I used fdisk, such as:

Primary disk, /dev/sda
/sda1 First Primary, 100 gig, for windows
/sda2 Second Primary, 100 gig, Linux
/sda3 Third Primary, 5 gig swap
/sda4 Fourth Primary, Extended Partition
/sda5 First Logical, 800 gig for files/documents

This is just fiction, but you get the idea...you want to know what you want to do before you start to run fdisk.

Don't forget to toggle the type as mentioned in the tutorial if you try it.

---

### Post by ds77 on 2010-04-30
Thanks for the link.  I managed to create the partitions by getting to gparted via command line. The install still fails though.  Is there a way to start the install from the command line as well?

---

### Post by blueridgedog on 2010-04-30
If you have partitioned your system with at least one Linux partition and a swap partition then you should be able to try installing via the alternate CD.  Though I have not used it in a while, I think it has a text based install option.

---

### Post by ds77 on 2010-05-01
I ended up installing 9.10 and then upgrading.  Worked perfectly.  Typing this on my laptop right now in fact!

---

### Post by blueridgedog on 2010-05-01
I too went ahead and jumped in for the upgrade.  Given the clogged pipe of all the others doing the same, I suspect it would have been better to just download the ISO and do a clean install...however, all worked well.

---

### Post by ds77 on 2010-05-05
marking this as solved.  My problem is solved as I upgraded.  But it seems that some folks still have a problem of a fresh install crashing at the gparted screen.

The following thread has more on the problem:
[http://ubuntuforums.org/showthread.php?t=1466009&highlight=gparted+crashing+install]("http://ubuntuforums.org/showthread.php?t=1466009&highlight=gparted+crashing+install")

---

