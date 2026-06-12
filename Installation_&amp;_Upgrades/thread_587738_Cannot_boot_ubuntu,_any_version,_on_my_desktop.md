---
title: "Cannot boot ubuntu, any version, on my desktop"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by AceMilo on 2007-10-23
I've always just installed ubuntu on my laptop and never had a problem, but my desktop was windows only.  My windows install has been sluggish and is in need for a format and I wanted to format and put ubuntu 7.10 on there as I love it on my laptop.  Here's the problem.  I wanted to test the live cd to make sure my hardware was compatable before installing.  I set my bios to boot to cd, pop it in, and I get greeted with the menu, ie install or run live cd, boot off hard drive, etc.  So, I click install/run live cd and it loads the kernel and the screen goes black and I get a _ in the upper left corner flashing in an infinite loop.  I thought the cd was bad so I popped it in my laptop and I saw the same _ but it quickly went away and began to boot.  I thought maybe 7.10 wasn't gonna work so I popped in an old 6.10 cd, same thing.  I tried a bunch of boot options and nothing works.  Again, the problem is that after selecting run install/live cd it just sits at a black screen with a _ in the upper left corner and I never get to the ubuntu splash screen.  Please, I really want to ditch windows as my main os, but I won't use anything but ubuntu.  Any info at this point would be appreciated.  My laptop runs fine and it boots off all of the cds so I know they are good.

TIA

---

### Post by avik on 2007-10-23
Can you tell us the specs for your desktop?  It's possible your desktop can't load the LiveCDs, and in that case, you'll want to us e the alternate CD with the text-based install.

---

### Post by AceMilo on 2007-10-23
I have been able to boot other livecd's in the past, such as knoppix.  Here are the specs:

ASUS P4P800 Deluxe mobo
P4 2.6 800mhz fsb w/ hyper threading
Nvidia 6600 agp 8x video card
Samsung 20" widescreen monitor
CDRW
DVDRW
Floppy
250GB hard drive
120GB hard drive

I tried disconnecting the hard drives, usb devices, and all but 1 cdrom and it still does the same thing.  I tried to boot it off a dvd and a cd, still nothing, it just sits with the _ in the corner flashing infinitely.  Thx for the quick reply btw.

---

### Post by AceMilo on 2007-10-23
*bump*

I still need help with this, I can't find anyone else with the same problem.  Thx again.

---

### Post by AceMilo on 2007-10-24
*bump*  Sorry to keep bumping but I really want an answer otherwise I can't use ubuntu at all on this system.

---

### Post by littlefireb on 2007-10-25
I did have the same problem as you have in my laptop, after I selected the start or install, it halts with "_" flashing.
After searching for many posts, i still cannot find any solution.
I just try to put the live CD in my desktop, when booting with the CD, I said check sum error, so I guest is the CD error. (I have burnt 3 set with different version)

Then I burn the CD again with my laptop, and it works finally. you may try if this works with you.

---

### Post by AceMilo on 2007-10-25
Thx for the reply.  I burned the alternate cd and it does the same thing.  I tried the dvd that I used to install it on my laptop (which I know works), and it does the same thing.  I'll try popping the cd in my laptop to see if it passes but I have a feeling it will pass.

Testing now:...... No errors found.  The cd is fine.  Any other ideas?  I really want to get this working.

---

### Post by bobyy on 2007-10-25
Hy
try to send ALT+F1 vhen it start blinking...i am in the same situation and for me it works...

---

### Post by AceMilo on 2007-10-25
Tried alt f1, doesn't do anything.  Any other ideas?

---

### Post by littlefireb on 2007-10-25
Maybe you can try to brun a new disc with you laptop, which ou want to install the ubuntu on it, with low burning speed. For me I use 24X burning with my laptop.

Now I have 3 OS in my laptop, XP, Vista, ubuntu, using the vista BCD as the master boot.

---

### Post by AceMilo on 2007-10-29
BUMP Still having the issue, tried with multiple cds, multiple versions, and multiple versions of ubuntu (6.06, 6.10, 7.04, 7.10) and they all do the same thing.

---

### Post by strider22 on 2007-10-29
I have found that using 1X recording works in a lot more machines than even 2x burning.
I use infrarecorder [http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/) when burning from windows because it allows burning at 1X.

---

### Post by AceMilo on 2007-10-30
I found a fix, but its not working:

[https://wiki.ubuntu.com/Asus_P4P800](https://wiki.ubuntu.com/Asus_P4P800)

I put in the switches but it still doesn't boot.  It's getting to the point where I'm like screw it and just gonna stick with windows.  I really love ubuntu, I use it more or less exclusively on my laptop and wanted to switch my desktop too, but I don't know if that's gonna happen.  I can 100% confirm its not a burning issue or a disc issue, it's gotta be a hardware issue.

---

### Post by jso2897 on 2007-10-30
This is a long shot, but something you might want to do is check with the mfgr and see if there is an update to your BIOS. Flashing the BIOS can sometimes fix booting problems - I had an old Dell that would boot Dapper - but not Fiesty or Gutsy. After I flashed the BIOS,no prob. But that was also an old computer, and the BIOS update was recent and had many fixes. It's not as likely to help a newer machine like yours.:(

---

