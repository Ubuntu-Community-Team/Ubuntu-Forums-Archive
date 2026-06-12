---
title: "Dual Boot and External Hard Drive - problems?"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by newyorkcityjay on 2007-04-28
Okay!  I'm new to the whole Linux thing, but I LOVE Ubuntu.

ATM my 4-year old laptop's hard drive is like swiss cheese.  I can install Feisty, and its fine, but if I restart it starts freezing and I wind up reinstalling to get working again.  It's bee frustrating.

I am going to buy a new laptop from HP with an AMD Turion dual core chip and 2 GB RAM.  I also have an external HD.  Although I love Ubuntu, I know I should keep Win VIsta around.  I found some tutorials to set up a dual boot, but it seems I would need to start by reinstalling Win Vista in order to repartition - is that right?  I also want to set up my external HD to be readable in both.  Do I need to format it as FAT32?

Right now, in Ubuntu, I can format the external to FAT32, but I don't know enough about partitions.  I can only get a single partition to allow me to read/write.  I can set up others, and mount them, but I can't write to them because the root owner has permissions.  Can someone help me out with a recommended arrangement of partitions on that drive?

---

### Post by ttakun on 2007-04-28
If you buy a new computer and you want to install Ubuntu on it setting up a dual boot, I don't really think you have to reinstall Windows Vista in order to repartition. Just defrag your HD, and install Ubuntu, and let it manage partitions.
About Linux partitions, I would advise you to make 3 of them, one for swap, another one for /, and the last one for /home.

About your external HD, you could format it in NTFS and read/write either in Windows or Linux. I have an external HD (Toshiba  300 Gb) with NTFS format and I have no problem reading/writting on that HD from both OS.

Have a look at this thread:
[ HOWTO: NTFS with read/write support using ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009")

And if you want to view your ext3 partition from windows, have a look at this program:
[explore2fs]("http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm")

---

### Post by newyorkcityjay on 2007-04-29
Thank you... I'll be trying that.  I was concerned I needed a new machine because of some hard drive problems on this one.  Basically every time I restarted after the initial bootup of a clean copy of Feisty something would freeze.  I concluded it was because something got written to bad sectors on the HD.  Eventually I removed all partitions and reset the disk label, then reinstalled and since then I've been fine.

I was worried about reading and writing NTFS from Linux.  I installed Automatix, but some users caution against doing this.  I would like to be able to access files in both OSes and do NOT like messing around with Wine.

---

### Post by WATERBOYsh on 2007-04-29
This is essentially what I am wanting to do too, except with a second internal drive instead of an external (plan on getting an external though so that my laptop can also read/write to it). I want winXP/Ubuntu on my main harddrive and all the data on the second. Right now my main is ntfs and has just XP and the secondary is just data and it is ntfs as well... so I should just be able to repartition my main and get Ubuntu on and not have any problems reading or writing to the other ntfs disk from inside Ubuntu?


[http://ubuntuforums.org/showthread.php?t=426845](http://ubuntuforums.org/showthread.php?t=426845)

---

### Post by ttakun on 2007-04-29
Before repartitioning make a backup copy of any valuable data. Also defragment your main HD.
If you want to repartition your HD *before *installing Ubuntu, you could try using the GParted Live CD [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
or Partition Magic, if you have it.
If your read other threads on this forum related to that, there are people who don't like repartition at all, and they prefer doing a fresh installation . But that's up to you.
I repartitioned my Toshiba laptop three months ago, and I had no problems.
About reading/writing ntfs partition, I have been using my external disk for about two months since I installed the ntfs-3g driver, and so far so good. So it should work with your internal HD as well.

---

