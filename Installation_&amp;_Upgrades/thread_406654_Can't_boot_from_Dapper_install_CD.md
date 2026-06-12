---
title: "Can't boot from Dapper install CD"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by Metz on 2007-04-11
I've got an old (read very old) Gateway 2000 tower that I want to use as a spare server on my network...to take some pressure off my main machine which acts as webserver.

The problem is, it refuses to boot from the Dapper install CD (official, not ISO download). However, I tried an old (read very old) RedHat CD, and it works fine. Problem is, the installation i'm left with is useless as I can't setup net access (apart from dialup!!) .

I'm by no means a noob....but hardware is still a dark art in my book ;). I'm guessing that my BIOS is so outdated, it's not recognising the dapper CD as bootable, or something along those lines. There's no USB on this box, and ever if there was, no option to boot from USB in the bios.

I've also been unable to find BIOS updates that I can install (even if I had the means to do so, as most of them need windows to run, I'm told).

Any ideas how I can rescue this machine into something remotely useable? Is it simply too old and destined for the scrap heap?

---

### Post by ajgreeny on 2007-04-11
It may be that the machine will not boot from CD at all.  Get a copy of smartbootmanager and run it from a floppy if you have one on the machine.  That will allow you to boot from a CD that refuses to boot normally.  A search on google will find where you can download it and how to copy it to a floppy that will boot.

---

### Post by Metz on 2007-04-11
Cheers Ajgreeny...I'll try that. Although, it did infact boot fine from the old redhat boot CD. There appears to be something different about the formatting of older CDs vs newer ones. Possibly FAT16 vs FAT32, or something like that. But like I said, I'll give it a go :)

PS: just found this... [https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto) :)

---

### Post by Metz on 2007-04-12
OK...I've been trying sbm for a hour now. Still nothing.

I made up the sbm disk (it worked on the 2nd attempt), and when I boot up, it presents me with the CD option. I select it from the list (it's got an asterisk to the left of it). I get a "Disk Error 0xAA". I've read up what I can, and it says to keep pressing it. 

Guess what I've been doing for the past hour ;):)

Thing is, it still boots fine into the Redhat CD that I have...but nothing else. I just don't get it.

---

### Post by ajgreeny on 2007-04-12
Sorry, I don't think I can help any further.  SMB usually seems to do it OK so have you checked the CD in another machine?  Perhaps it is the CD itself that is the problem.

---

### Post by Metz on 2007-04-13
Yup, any of the CDs I've tried boot fine on both machines either side of this one in the 'server cupboard' (cupboard under the stairs ;)).

Looks like this could be a lost cause then....

How about this :-

a) Could it possibly be caused by the speed at which the cd is written? IE: Should I re-write the alternate CD at x1...it was done at x4, I beleive. But as it boots on other machines, I guess that's not it.

b) As I've managed to install RedHat on that box (all be it a very very old version...7.1, pre 2000, I think), is it possbile for me to copy some files onto the machine, modify some boot files, etc, so that when it boots, it actually boots into the install?? I've given it some thought, and it seems to me that it should be possible, but it's way beyond my level to actually figure it out. I'm pretty sure that the Ubuntu CD can be read once I boot into RedHat.

---

