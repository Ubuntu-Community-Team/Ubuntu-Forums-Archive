---
title: "I need help getting Ubuntu"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by anticasper67 on 2006-12-15
I downloaded Ubuntu about a week ago, hoping to install it on my old, unused computer in my basement.  When I turned the computer on, I realized the hard drive had failed, so today I bought a new 160 gig Western Digital hard drive and put it in my old computer.  I partitioned the drive into 120 gigs and 40 gigs.  Then, I burned the Ubuntu image to a CD-R.  The first time I burned it, I used Sonic Record Now, and the only file that appeared on the CD was the iso.  When I tried it on my computer downstairs, it wouldn't boot from the CD.  

Then, I burned the CD exactly according to this guide: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)  When I tried to view the files this time, it said that they could not be viewed and it still wouldn't work on my computer downstairs.  Please help! 

The computer I'm trying to install it on is an old Gateway (one of the first to come with XP installed on it).  It has 256 RAM.

---

### Post by taurus on 2006-12-15
When you view the CD in Windows, do you see a few files and a few directories?  Also, make sure you go into the BIOS and change the boot order from harddrive first to CD-ROM first!!!  And if you have another computer, see if you can boot off of that CD...

---

### Post by anticasper67 on 2006-12-15
No.  On the Record Now burn, all I saw was the iso file.  On the "official" burn, it said that the CD could not be accessed.  I'll try booting the CD on this computer.  And my boot order is CD, Floppy, Network, Hard Drive.

---

### Post by taurus on 2006-12-15
Well, you need to burn that ISO as an image file, NOT a data file or you won't be able to boot.  Look in the menu to see if there is an option to burn it as image file and that is what you want to use...

---

### Post by anticasper67 on 2006-12-15
Wouldn't using the official guide solve that problem?  Or is there something I have to change in Infra Recorder to make it burn as an image file?

---

### Post by anticasper67 on 2006-12-15
I tried booting the CD on this computer, and it said the boot device was unavailable.

---

### Post by taurus on 2006-12-15
Why don't you look at this guide, skipping all the download part since you have already done that!  

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

You can download a copy of CDBurner XP for free...

---

### Post by anticasper67 on 2006-12-15
I couldn't find the notepad file it was talking about, but I already verified the iso using the hash checker program on the other site.  It's burning at 8x right now, which may have been my problem since I was burning at 40x before.

Edit:  Well, this time the iso burned correctly onto the CD and I can view the files and browser.  I'll go try it on the downstairs comp.  Thanks for all the help, taurus!

---

### Post by taurus on 2006-12-15
Yes, it is recommended to burn it at 4x although my machines can boot and install at 8x.

---

### Post by anticasper67 on 2006-12-16
I burned the iso correctly, and I can install Ubuntu, but I need some help figuring out about the "swap" and "root" parts of the install.  I only have two partitions on the computer: one 120 gig for Windows, and one 40 gig for Ubuntu.  I've read the guides on this site, but they didn't help much.  Do I need 3 separate partitions for Ubuntu?  Or is there a way that I can split up my 40 gig partition so that I can install both root and swap onto it?

---

### Post by taurus on 2006-12-16
Just tell the installer to use the 40GB (the empty one) and it knows what to do next...

---

### Post by anticasper67 on 2006-12-16
OK, right now I am on the Live CD for Ubuntu, and during the install process, it does not give me the option of choosing which partition to use unless I manually edit the partitions.  If I manually edit, I have to choose the swap/root options too.  How do I choose which partition to install on?

---

