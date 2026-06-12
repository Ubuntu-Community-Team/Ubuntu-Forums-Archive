---
title: "How to decide whether to update to 9.04?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yankeeDDL on 2009-03-27
Hello,

I’m relatively new to Linux: been using Ubuntu for about 4 months now. 
I have installed 8.10 and I’m now wondering if I should update to 9.04.
I read that 9.04 will have much better support for ATI cards (Ubuntu 9.04 beta out) and I did have a lot of difficulties getting nice performances on my HD 2600Pro.

I wonder though:
- am I going to have problems with the installed programs when I do the move? For example: 9.04 will include OpenOffice 3.0, but I have it already installed in 8.10 by adding the appropriate repositories.
In this specific case I do know that I should remove OO3.0 from the repositories … but I don’t know what to do with the other repositories that I added.
-	would I receive all the performance improvement anyway by keeping the OS up to date, or will there be features that I will have access to only if I move to 9.04?
-	will I retain all the settings (email accounts, email filters, bookmarks, preferences (e.g.: open MP3 with VLC instead of Rythmbox)) or will I have to re-setup everything?
-	I have successfully setup SynCE with my Axim: will I lose my sync data?

Just wondering if anybody wants to share his/her experience in the past and whether this would be recommended or not.

Thanks.

---

### Post by KCG102282 on 2009-03-27
As far as your extra repos they will get disabled during the upgrade and you will have to reenable them after the upgrade. With mt ATI 2400 HD card the proprietary driver didn't work, but lucily the open driver did, but no 3d acceleration. The main thing you want to do when deciding if you want to upgrade is that everything works that you need to work. My MP3 player isnt working with 9.04, but does with 8.10 which is why I am not upgrading until I know its fixed.

---

### Post by Mark Phelps on 2009-03-27
Sharing my experiences ...

Two machines: desktop and tablet PC.

Have been upgrading the desktop since 7.04, have not had any problems doing that.

Recently upgraded the tablet PC from 8.04 to 8.10 -- major problems.  Xorg didn't work right, xev didn't work right, totally hosed my pre-existing Open Office 3.0.1 installation.

So, based on my upgrade experiences, you may have major problems with Open Office.

General comments in this forum are to NOT upgrade, but instead, to install clean each time. That's a LOT of work if you've done a lot of customizing to your system.

Two things you can do (both of which I do):
1) Image off your existing Ubuntu installation.  I use P.I.N.G (from windowsdream.com).  This way, you can do an in-place upgrade and, if you get any MAJOR problems, you can restore your working version.
2) Dual-boot your system to install the new version in a different partition.  I do this if 1) goes badly so I can work on the new version to get it working properly before I cut over.

---

### Post by yankeeDDL on 2009-03-28
Hello, thank you both for the tips.
I am relatively new to Linux, so I think I'm going to stick to 8.10 for some more time.
I do have also 8.10 in a Virtualbox on my laptop and perhaps I will "play" with it to go to 9.04.

Again, thank you for your suggestions.

---

### Post by Ranimator on 2009-03-28
I tried to update from 8.10 to 9.04 beta on a machine my kids use and I can't get into Ubuntu. (Starts but gets some error and just stops there.) 

Is there any way to use the LiveCD to get into the old filesystem so I can copy the kids' files off before trying a complete new install?

---

### Post by oserdavid on 2009-03-28
I'd just like to say that on a dual boot machine, with Windows Vista and Ubuntu Hardy Heron via Wubi - I took the very risky plunge and Alt+F2'd into Upgrade Ubuntu - not knowing whether it would work within Wubi-for-Hardy, not knowing whether it would bugger up Grub and cause all sorts of problems for me still operating dual boot - stupid, or what? But it worked beautifully! 

I love Jaunty (9.04) - after a little bit of fiddling with repositories, Flash, Pulse Audio, Skype (which anyone can find out how to do by Googling these and other forums - but I found [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html) exceptionally useful) I have, so far had very few problems: one crash on C-Span Live Video trying to 'Open with Movie Player - necessitating a hard restart. But it's great. If you don't mind a bit of fiddling (and provided you are not going to be totally dependent on this Beta for all your Internet use) I'd thoroughly recommend it.

And - by the way - OpenOffice worked fine.
David

---

### Post by Ranimator on 2009-03-28
I'm still getting the error with my 9.04 upgrade which appeared to go smoothly until the part when you restart the computer and now when I restart the computer:
[LIST]
[*]Boots
[*]Grub loads
[*]Ubuntu logo is displayed with progress bar
[*]System hangs and displays text on the screen. (The final lines indicate it's checking the battery and then doing APM. There is an asterisk a few lines above that's colored orange rather than th standard.
[/LIST]

I'm looking for either: 1) help on getting 9.04 working, or 2) ways to use the LiveCD to get files off the system before just installing over the top of everything. (The above happened when I tried doing an upgrade.)

Thanks for any suggestions.

Randy

---

### Post by infoseeker on 2009-03-29
deleted

---

### Post by unelsson on 2009-03-29
I'm concerned about stability issues, since I have some serious stability problems with Ubuntu 8.10. Would upgrade to 9.04 perhaps make my computer more stable, or am I headed towards catastrophic situation by upgrading already unstable system?

I suppose I'll wait until we hear some experiences from upgrades from stable computers with Ubuntu 8.10..

Here's a post about the differences of upgrading vs reinstalling, perhaps the reinstall is better if I have already trouble with stability.
[http://ubuntuforums.org/showthread.php?t=1109358](http://ubuntuforums.org/showthread.php?t=1109358)

---

### Post by Mark Phelps on 2009-03-29
Generally speaking, if you have instability problems at present, a clean install will produce better results. But a clean reinstall (of the same OS version) could also produce a more stable machine.

I don't think anyone is going to be able to predict accurately in advance whether (1) your machine will be more stable or (2) whether you will have any problems from the upgrade.  The reason for (1) is that we simply don't know what is causing the instability; so we have no way of knowing if an upgrade will fix it.  The reason for (2) is that the developers sometimes make major changes between upgrades that "break" things that used to work.

I found the second to be true when I upgraded my tablet PC from 8.04 to 8.10.  Had major problems with all kinds of stuff simply not working anymore.  Was able to fix some of it; others are simply not fixable. Had to restore to 8.04 to get a working system back.

Which is why I always provide the same advice: either (1) image off your current installation to an external drive so you can restore it if the upgrade goes bad, or (2) install the upgrade in a dual-boot setup so you can work on resolving any upgrade issues while you still have a working version.

---

### Post by Ranimator on 2009-03-29
Is there any way to access files already on my system after booting up from a LiveCD?

Randy

---

### Post by Mark Phelps on 2009-03-30
Sure ... Places should have icons for all your "drives".  Simply double-click one to open a Nautilus panel for that "drive".

---

### Post by andrewabc on 2009-03-30
> **unelsson said:**
> I'm concerned about stability issues, since I have some serious stability problems with Ubuntu 8.10. Would upgrade to 9.04 perhaps make my computer more stable, or am I headed towards catastrophic situation by upgrading already unstable system?

I suppose I'll wait until we hear some experiences from upgrades from stable computers with Ubuntu 8.10..

Here's a post about the differences of upgrading vs reinstalling, perhaps the reinstall is better if I have already trouble with stability.
[http://ubuntuforums.org/showthread.php?t=1109358](http://ubuntuforums.org/showthread.php?t=1109358)

If you have bad stability and problems with 8.10, definitely try 9.04 livecd to make sure everything works.

Even if still going to use 8.10 until 9.04 final, you should still download/burn 9.04 beta livecd to make sure most things work without installing it. If something doesn't work, search forum to see if others have same problem. If no one else does, then create a thread getting advice, and eventually open a bug.

---

### Post by Ranimator on 2009-03-30
> **Mark Phelps said:**
> Places should have icons for all your "drives".  Simply double-click one to open a Nautilus panel for that "drive".

I'm able to see the drive, but I don't know how to find or access the files from my original Ubuntu 8.10 "home" directory. (If I can find them then I think I can back them up and just do a fresh install to see if that solves the problem where my system won't boot since trying the Upgrade.) 

Thanks for the suggestions.

Randy

---

### Post by emarkay on 2009-03-30
I did the upgrade to see if there were any testing issues via that route.  So far all seems stable, and functional.

---

### Post by mhenriday on 2009-03-31
I updated to 64-bit **Jaunty** from **Intrepid** when the beta version was released. Both my **OOo 3** versions, (OOO300m 15 Build:9379 and OOO-dev3.1.0 m7 Build:9393, respectively) seem to be functioning perfectly. I had to redo some repositories, and as I am blessed with a **Creative Soundblaster X-Fi** videocard, I was forced to reinstall the **Creative 1.00** driver according to **NullHead**'s excellent [guide]("http://ubuntuforums.org/showthread.php?t=870001"). These things done, **Jaunty** works as least as well for me as **Intrepid** did - with one exception (so far) : as detailed on this [thread]("http://ubuntuforums.org/showthread.php?t=1111175"), I can't get **SCIM** to cooperate with **Gmail**....

Henri

---

