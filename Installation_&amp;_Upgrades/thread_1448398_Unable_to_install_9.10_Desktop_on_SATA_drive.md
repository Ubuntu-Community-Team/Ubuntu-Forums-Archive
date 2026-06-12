---
title: "Unable to install 9.10 Desktop on SATA drive"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by kphill on 2010-04-06
I am new to Ubuntu although I have used another Linux version for several years.  I wanted to try Ubuntu after a couple of people recommended it to me.

I am trying to install 9.10 Desktop, i386,  on a 500GB SATA drive.  The computer uses AMD dual-core processors.  I can't remember the type of motherboard off-hand; it might be an Abit.  The drive has been zero-filled from previous installations of other operating systems.  (I have also tried installing the 64-bit version.  When I try this, I get a black screen with the cursor blinking in the top left-hand corner for several minutes before the screen goes blank.  In this situation, the harddrive light stays lit continuously as if the drive is stuck.)

When I boot the computer I get the screen to choose the language.  Then I get the screen for the various options (run without changing the computer, install, etc.).  When I hit "Install", I get a screen with the Ubuntu logo in white which "pulses".  After a few minutes of this the screen goes completely blank and there is no more activity.  I have tried choosing other options without success.  

I just wondered if there were any known issues with installing Ubuntu on SATA drives or if this is being caused by some other issue.

Thanks very much.

---

### Post by goldshirt9 on 2010-04-06
i had a similar problem.
i couldn't install unless i ran the live cd and then booted from the desktop option.
no idea why but it worked for me.
i have similar spec to you so try that.

if you cannot run into the live desktop then burn at a slower rate

---

### Post by oldfred on 2010-04-06
First does BIOS see the drive? One user said he did not have it on, but I did not know there was such a setting, but it could be just setting it to IDE. The new versions seem to follow BIOS settings more where older versions and windows may have ignored them and worked anyway.

---

### Post by quadproc on 2010-04-06
> **kphill said:**
> 
...
I just wondered if there were any known issues with installing Ubuntu on SATA drives or if this is being caused by some other issue.

Thanks very much.
The system that I am using right now is running Ubuntu 9.10 with three internal SATA drives and sometimes one external eSATA drive.  Additionally, this system has a "catchall" IO device that uses SATA to communicate with the mother board.  The only problem that I have had was with a Buffalo external drive which doesn't work on its SATA port but that problem was with that hardware; I switched to a generic USB/eSATA housing and a WD disk(and scrapped the Buffalo hardware) and have had no problems with the eSATA since then.

Edit: The white Ubuntu logo which fades brighter and dimmer is normal.  This lasts for a few seconds on this system and then the startup proceeds.

I have read of similar problems to yours so searching the web for your system's symptoms might yield some useful data.

quadproc

---

### Post by kphill on 2010-04-08
Some new information:  I burned new disks using the slowest speed I could.  I still cannot install nor can I run it as a Live CD (the same disk *will* run as Live CD on my laptop which uses Windows XP and is an Intel system).  The BIOS of the computer on which I have been attempting to load Ubuntu has settings for "Auto" detection of harddrives or "None".  I have tried both ways and neither work.  Yes, the BIOS does see the harddrive but it does apparently list it as IDE.  It sounds as if this may be a BIOS issue or hardware incompatibility.  I had trouble with newer versions of Fedora and finally had to set the BIOS to *not* automatically detect the harddrive.  Older versions (before 10) ran fine.

---

