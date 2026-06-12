---
title: "Daily alternate CD hangs at language selection"
date: 2009-01-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-01-11
I wanted to test out the latest daily 64-bit ISO of Jaunty and I downloaded the alternate CD (mostly because of the problem with not being able to use the manual partition option on the Live CD, as stated in the release notes). However, I cannot get past the language selection screen because the keyboard does not respond, and the only way out is to hard reset the PC.

The last message to appear before the install screens appear is:
```
Memory length for this resource is less than required
```

The live CD works fine on Virtualbox, but I want a clean install on my current Jaunty partition.

Any suggestions or way to log the console output before it becomes unresponsive?

---

### Post by LordVeovis on 2009-01-11
> **tghe-retford said:**
> I wanted to test out the latest daily 64-bit ISO of Jaunty and I downloaded the alternate CD (mostly because of the problem with not being able to use the manual partition option on the Live CD, as stated in the release notes). However, I cannot get past the language selection screen because the keyboard does not respond, and the only way out is to hard reset the PC.

The last message to appear before the install screens appear is:
```
Memory length for this resource is less than required
```

The live CD works fine on Virtualbox, but I want a clean install on my current Jaunty partition.

Any suggestions or way to log the console output before it becomes unresponsive?

Can you boot off the CD to a terminal? If so does the keyboard work?

EDIT: Try passing the 'single' option to the kernel

---

### Post by tghe-retford on 2009-01-11
> **LordVeovis said:**
> Can you boot off the CD to a terminal? If so does the keyboard work?

EDIT: Try passing the 'single' option to the kernel
Nope, can't get to a terminal and the single option just brought me back to the language section screen without being able to use the keyboard. As a side note, the same thing happens if you select the rescue mode option.

---

### Post by Gina on 2009-01-11
I have exactly the same thing.  Since it seemed to be tied in to keyboard actions I decided to try an old PS2 wired keyboard instead of my USB wireless keyboard.  Having plugged this in and restarted the install proceeded past the language selection.  In fact it went right past all the setting up and into the "Installing Software" phase (having installed the base system).  However, at 1% it stopped with a message "media change" and "Insert the CD labelled (I can't quite remember exactly but... ) it referred to Alpha and included the date "(20090111)" which is totally different from the real label.  Only button was "Continue" which after a brief glimpse of the progress box returned to the message box.  Only option then was to power down.  This was using my AMD64 with the 64 bit Alternate CD image burned onto a DVD+RW disc.  I used manual formatting to use a separate / and /home partition made with gparted earlier and then formatted ext3.  In the installation I chose those partitions and set to use ext4.  The partitioning and formatting appeared to go fine.

Earlier today I installed Jaunty in ext4 partitions as above on an old desktop (as mentioned in the ext4 thread).  At first I used a DVD+RW and had exactly the same problem as above (using the PS2 wired keyboard which came with it) ie, stopped at 1% of installing software with the media change message.  So I tried a CD-RW and the installation went straight through to completion.

Maybe the next thing to try with my AMD64 is a CD-RW instead of DVD+RW.

So I seem to have found two problems:- 
1. Alt CD install has problems with USB/wireless keyboard
2. Part way through installation from DVD it thinks the media has changed and won't continue.

As it stands the cause is pure conjecture on my part and I feel at a loss as to how to post on launchpad.

---

### Post by tghe-retford on 2009-01-11
> **Gina said:**
> So I seem to have found two problems:- 
1. Alt CD install has problems with USB/wireless keyboard
2. Part way through installation from DVD it thinks the media has changed and won't continue.

As it stands the cause is pure conjecture on my part and I feel at a loss as to how to post on launchpad.
That first problem will definitely be a regression, because I have done a alternate install (I prefer a clean barebone system) with Intrepid and my wireless keyboard worked perfectly fine.

Both problems are separate and would need to be filed separately.

---

### Post by Gina on 2009-01-11
1. I installed Alpha 1 of Jaunty on my AMD64 with no problem with USB wireless keyboard.  Alpha 2 no joy at all.

2. Just tried a CD-RW on same machine and it stops too - same place as with DVD+RW so it's not ***just*** a matter of the media.

system CD. DVD
32bit.. OK. bad
64bit.. bad bad

---

### Post by tghe-retford on 2009-01-11
I started a bug report for the USB/Wireless keyboard problem. I hope its fine:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/316205](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/316205)

EDIT: From my limited knowledge, the DVD media change problem could be filed under the same package I filed my bug under.

---

### Post by Gina on 2009-01-11
> **tghe-retford said:**
> I started a bug report for the USB/Wireless keyboard problem. I hope its fine:

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/316205](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/316205)Thank you - that looks fine.  I'll add my confirmation.

EDIT - Done.

---

### Post by ronacc on 2009-01-11
hang in there , back at  the end of dec there were several dailys that wouldn't install , both destop and alternate (64bit) I had nuked my original install and it took a few days to get one that would complete .

---

### Post by ShirishAg75 on 2009-01-11
Another things you guys could do is also report or/and get attention at the qa testing corner.  Few URLs to help you out. 

[https://wiki.ubuntu.com/Xubuntu/Testing/TestingInfo/Short](https://wiki.ubuntu.com/Xubuntu/Testing/TestingInfo/Short)

[http://iso.qa.ubuntu.com/qatracker/build/ubuntu/all](http://iso.qa.ubuntu.com/qatracker/build/ubuntu/all)

[http://iso.qa.ubuntu.com/qatracker/testcases](http://iso.qa.ubuntu.com/qatracker/testcases)

[https://wiki.ubuntu.com/Testing/ISO/SmokeTesting](https://wiki.ubuntu.com/Testing/ISO/SmokeTesting)

[https://wiki.ubuntu.com/UbuntuAutomatedTesting](https://wiki.ubuntu.com/UbuntuAutomatedTesting)

[http://iso.qa.ubuntu.com/qatracker/report](http://iso.qa.ubuntu.com/qatracker/report)

[https://wiki.ubuntu.com/Testing/ISO/SmokeTesting](https://wiki.ubuntu.com/Testing/ISO/SmokeTesting)

[https://wiki.ubuntu.com/UbuntuAutomatedTesting](https://wiki.ubuntu.com/UbuntuAutomatedTesting)

This would make sure that the people who need to know and the bugs themselves will get proper attention.

---

### Post by ShirishAg75 on 2009-01-12
A much more interesting link. 

[https://wiki.ubuntu.com/ScalableInstallationTesting](https://wiki.ubuntu.com/ScalableInstallationTesting)

---

### Post by Gina on 2009-01-12
Thank you for those links :)

---

### Post by Mutiny32 on 2009-01-14
Exact same problem here, USB keyboard won't work on alternate installer. Still exists on the latest daily build.

---

