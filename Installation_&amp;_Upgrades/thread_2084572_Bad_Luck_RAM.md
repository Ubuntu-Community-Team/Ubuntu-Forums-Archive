---
title: "Bad Luck RAM?"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by mof920 on 2012-11-15
:confused: Okay, so at first, I installed 12.10 on my VAIO just fine. Brand new hard drive since the one that was in had my partitions all strange. I didn't want to deal with it so in went the new one. I installed all nice and good via USB(I feel this might have been the problem, but hear me out.)

It installed and worked perfectly good for a while. Then, it froze. I shut it down and back up. It froze again for a while. I ran a memcheck on the next boot and I have errors at Test#7 [random number sequence] EXACTLY at 43% (this is important). So I thought, darn, need to replace RAM. Oh well. *replace RAM and test again* Fails same exact spot. I think, DAMN! RAM SLOTS! *clean with rubbing alcohol and each slot individually* Both fail. I thought, well hell, I'm SOL. 

NOW: I found my old laptop and powered Win7 perfectly fine and what not. I mess with it, then format and install Ubuntu 12.10 once again. Again, installs fine, works fine and BOOM! Freezes. Immediately ran the MEMCHECK and what do you know? Fails same exact spot as stated above. There's NO way I can be this unlucky. I mean, is it really my RAM, or did I do something wrong?

[This is my first time EVER messing with Linux in general.]

---

### Post by workaround on 2012-11-15
How much RAM do u have? You shouldn't be using rubbing alcohol, where do you get your ram:)   You should make sure your RAM is snapped in and that's it. Try reinstall-repair, that should take care of it.

---

### Post by QIII on 2012-11-15
Try this (From memory.  Sorry, I don't have any USB installation media handy):

Boot from your USB, pressing and holding any key during the boot process (after the post).

Press F6 (I think!), which should bring up a language menu.  Choose English or anything you care to.

You should get an option menu.

First choose "Check disk for defects" to check the install media (not the hard disk).  In your case, this will check the integrity of the image on your USB drive.

If the media check fails, you may need to retrieve the image again to make sure you have a good copy.

If all is well, select the "Test memory" option and run it from the USB device.

My guess is a bad install image.

---

### Post by mof920 on 2012-11-16
> **QIII said:**
> Try this (From memory.  Sorry, I don't have any USB installation media handy):

Boot from your USB, pressing and holding any key during the boot process (after the post).

Press F6 (I think!), which should bring up a language menu.  Choose English or anything you care to.

You should get an option menu.

First choose "Check disk for defects" to check the install media (not the hard disk).  In your case, this will check the integrity of the image on your USB drive.

If the media check fails, you may need to retrieve the image again to make sure you have a good copy.

If all is well, select the "Test memory" option and run it from the USB device.

My guess is a bad install image.

This is what I was told by a friend. I booted the USB into said menu, however, I see no option to check the disk. I see the test memory, but nothing more than boot main hard disk and install Ubuntu into hard drive. 

(Also, I'm installing the x64. Not sure if that makes a difference.)

---

### Post by mof920 on 2012-11-16
Okay, so I did the following: I moved from USB's to DVD's

I got gparted on one DVD and formated into NTFS. After I did this, I installed Ubuntu normally. The installation still froze. I REALLY doubt it's my RAM since this exact same issue is happening with my old laptop as well after I moved to that one and tried installing Ubuntu 12.10

I'm gonna try to get a Windows 7 disk and install that instead then check my RAM once more. I'll post results.

---

### Post by mof920 on 2012-12-07
Okay, this is what I did:

Re-Installed Windows 7 on both computers on freshly formatted hard drives. Both computers freeze up constantly. Ran MEMCheck and they keep failing. Mind this: I made sure the RAM was set on my VAIO as I did mess with that one. As far as my Dell goes, I NEVER touched the RAM before. This HAS to be a system error. I don't think it's faulty RAM since my Dell has never had issues. (Unless I really do have this much bad luck :cry: )

---

### Post by mof920 on 2012-12-07
I forgot to mention, the disk checked out perfectly. There were no defects.

---

### Post by mof920 on 2012-12-10
Bump

---

### Post by mastablasta on 2012-12-10
did you check the downloaded image and make sure it is a good one? : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
also you shouldn't install to NTFS (iot will cause problems).

---

### Post by mastablasta on 2012-12-10
did you check the downloaded image and make sure it is a good one? : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
also you shouldn't install to NTFS (it will cause problems).

---

### Post by mof920 on 2013-01-10
I did. I checked the disk several times to make sure my eyes wasn't playing tricks on me. I've given up on it for the past couple weeks. I'm gonna give it another shot (format and install) and see if it'll solve the issue.

---

### Post by mof920 on 2013-01-10
Okay, so I'm gonna format the drive into ext3 and reinstall Ubuntu entirely (again) using the CD (again) and see if that helps it any. I'll come back with results.

---

### Post by mof920 on 2013-01-11
So I did the following:

Burned a copy of Ubuntu and a copy of GParted. 

I first formatted the hard drive into EXT3 and shutdown. 

Then, I booted off the Ubuntu CD and started installing. Eventually (at the choose your avatar part) the set up froze. Well.. the entire laptop froze.

---

### Post by hubertofliege on 2013-01-12
I have a similar problem, and it looks like bad RAM is the culprit.

How do I fix this?  Do I need to replace the RAM?  Can I do this myself?  How do I find what kind to buy, and how to replace it?

---

