---
title: "Dual boot partition question from newbie"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by gsmith45 on 2009-11-23
Hi all.  
Sorry -  this is a dumb question from a non-techie newbie.  I searched the forums for answers but got confused by different opinions.  

I want to set up a dual boot system on my Samsung NC10.  There is one HD with three partitions and I've been happily using the NC10 to run XP for nearly a year.  It's got all my pictures and docs on it, but is slowing down a little now.  I'd like to add Ubuntu as a dual boot, but without losing anything from the disk, 

On my disk I have a small Recovery partition, a C: partition of 75GB, which I use for programs and for XP and which has about 16GB of stuff in it, and a D: drive of 75GB which I use for data (music, docs, photos) and has about 75GB on it.  There is no "free" unpartitioned space on the drive as far as I know.

I have downloaded the UNR version and have successfully run it from USB.  I bottled out at the point of the install where I got to the partitioning.  The instructions on screen are different to those in the general support documentation.  There is one sentence in particular in the support documentation that says that re-partitioning will cause my data to be lost.  Is this correct?  Although I have back-ups and disk images I really don't want to run the risk of losing everything and having to re-install.

I have de-fragged etc, but am now nervous about losing any data of having to re-install Windows. I've read various responses about trusting the installer from some people, and then other people recommending using Windows to re-partition.

Can someone suggest exactly what next steps to follow for UNR (which doesn't seem to have the "Guided" option for re-partioning in the on screen instructions).  Please be as pedantic as you want in your responses - step by step appreciated!

G

---

### Post by dhavalbbhatt on 2009-11-23
It seems to me that you have about 59GB space free on your C drive. What I would suggest you do is, de-frag your C drive and create 1) a root partition for Ubuntu (I wouldn't put more than 20 GB here) and 2) a swap area (about 2GB). You can continue using your D drive as your home partition for Ubuntu (basically all your documents, music, pictures, videos, etc. will live here and if your D drive is NTFS, it can be read by both Ubuntu and XP). 

With regards to UNR and USB, I am not sure how you would go about doing this, I have never used that.

---

### Post by gsmith45 on 2009-11-23
Thanks for the advice.  Can you point me somewhere that can talk me through how to do what you suggest?  Do I do it under Windows, or via the installer?  Also - if  I repartition my C: drive, do I lose all my data? (Which is what is making me nervous about all of this?)

G

---

### Post by darkod on 2009-11-23
To confuse you even further, one question: Have you also tried desktop 32bit to see how it looks and compare it with UNR?

I am asking because on my NC10 I went for UNR automatically but hated the way the menu looks and after 2 days installed desktop 32bit over it.

In case you are aware of the difference and you like UNR better, the first thing you need to check is whether there is program Gparted in System -> Administration? I don't remember because I used UNR only briefly.

I am asking because you would use that to shrink your D: for example, to make unpartitioned space for Ubuntu.

Also, you said all 75GB on D: are used if I understand correctly. You would have to move some data to external usb hdd or dvds because you can't shrink when all the partition is used up.

---

### Post by snowpine on 2009-11-23
Hi G,

There is some dangerous advice on this thread :) so you would be wise to [consult the *official* documentation]("https://help.ubuntu.com/community/HowtoPartition") and *back up all of your data* before proceeding! 

All software has bugs (including the Ubuntu installer) so there is a very small chance it will malfunction and overwrite existing data. There is a much larger possibility you will make a mistake as a new user (or follow some bad advice). So, back it all up to an external drive.

With the backup out of the way, and your drive defragmented from within Windows, you can proceed to install Ubuntu. The safest option is the "guided partitioning" option to resize your C: partition (which won't be called C: in Linux; possibly /dev/sda2) and install Ubuntu to the freed space (I recommend at least 10gb). This will automatically create the / (root) and swap partitions.

Don't use your D: drive as your Ubuntu /home partition; that's just crazy! (You don't need a separate /home partition anyway.)

---

### Post by audiomick on 2009-11-23
Hi.
Read today somewhere that it is a good idea to re-boot your windows at least once after shrinking the partition and before installing Ubuntu. This allows windows to run its' disc check stuff and get its' head straight.
I'm sorry I can't remember more details that this, but it made sense as I read it.

---

### Post by steven1664 on 2009-11-23
Dual booting, while not hard can screw up your computer if your not careful.  I would suggest imaging your laptop with something like clonezilla before you attempt to set up the dual boot so if you happen to make a mistake it won't be a big deal you can just put the image back on your computer.  

Once you have imaged your computer give installing Ubuntu a shot.  Just got through the install process and when you come to the spot to setup for your partition you can selecet to install them side by side or determine the amount of space you want to give ubuntu through the advanced section.  My advice to you would be to image your computer first though and just go through it and give it a try it is pretty simple to figure out, just make sure you have your image in case you make a mistake the more you try it the more comfortable you will be and the more it will make sense.

---

