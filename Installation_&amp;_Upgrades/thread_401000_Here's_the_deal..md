---
title: "Here's the deal."
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Bolto on 2007-04-04
Okay i am new to Ubuntu and Linux in general and i am trying to dual boot Windows XP and Ubuntu. I currently have Window's XP and am defragmenting my disk for installation of Ubuntu. So Heres the deal: i want to know whether my computer will be compatable and whether my thoughts on partitioning is correct.

My computer has 1GB of DDR RAM,
a GeForce 6200 256mb graphics card
and a hardrive of 75GB, of which 22GB is free.

Partitioning i am thinking of:

Windows( 60GB resize?) | UBUNTU ( 13GB? )|  Swap 2GB |
          ( NTFS )             |       ( EXT3)          |                 |

OR


Windows( 57gbGB resize?)|  Shared data (13GB)  | UBUNTU ( 3GB? )|  Swap 2GB|
          ( NTFS )                |     ( FAT32)              |      (EXT3)          |                |


I am considering the first one as you can see my windows it already quite full and i will mainly be using windows and just ubuntu for learning.

my main worry is that after defragmenting and partitioning the HDD ( with the boot up gnome installation) will it ask me to say whats what if you understand what i mean, like say whether the 13gb of ( FAT32 ) is shared and how easy is it?

And also what is the chances the install will go wrong and neither windows nore ubuntu will be bootable and i will have to reinstall windows from scratch. (I'd rather not make a backup as the only 'important' things on my windows are games which are easily installable.)

and 1 last thing will the bootloader ( GRUB? ) install automatically and will i be able to choose straight after installation whether i want to boot windows or ubuntu?

Thanks in advance.

---

### Post by teaker1s on 2007-04-04
firstly I'd recommend "gparted live iso" to point and click adjust your partitions.
Then when you have the total unallocated space you want for ubuntu, select install on largest free space. The partitioner can automatically set best options.

Lastly if you let ubuntu automatically set up grub it will ask if you want windows added to grub-if yes then you get a choice of ubuntu or windows at boot

welcome to the forums:lolflag:

---

### Post by sloggerkhan on 2007-04-04
you shouldn't need a 2gig swap for a regular desktop... If you have 22 gigs free, my instinct would be to have a 512 - 768 mb swap. (Which should still be more than big enough. I pretty much have never used more than 10% of my swap and it is about that size.) and then make the rest the regular linux partition. Linux will want to use ext2 or 3 format which will not be readable by default by windows. It also shouldn't need defragging, I think. Anyhow, I'd just leave 15 gigs of the rest for linux.

---

### Post by teaker1s on 2007-04-04
defrag and scan disk are required to avoid problems

---

### Post by Bolto on 2007-04-04
The reason im defragging is when i actually tried partitoning an error came up, and i read around and there was a lot of recommendations to defragment before partitioning.

Tell me if i am wrong.

Also when i choose do the unallocated space thing for ubuntu, like you said, will it automatically make the swap partition?

---

### Post by teaker1s on 2007-04-04
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
you need to download and burn as image. Scan disk and defrag-then boot gparted and you can adjust windows partition with point and click.
[B]Note when you reboot windows you must allow it to scan disk if it asks-or you'll get BSD
[/B]
Yes if you allow the installer to guide you then you avoid the hassle of deciding correct partition settings.

One of our long time regular contributors and a forum member of staff created this I believe which has good set of instructions
[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by Bolto on 2007-04-04
Thanks, i'll take a look at them

---

