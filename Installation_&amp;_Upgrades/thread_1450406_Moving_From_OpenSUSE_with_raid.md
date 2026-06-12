---
title: "Moving From OpenSUSE with raid"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by theparticle010 on 2010-04-09
I have run Ubuntu in the past and then switched to OpenSUSE several months ago and set up raid 0 on a 500gb hard drive and 700gb hard drive ( I went with openSUSE because of the graphical raid setup. )

My whole partition setup looks like this:

500gb Hard Drive:
400gb Partition For raid
50gb partition for raid
15gb /boot partition ext3

750gb Hard Drive:
400gb Partition for raid
50gb partition for raid
Rest of the drive not used.

md0 is the two 400gb partitions on each drive for a total of 800gb space on my /home partition ext4 filesystem ( 380gb space used )
md1 is 100gb ext4 / partition.

all raid 0

Now I was wondering if I downloaded the alternate install cd for ubuntu ( as OpenSUSE has crashed for the second time because of bad updates ( starts, but gets to terminal only ) ) would I be able to keep my raid 0 home partition and wipe the rest of the each drive and setting up Ubuntu keeping all of my files and settings intact, just to install my programs I need all while keeping my old settings ( such as firefox bookmarks, virtual box utilities etc. ) intact.

From what I know it's possible, but I don't know much about the Ubuntu Alternate install disk ( as I have been dealing with dependancy hell on OpenSUSE ) but in OpenSUSE it wont let me keep the old raid setup ( md0 ) Im guessing it is possible to set up the home directory on a different hard drive and then going back into the live cd, editing the fstab, and switching it to md0, if this is even possible, or would I need to configure the driver on that system before I did that :confused:  Oh and I forgot to mention that I've only been running 64bit operating systems.

System Specs:
AMD Dual core at 2.8ghz ( overclocked, stable, cpu ran at full bore for a day. only reaching 120f)
Nvidia 9600 gso 368mb ram
4gb ram at 800mhz

---

### Post by theparticle010 on 2010-04-12
Well I decided to go ahead and wing it, and all I did was when I put in the alternate install disk I went to the manual partition manager, hit undo ( as it tried to auto configure a partition setup ) and specified which partitions would be used and I was able to keep everything, I just created a random account to use, then I went into users and added the account that was used on OpenSuSE and when I logged in everything was just as I had expected it to be, not a setting changed! ( now to just to install all of my software again. )

---

