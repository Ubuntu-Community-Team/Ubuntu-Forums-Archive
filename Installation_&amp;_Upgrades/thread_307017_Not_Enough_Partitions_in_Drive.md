---
title: "Not Enough Partitions in Drive"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by ColCommunism on 2006-11-25
Hello.  I'm new to Linux and am trying to install Ubuntu 6.10 onto my computer, which has Windows XP, 32 gigs of hard drive space, and 512 megs of RAM.

I've burned it onto a CD, loaded up the LiveCD and everything else that's necessary, but once I get to the partitions part, I'm stuck.  I've got four partitions that go something like this.  The numbers have been fudged a little, and I can't remember the name of the ext3 one, but I hope it doesn't matter.

/dev/sda1 - FAT16 - 47 megs
/dev/sda2 - NTFS - 20 gigs
/dev/sda3 - FAT32 - 3 gigs
Gparted-made partition - ext3 - 9 gigs

The ext3 partition was made with Gparted in Ubuntu, and the other three were there when I got there.  The problem is that I can't create another partition for my swap partition, and there's no way that I'm going to delete one of the Windows partitions unless I know what I'm doing.

So basically, I've run out of partitions.  Is there any way to create a swap partition without getting rid of some Windows files?

---

### Post by taurus on 2006-11-25
On a harddrive, you can only have four primaries partitions and if you need more than four, you need to make one of the primaries into extended partition and create many logical paritions from that extended partition.  So, if you need two more partitions for Ubuntu, / and swap, you need to make the last one as an extended partition and tell the installer to use that to install Ubuntu on.  The installer now will make that into /dev/sda5 for / & /dev/sda6 for swap...

---

### Post by ColCommunism on 2006-11-25
Before I go rushing back to my installer, how do you make an extended partition, exactly?  I remember looking for that, but I don't think I was able to find an option for it in Gparted.

---

### Post by taurus on 2006-11-25
[http://gparted.sourceforge.net/screens/gparted_1_big.jpg](http://gparted.sourceforge.net/screens/gparted_1_big.jpg)
[http://gparted.sourceforge.net/screens/gparted_4_big.jpg](http://gparted.sourceforge.net/screens/gparted_4_big.jpg)
[http://gparted.sourceforge.net/screens/gparted_7_big.jpg](http://gparted.sourceforge.net/screens/gparted_7_big.jpg)

---

### Post by ColCommunism on 2006-11-26
Thank you very kindly.

---

