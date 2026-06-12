---
title: "Installation problem. . ."
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by Bright_View on 2010-01-03
Hi all,

Just wondering if this sounds familiar to any of you:

Trying to install Ubuntu (or Ubuntu Studio) 9.10 on a computer that was given to me for free due to hardware problems.  I fix computers as a hobby, so I *think* I found the problem which was a faulty hard disk and bought a new one.

I have installed Windows XP on the system no problem.  I have also installed Ubuntu 8.04 twice, with no problems (currently posting from Hardy).

I cannot install either Ubuntu or Studio 9.10 on the system - it hangs at various places during the system install.  Sometimes it will give an error which states that there is likely a faulty cd/dvd, cd/dvd drive, or hard disk.  Sometimes it just hangs with no error.  

I have burned the disks using three different optical drives, and checked them with MD5 sums.  Makes no difference.  I have tried going through installation with two different optical drives.  Makes no difference.  I have tested the memory with memtest - everything looks good.

Is there any reason why Hardy would go on fine, but Karmic would not?  Or is this still a hardware issue?  Any thoughts would be appreciated.

Here are the specs of the system:

Mobo:  Asus P5KC
Proc:  Intel Core-2 Q6600
Memory:  OCZ 2x2GB PC2-6400 Platinum Edition
HDD:  Western Digital wd5001aals
Video Card:  Not sure - lspci says Radeon HD 2400 PRO beside VGA Compatible Controller, but the write up for that card says it has two DVI-I ports and my card has only one.
Bios settings:  Default
 
Thanks to everybody who clicks on this with the intention of helping.  I appreciate it greatly.

Cheers,

Dave.

---

### Post by Bright_View on 2010-01-03
Some more information:  I tried updating Hardy on the system through the network, and it hung while unpacking myspell-en-au.  I'm starting to think this is another hardware issue because I don't understand why it would hang doing that.  It'd just be one heck of a coincidence that it didn't hang installing either XP or Hardy twice with no problems.    

Anybody really good at isolating hardware issues with Ubuntu?  Usually I would just swap parts, but my other system is too old to be of much use to me.  I might try swapping graphics cards, and if I get really desperate I might try switching hard drives to see if my good hard drive with Ubuntu properly installed can run everything in this system, but that seems a bit dicey.  

Any help would be appreciated.

---

### Post by YYY123 on 2010-01-05
I'm in exactly the same situation. I was given a computer that didn't work because the battery that saves the BIOS settings had died. After replacing the battery and checking to make sure things were working as far as the hardware was concerned, I tried installing Ubuntu 9.10 as a fresh install on an empty hard drive.
 
The installation seems to go okay, and then hangs with a message popping up saying "the installer encountered an error copying files to the hard disk [errno5] input/output error". It also has the mention of the problem likely being a faulty optical drive, hard drive, or disc burned at too high of a speed.
 
I tried burning disks using slower speed, tried burning with two different optical drives, tried two different burning programs, tried three different brands of blank discs, tried downloading the iso file from three different sources, tried installing with two different optical drives, tried installing on two different hard drives, and the results were always the same. I checked the disks, and they all checked out fine. All of the hardware involved seems to work fine with everything else. I tried installing Windows XP from both of the optical drives tried, and onto both of the hard drives tried, and XP always installed and worked perfectly when I did.
 
I'm in the process of downloading the alternate installer from:
[www.ubuntu.com/getubuntu/downloadmirrors]("http://www.ubuntu.com/getubuntu/downloadmirrors")
 
Tomorrow I'll try again using that instead of the regular download of 9.10.

---

### Post by YYY123 on 2010-01-05
I downloaded, burned, and tried installing with the alternate installer, and it didn't work either. As a last try, I removed all of the RAM except for a single 1MB stick, and tried installing again using the regular installer, from one of the discs that had always failed before. It worked without any problem at all. I later reinstalled the other memory sticks back into the computer, and everything's working as it should be.

---

### Post by Bright_View on 2010-01-05
YYY123, 

Thanks very much for this reply.  I'll try taking one of the 2 GB sticks out of the mobo to see if that helps during installation.  This would be the first time I've heard of too much (good) memory being a problem, but I guess there's a first time for everything.

I'll report back once I've tried installing ubuntu studio for the 10000000000000000th time.

Dave.

---

### Post by Bright_View on 2010-01-07
Unfortunately, that didn't seem to help.  I was really hoping for a miracle, but no go.  I'm going to tear the computer apart and check it piece by piece.

---

### Post by Bright_View on 2010-01-26
Alright, I think I've finally got it figured out *knocks on wood*.  It seems that one of the memory modules is faulty, although not in such a way that it fails memtest.  This stick must have gone through about a dozen passes on memtest altogether, and has never had an error.  However, every time I try to install with it in place, I get the error stated above or a system hang.  If this particular stick is not in the system, I can install an OS (have tried both Karmic and Studio now successfully). 

I got the idea of checking out the memory in more detail from a friend who has much more experience fixing computers than I do, and he said almost every time there are errors during an install it's related to memory (provided the disk was burned successfully).  

So keep that in mind next time you're installing Ubuntu and get a reproducible error that you know is not coming from the disk drive or the install disk itself.  Could be your memory is faulty.

Thank goodness this is over.  Cheers everybody!

---

