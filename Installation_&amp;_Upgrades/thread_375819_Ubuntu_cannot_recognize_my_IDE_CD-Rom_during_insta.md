---
title: "Ubuntu cannot recognize my IDE CD-Rom during install"
date: 2007-03-04
forum: Installation &amp; Upgrades
---

### Post by jeff_p on 2007-03-04
Hello,

I have seen similar posts to this one, but none of the advice in them has helped me.

I have a brand new box here, ready to try Ubuntu 6.10 server.  The motherboard is an Intel BOXDG965WHMKR, with one SATA 500GB drive, and a Pioneer DVR-112D drive.  This optical drive should be recognized as a standard CD Drive, but the Ubuntu install process gives † the "No common CD-ROM drive was detected" error, which I cannot bypass.

I have tried adding "ide=nodma" to the install options, which did not make a difference.

I have tried changing the SATA settings in the BIOS so that the drive seems to be an IDE drive, like so:

In Drive Configuration:
ATA/IDE Mode:   <Native>
Configure SATA as  <IDE>
S.M.A.R.T.  <Enable>

and then my SATA disk is listed.

I'm not sure what to try next.  Will I be able to install Ubuntu on this rig?

---

### Post by jeff_p on 2007-03-04
A quick update...  I installed the 02/27 BIOS update from Intel, still no luck.  It looks like cdrom-detect cannot find my IDE CD drive.  

I will try downloading Herd 5 (Feisty Fawn) to see if this helps.  The problem seems to be with the JMicron controller, and it seems like it has been fixed only recently.

---

### Post by jeff_p on 2007-03-04
Feisty Fawn hasn't improved anything.  

I am going to try Gentoo or something else, to see if it can help diagnose what is happening.  I would like to use Ubuntu, however, and I will return to this distro if I can.

---

### Post by funesto on 2007-03-04
I've been having that problem too when using the Alternate CD... I've had just about every other error as well >.<

When I use the Desktop CD, it will either freeze when mounting the root file system or throw some error about not being able to access tty and just stop.

Anywho, if you find a solution or have any luck with other distros let me know :)

---

### Post by mgmiller on 2007-03-04
Try opening your case and looking at the jumper setting on the IDE optical drive.  Many of them are shipped today with the jumper set to "cable select".  Try changing it to Master.  You may need to remove the drive from the case to find the markings telling you which jumper settings are which.  They could be on a sticker on the top or bottom, or be embossed into the metal case itself.  Since you are using a SATA HDD for the Ubuntu drive, the optical drive should be the Primary Master.  That is, it should be jumped as Master and be on the IDE cable that goes to the First or primary IDE controller on the mobo.  These are often a different color, like blue, but this may vary with manufacturer.  Refer to your mobo manual for the layout of the IDE ports or perhaps it is silk screened onto the mobo itself.

---

### Post by jeff_p on 2007-03-04
Funesto, it seems like you're having a different problem.  I can't even get the Ubuntu installer to recognize the CD drive that its booting from :lolflag: 


Gentoo doesn't work either...  I have done some research, and it seems like there is a problem with the PATA controller on this board.  Apparently it isn't really supported under linux yet, though there are some patches available.  I have read in several places that Feisty Fawn supports this chip now, but I am still having no luck.

There is a thread here which gives some more details for the problem: [http://www.ubuntuforums.org/showthread.php?t=234706&page=30](http://www.ubuntuforums.org/showthread.php?t=234706&page=30)

---

### Post by jeff_p on 2007-03-04
mgmiller,

That is interesting...  I will try to change the jumper settings on the CD drive right now.  I'll let you know if it works!

---

### Post by jeff_p on 2007-03-04
Okay, I took a look.  The jumper on the CD drive was set to master all along.  It is the only item connected to the PATA cable, but I swapped its location just in case.  Still no luck...this is very strange!

---

### Post by mgmiller on 2007-03-04
In reading through the forum post you mentioned.  One person had luck changing the BIOS setting for legacy  USB support to disabled.  I know I have had to do that many times on different mobo's to get things working correctly.  Give it a try.

---

### Post by mgmiller on 2007-03-04
Another thing you could try, (costs money), would be to get a SATA DVD drive and bypass the whole IDE subsystem.

---

### Post by mgmiller on 2007-03-04
Another BIOS setting thing to try is the ACPI support.  You could try turning that off.  Although that might affect it's detecting a 2 core CPU.

---

### Post by jeff_p on 2007-03-04
mgmiller, thank you so much for your help!

Unfortunatly, I am still stuck...I tried disabling USB altogether, after removing legacy support didn't help.  Still no CD support.

I'm not ready to give up yet...many people have had this problem, and I'm sure that somebody has found a good solution!

---

### Post by mgmiller on 2007-03-04
From what I have been reading, your mobo has some real issues with linux and IDE drives.  The last thing I will suggest that is less expensive than buying a new SATA DVD drive is to get a SATA to IDE converter and stick it on the back of your IDE DVD Drive.  The whole point is to get the optical drive off the IDE controller..

Did you try the BIOS ACPI suggestion yet?

---

### Post by jeff_p on 2007-03-04
mgmiller...yeah, I tried that...no luck.  Apparently kernel 2.6.17 will support this motherboard, but I can't figure out how to make it work.  

I think that the problem is that I won't be able to find an installer that will see my CD drive, but I Bet I can get it to work _after_ I have ubuntu installed.  I am going to try to install using a USB drive that I have..I'll update this thread with the status of that process

---

### Post by mgmiller on 2007-03-04
Good Luck

---

### Post by louieb on 2007-03-04
Sometimes it just guess and God when you have to use cheat codes to get a Linux CD to boot on a given computer. The CD's  I've  had the best luck with have been Knoppix and DSL. I have found the [Knoppix cheat codes]("http://www.knoppix.net/wiki/Cheat_Codes") work with most distros.

---

