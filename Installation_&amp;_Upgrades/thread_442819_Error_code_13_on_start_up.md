---
title: "Error code 13 on start up"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by copracr on 2007-05-13
Hello all,  I've got a little question here.
  I tried out the live cd a few days ago (v7.04) and it worked great.  Most of the major hardware worked right out the box (including my ipod:) ).  My XP install was totally fragged so I reformatted the entire hard drive and reinstalled windows,  but  left 20gb as unused space.  I installed the ubuntu into that 20gb space and it worked great for a few days.
I tried to upgrade xp to sp2 and it kept crashing (no suprise there), and on the same day whenever I tried to sign into ubuntu it would sign me right back out.  It gave me a message like "your session lasted less than 10 sec....
I figured the updating was causing a problem maybe, and I like ubuntu and wanted more space for it,  so I reformatted.  this time I left 60gb (out of 120) as unused and installed xp.  I did all the updates it would let me to xp,  then turned off automatic updates.  Then I installed ubuntu ( I let the installer choose the partitioning) and it won't start up at all.  When I get to the grub menu ( I think that's what it's called ) and choose ubuntu it says "Error 13:invalid or unsupported excecutable form". 

Sorry if this is long,  but I have no idea how linux works and I'm not sure what would be relevant.  I've been with MS since ms-dos and just tried linux for the first time a few days ago when XP crashed again, so please treat me as a total noob.

(BTW,  I was braggin about this os to my g/f, so I have to fix it before she needs to check her email)

---

### Post by phidia on 2007-05-13
I think that error message  is "invalid or or unsupported executable format"  You can use the live cd and select rescue a broken system and/or reinstall grub. try that see if that does the trick.

---

### Post by copracr on 2007-05-14
> **phidia said:**
> I think that error message  is "invalid or or unsupported executable format"  You can use the live cd and select rescue a broken system and/or reinstall grub. try that see if that does the trick.

I reinstalled ubuntu,  but there was no change.  

On a different note,  I noticed that there were dozens of posts between now and last night when I posted this.  Is this software flaky or complicated?  Should I try a different linux for newbies since i've never had linux before?

---

### Post by Herman on 2007-05-14
Hello copracr,
Quoted from the [Gnu/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html")> 16 : Inconsistent filesystem structureThis error is returned by the filesystem code to denote an internal error caused by the sanity checks of the filesystem structure on disk not matching what it expects. This is usually caused by a corrupt filesystem or bugs in the code handling it in GRUB.                                        Try a file system check.

If you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/") you can boot that and right-click on the filesystem you need to check and select 'check' from the right-click menu. That will fix a lot of filesystem problems. A GParted LiveCD is free and only a small download (45 MB or so), and it is almost indispensable.
Keep clicking on the triangular buttons to keep expanding the window after the check is completed to see a report on what happened and what GParted had to fix. You might want to write some of that down even if it makes no sense to you, it might help someone help you later if that doesn't fix it. Especially write down any error messages if you get any.

If that doesn't work or you would rather use your own commands for filesystem checking, see this link [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm") and run a filesystem check with the Ubuntu Live CD.

> On a different note, I noticed that there were dozens of posts between now and last night when I posted this. Is this software flaky or complicated? Should I try a different linux for newbies since i've never had linux before? I think the amount of posting is because Ubuntu is so popular. I'm a little worried about your hard disk actually. Maybe it's on its way out, just guessing from the clues you have posted. Hopefully I'm wrong, but keep on backing up your data just to be sure. 
Well actually, you could still use Knoppix really well without any hard drive troubles at all, especially if you have enough RAM, I have a page about Knoppix, here: [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html") If you have a big enough external hard disk you could make a /home for Knoppix there and move all your info into that, then it would be safe if your hard disk really does go south. You can do the same with a Ubuntu LiveCD too, but it isn't as automatic for new users as Knoppix. 
I hope you'll stay with Ubuntu though. See what happens when you do a filesystem check and keep posting your news here and we'll try to help you as much as we can.
Regards, Herman :)

---

### Post by psusi on 2007-05-14
I assume that you only have one disk right?  Boot from the livecd and post the output of sudo fdisk -l.

---

### Post by copracr on 2007-05-14
Thanks guys,  I'll give that a try.
I should have noted my system specs though,  maybe that would have helped.
3.2ghz celeron D
Asus P5N SLI mobo
EVGA GeForce 7600 GT 
1.5 ghz PC4200 DDR2  RAM
120mb HD

You know,  I would be happy to run the live cd all the time,  but i'd like to save my email and web settings,  is that possible?

---

### Post by copracr on 2007-05-14
> **psusi said:**
> I assume that you only have one disk right?  Boot from the livecd and post the output of sudo fdisk -l.

Right,  just one disk drive.  What is sudo fdisk -l ?

---

### Post by psusi on 2007-05-14
It is a command.  Run it in a terminal window and post the output.

---

### Post by phidia on 2007-05-14
> **copracr said:**
> Thanks guys,  I'll give that a try.
I should have noted my system specs though,  maybe that would have helped.
3.2ghz celeron D
Asus P5N SLI mobo
EVGA GeForce 7600 GT 
1.5 ghz PC4200 DDR2  RAM
120mb HD

You know,  I would be happy to run the live cd all the time,  but i'd like to save my email and web settings,  is that possible?

Yes you can run the live cd and save your settings and home directory to a usb drive. Check out the link in my signature area for community docs/how tos.

---

### Post by copracr on 2007-05-17
> **Herman said:**
> If you have a [GParted -- LiveCD]("http://gparted.sourceforge.net/") you can boot that and right-click on the filesystem you need to check and select 'check' from the right-click menu. That will fix a lot of filesystem problems. A GParted LiveCD is free and only a small download (45 MB or so), and it is almost indispensable.
Keep clicking on the triangular buttons to keep expanding the window after the check is completed to see a report on what happened and what GParted had to fix. You might want to write some of that down even if it makes no sense to you, it might help someone help you later if that doesn't fix it. Especially write down any error messages if you get any.


I did this and it returned no errors.  I also ran a couple of utilities that came on a disk that came with the hard drive.  again,  no errors.  However, I ran the memcheck utility (not sure of the name) that came with ubuntu and i think it turned up quite a few errors.  Is this checking my ram? possibly the source of my headaches?

I also tried pclinuxos and it didn't work either, so I know there's gotta be something up with my hardware.

---

### Post by Herman on 2007-05-18
Error messages (in Windows), that might possibly (but not necessarily) be associated with faulty RAM modules include '*parity errors*', '*general or global protection fault*s', '*fatal exception error*s', and '*divide errors*'.
Before running memtest86+ you should go into the machine's CMOS (BIOS) settings first, and disable all caching, such as 'L1' and 'L2' or 'CPU Internal Cache' and 'External Cache'. Otherwise the memory test might not be testing the RAM modules at all, but the machine's CPU caches instead. Save the changes and reboot.
                          Then run memtest86+.
                          If you find any errors and you have more than one RAM module, remove all but one RAM module and test one RAM module at a time to determine which one is faulty.
Be careful of ESD and read up on how to work on your own computer first if you don't already know a lot about it, or get a good computer technician to do it for you. 
                          Often just removing and reseating the RAM modules can cure the problem if it is caused by dirt or a bad fit in the socket. (That has worked for me before).
                          Don't forget to go back into your CMOS (BIOS setup), and re-enable caching, and save the changes and reboot, otherwise your computer might run very slowly.
                                                                                         For more information on memtest86+,
                          [CENTER] [Memtest FAQ]("http://forum.x86-secret.com/viewtopic.php?t=2906"),   [Memtest86+]("http://www.memtest.org/#downiso"),   [Memtest forums]("http://forum.x86-secret.com/viewforum.php?f=15"). 
                          [/CENTER]
                                                                         
Regards, Herman :)

---

### Post by copracr on 2007-05-18
I couldn't figure out how to disable the cacheing,  but I pulled out the 512 ram module (left the 1g module in place) and reran the test with no errors.  I installed ubuntu and it's working great,  so far.  Wish me luck and thanks for the help fellas!

---

### Post by Herman on 2007-05-18
Okay, good! :) i GB of ram should be enough anyway. :)
Thanks for your feedback,
Regards, Herman :)

---

