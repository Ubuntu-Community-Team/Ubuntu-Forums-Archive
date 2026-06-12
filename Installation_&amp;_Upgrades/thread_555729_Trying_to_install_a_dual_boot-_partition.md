---
title: "Trying to install a dual boot- partition ?"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by G-Dawg on 2007-09-20
Hi I'm trying to work towards adding a windows xp partition to my system that came with ubuntu installed and i can't seem to work through any of the tutorials/documentation/support I'm finding.

I'm confused by my partitions in GParted- for which I can't seem to be able to manipulate at all to try and siphon off a few gigs for a seperate partition.  My screenshot looks different than others I've seen posted and I don't  how my drive is set up.  Can someone help me explain whats going on with my partition by looking at my screenshot?

---

### Post by Pumalite on 2007-09-20
You have a small swap partition on the left and 74.29 GB where '/' goes that you can resize. Right click on partition and from the menu choose 'resize partition'

---

### Post by dabl on 2007-09-20
This is not a great way to set up Ubuntu, IMHO ](*,)  That "/boot" partition is kind of a legacy approach from days of yore -- unless there's some plan to have multiple Linuces booting from it, and even then it's very stingy in size.

OK, on to your question: 

It looks like /dev/sda5 is a logical partition within the extended partition /dev/sda2 (the numbers are REALLY hard to see -- I'm talking about the 74.29G partition).  So, you can put your cursor on the right end of that partition in the graphic, and slide it to the left to free up whatever space you want for your Windows partition.  Then you'll need to make a new logical partition in the unallocated space that will result from shrinking /dev/sda5, and choose FAT32 or NTFS as the filesystem format, since that's what Windows uses.

Hope this helps.  If you could start over with that drive, there are better ways to partition it, and I'd be happy to share my thoughts on that.  :guitar:

---

### Post by az on 2007-09-20
No partitions can be in use while you resize them.  Make sure the swap is off and that the partition is unmounted.  You need to run any partitioning program from the live cd, if you only have the one drive.

sudo swapoff -a

---

### Post by Pumalite on 2007-09-20
You can do all you partitioning with Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
(The stand alone, burn iso to CD as 'Image', boot from, program)
Partition will be unmounted as Gparted works.

---

### Post by G-Dawg on 2007-09-20
I can't seem to be able to resize it.  I've tried booting from a GParted Live CD and even then it doesn't let me resize the bigger partition.  Do I need to unmount it and then run a Live CD?

---

### Post by Pumalite on 2007-09-20
If you are running the program I recommended, the partition is unmounted while the program works. I hope you are not talking of using the Gparted that comes with the Ubuntu CD.

---

### Post by G-Dawg on 2007-09-20
Pumalite: This is what I did: I burned a copy of gparted-livecd-0.3.4-8.iso to cd.  Restarted my computer.  Pressed F12 for boot menu when starting up.  Selected my CD drive.  In this GParted it won't let me resize my image, either by sliding the cursor or right clicking selecting resize (when I try the latter, under resize the up/down buttons are greyed out so I cant change it).  Could this problem have anything to do with the "!" symbol for the /dev/sda5 partition?

(fyi the screenshot was taken within the ubuntu GParted- but it looks the same when I boot from the live cd)

---

### Post by Pumalite on 2007-09-20
Lets try this: before booting Gparted, get in Ubuntu, go to terminal and code this:
sudo swapoff -a
Then, go back to booting Gparted. Let me know what happens.

---

### Post by dabl on 2007-09-20
You're permitted up to 4 primary partitions on a hard drive, so I don't understand why an extended partition has been made as the second one.  :confused:

YES, the "!" is because it has the "Logical Volume Manager" flag on it. See the little "lvm".

I would delete the whole deal as it is now, and make 4 new primary partitions as follows:

1.  6GB for "/"
2.  0.5GB for "swap"
3.  10GB for "/home" (assuming that's enough for your Linux-only data files)
4.  the rest of it (about 58GB) for "/shared_data" to share with Windows.  This one can be formatted NTFS, or FAT32, but NTFS is a little more rugged under crash/hard reboot conditions.

:guitar:

---

### Post by Pumalite on 2007-09-20
I would give '/' at least 10 GB and give /home at least 15 GB. Swap is OK,

---

### Post by G-Dawg on 2007-09-20
Tried that.  Didn't change any available options.  Still have the option of resizing my puny boot partition but not on the extended (larger) partition.  I wish I had a better understanding of linux filesystems to know what I'm dealing with here!  Appreciate the help though.

---

### Post by dabl on 2007-09-20
Well, if you're familiar with Windows, you know about FDISK, right?  If that is the second drive in your PC, boot Windows, open the "DOS prompt", and FDISK D:

:)

Then boot your GParted Live CD, and make 4 new partitions as recommended, and you'll be on your way.

:guitar:

---

### Post by G-Dawg on 2007-09-20
doh i bought the laptop from system76 the whole point being they would have it all good to go since this is my first major experience with linux.  But I'm just having so many problems with things its a bit of a nightmare in terms of time it takes to try to figure out things like synce and bluetooth.. ideally i wouldnt even need another partition for windows but its just not looking practical to rely on ubuntu alone atm.  but if i wipe it clean that kinda defeats the purpose of buying it from them.  hmm i know there is actually a ubuntu cafe in the city near me so i might bring it in there and get some hands on help..

---

### Post by Pumalite on 2007-09-20
We have to go to major surgery it seems. Backup /home in Ubuntu, including 'Hidden Files'(to external drive or DVD's). Boot Gparted and delete all partitions first, then make one large partition formatted ntfs. Install Windows. (XP I assume), defrag several times; then boot Gparted and right click on XP partition, in the menu, choose 'resize partition'. Then install Ubuntu and install Grub to MBR.

---

### Post by G-Dawg on 2007-09-20
Ok looks like I'm not the only one with this problem: [http://system76.com/forums/viewtopic.php?t=3409&highlight=dual](http://system76.com/forums/viewtopic.php?t=3409&highlight=dual).

Oh well I guess you're right I have to reinstall.  Thx for the advice anyway.

---

### Post by Pumalite on 2007-09-20
So, an LVM install??? Kind of creepy. Why on earth would they do that?
You can follow my recipe, have a REAL install and you could have XP and Ubuntu. In these dual boot deals is better to install Windows first(It likes to be sda1) and then Ubuntu with Grub in the MBR. You would have the best of both worlds(if you ask me windows sucks). I read your link and what they sold you keeps you as much a prisoner as a windows user. It's not worth it. The whole point of having Ubuntu is that you are free to do what you want with your system. Think about that.

---

### Post by G-Dawg on 2007-09-21
Wiped it clean; installed xp on ntfs; then ubuntu with the partitions you recommended; worked great :>

thx for the help!

---

### Post by Pumalite on 2007-09-21
You are welcome. Glad it worked for you!

---

