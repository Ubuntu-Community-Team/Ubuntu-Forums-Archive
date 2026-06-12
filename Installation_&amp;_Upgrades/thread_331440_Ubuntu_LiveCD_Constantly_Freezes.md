---
title: "Ubuntu LiveCD Constantly Freezes"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by matthewsage on 2007-01-04
I have been trying to install Ubuntu on my desktop, but the installation has failed each time.  The first time it froze at the "Booting Kernel..." prompt.  Then it froze twice on the logo screen with the bar moving back and forth under the logo.

After those failures I burned a new Installation CD and also found the thread discussing how to change the xorg.conf file to use the "vesa" driver instead of the Ati driver.  After that the monitor stopped receiving a signal (went blank) and the installation froze.  Here are my computer specs:

AMD Athlon 64 X2 4200+
2 gb DDR ram (PC3200)
Asus A8R-MVP motherboard
ATI Radeon x80o GTO2 Video Card
250 gb SATA Western Digital Hard drive & 320 GB Seagate SATA
NEC 3550A 16x DVD-RW drive

I would really like to use Ubuntu.  I've installed it on other machines (Dell) with ATI graphics from this same install CD, no problems.  I've installed Edubuntu, Suse, and Fedora.  I just can't seem to get this install CD to function.  I'm downloading the Kubuntu DVD now, but I may have to go back to an openSuse install.

This will be a Windows XP dual boot system after I partition the main hard drive.

Thanks for your help!

---

### Post by riven0 on 2007-01-04
Are you using the 64bit installation cd? If so, you may want to try the 32bit; I heard that works for some people.

---

### Post by Ciego on 2007-01-04
Check out this thread .... A few of us have had a similar issue.  Hope it helps.

[http://www.ubuntuforums.org/showthread.php?t=272490](http://www.ubuntuforums.org/showthread.php?t=272490)

Make sure the jumpers(try not to use Cable Select) and cables are all connected correctly and if that doesn't work, try using another optical drive to install.

Also make sure that your install disk has no errors using the check utilty when it boots up.  Just another note ... it is advised to burn the disks at a slow speed.

---

### Post by matthewsage on 2007-01-04
Thank you for the quick responses.  I am in fact using the 64 bit CD, and am downloading the 64 bit DVD.  As I plan on doing some heavy rendering (ie blender) I was really hoping to use the 64 bit rather than the 32 bit.

The installation CD I'm using was able to install on a different system so it is probably okay, but running the "Check CD" option at the boot menu causes the exact same freeze/crash.  I will have to check the cables/jumpers as the optical drive sounds like it might be the problem.  I can't think what else could be causing the hang up.

Has anyone had luck with an installation without using a CD?  I saw links for a network install, etc.  I have a very fast internet connection (15mbps down/ 5mbps up) so maybe I could do an internet based install?

---

### Post by Ciego on 2007-01-04
This probably won't help much but here is another thread that I posted to concerning a similar problem.

[http://www.ubuntuforums.org/showthread.php?t=268927](http://www.ubuntuforums.org/showthread.php?t=268927)

I would definitely try reburning the CD if it wont even complete the check.

---

### Post by matthewsage on 2007-01-04
@Ciego

Thanks for the thread.  I did an MD5 check on the iso I downloaded and burned 2 different copies, both of which gave me the same frozen install.

However, that thread you linked to provided me with another avenue of attack.  I do happen two have 2 different brands of memory in my system, both 1 gb DDR.  They are both the same speed and CAS latency, and are running in Dual Channel mode right now, but they are different brands.  Perhaps those are causing some problems...

---

### Post by Ciego on 2007-01-04
I would definitely take one out at least for the install.  I had that same issue and racked my brain for a few days on it and then about  kicked myself in the rear when I solved the problem.  

Install ran first time all the way through after that.  I never tried adding the ram back in after the install though.  Let me know if that works for you.

---

### Post by matthewsage on 2007-01-05
Kubuntu installation has also crashed in the same place now.  After multiple attempts I have been able to determine that the lock up occurs at:

OHCP (some string of numbers): new usb hub detected, registered at number 1

(Okay, so that's not verbatim, but it was definitely a usb thing)  I have about 8 usb ports, and the only usb device, so to speak, that is plugged in during the boot is a flash card reader.  It's one of those 21 in 1 read everything deals that mounts in a 3.5" spot.

Anybody know if those cause problems, perhaps a workaround?

---

### Post by Ciego on 2007-01-05
I believe that I have read something about card readers causing problems during new computer setups due to the way the drives are mounted.  Try unplugging the card reader and running the install.  If that works, you should be able to plug it back in after the install and it will mount correctly.

---

### Post by matthewsage on 2007-01-05
Well, I installed openSUSE 10.2 without a hitch on the machine last night.  It worked well as is now functioning.

I'm very new to Linux, I had tried Suse before, and I was hoping to try out Ubuntu this time around.  It's too bad, I think it must have been a hardware compatibility issue.  I've noticed a plethora of threads about this exact same issue over the last couple of days.  Everyone of the people who have posted have had an ATI graphics card.  It may just be coincidence, but maybe not.  The xorg.conf "vesa" fix is supposed to fix the ATI incompatibility issue, but it didn't work for me.

Well, wish me luck with learning Linux!8)

---

### Post by zionykl on 2007-01-05
I did have the same issue you were describing and I do have a ATI X1600 graphic card.

Sounds like I am going to openSUSE 10.2 already.

---

### Post by matthewsage on 2007-01-06
Well, openSuse 10.2 installs beautifully, except for one problem.  There are no ATI drivers compatible with Suse 10.2.  ATI has made any yet, and the oss drivers are not compatible either.  Something about Suse 10.2 using xorg 7.2.

So I'm off to try and load Kubuntu 6.06 instead of 6.10. ](*,)

---

