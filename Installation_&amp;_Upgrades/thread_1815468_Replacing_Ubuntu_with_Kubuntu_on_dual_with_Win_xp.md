---
title: "Replacing Ubuntu with Kubuntu on dual with Win xp"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by Bkock on 2011-07-31
I have Ubuntu 11.04 32 bit running dual boot with Win XP and all is fine. BUT, I would like to try Kubuntu 64 bit for a while.
When I run the Kubuntu disk it tries to add partitions and install beside Ubuntu not replace it.
I would like to know how to leave windows alone and setup the partitions and replace Ubuntu with Kubuntu.
Also if possible would like to have /home in a separate location in case of an incident with the operating system.
Any help greatly appreciated.
Thanks,

---My first or second post, hope this is not to far out of order---

---

### Post by spsf on 2011-07-31
Did you try to install kubuntu-desktop?
After that, when you login just log into kde plasma session and you can enjoy kubuntu
Also you can head to kubuntu.org and find instructions on how get the new kde 4.7
Hope it helps

---

### Post by oldfred on 2011-07-31
To change to 64bit you will have to do new install.

I always suggest partitioning in advance and then using manual install (Something Else in Natty) to choose which partition is / (root). If /home is separate then you also choose it but DO NOT format it.

If you do not have a separate /home partition, you can make it before hand and copy your data into the partition before you install. Some settings in the hidden files may not work but since you can install both desktops in the same system it should work. Normally you should not use a /home from one system to another except for upgrades.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

You can use the move home instructions, but only have to copy to the new partition as the new install will then automount and create the fstab entry.

Three essentially identical ways using different copy commands:
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Bkock on 2011-07-31
Thanks for the quick response. 
FYI. I am a fairly decent windows user and have been an Ubuntu user for about a year so I may not be explaining things in the right terms.
Your first statement is correct and that exactly what I want to do "New Install" and have no need to preserve the "old" Home folder or it's contents. I do need windows in it's current state.  
I have downloaded the KUBUNTU 64bit iso and burned the image to disk. When I try to Install it brings up the Partition table with three options the default looks as if it will create more partitions and install Kubuntu there along side windows and Ubuntu and not in place of Ubuntu as I would like. I am sure I need to use the manual partition but thats where I get lost. Your statement says to partition first then use the manual install. I guess that the part I don't understand. There are already partitions of the correct size except maybe for the HOME partition. What I want to do is replace the contents of the current ubuntu partitions with KUBUNTU if thats possible and create a separate HOME partition.

  Once I get to the manual partition screen I panic and back out of the install maybe if I just continue the next screen might explain more???

Thanks

---

### Post by oldfred on 2011-07-31
You can do it all inside the manual install. I just like to do it first. But either way you have to shrink your current / and create a new partition for /home. If current / is inside the extended partition it should be easy. If changing the size of a windows partition, I think it is more important to partition first, and then reboot into windows. Windows wants to run chkdsk and adjust to its new size and it is best to confirm that is ok before the install of Ubuntu.

Post screen shot from gparted if you want a bit more detail.

With a separate /home you only need 10-20GB for /. I use 20-25Gb but keep all data separate from /. Default install is just over 4GB and with lots of programs I have about 6 or 7GB used in my / partition.

---

### Post by Bkock on 2011-08-06
Problem Solved!
I just selected the OLD Ubuntu drive(ext4) on the patrition screen of the installation process,resized and formated it to about fifty meg and then selected the Empty space and selected   /Home   and continued the installation it loaded and ran fine without damaging my Windows XP.

Thanks to all who gave assistance.

---

