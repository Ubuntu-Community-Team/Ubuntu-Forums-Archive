---
title: "Dual Boot XP &amp; Ubuntu"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by bcaulkins on 2007-05-21
I've got a little problem.  I want to dual boot Ubuntu and XP.  I have installed each OS on a seperate 36 gb SATA drive.  Each will boot independently of each other but I have to switch which SATA controller it is on.  For example, the SATA controllers being used are, let's say, 5 & 6.  If I want XP to boot I put the XP drive on SATA controller 5 and Linux drive on 6 and XP boots.  If I want Linux I shutdown, switch the cables and Linux boots.

This is how I installed my OSes.
First I hooked up one SATA drive, installed Windows and got it working.
Second I unhooked the XP drive, hooked the second SATA drive up, loaded the Ubuntu 7.04 live CD and installed Ubuntu.
Now both drives are hooked up but only one will boot at a time.

I know about the GRUB boot loader but I'm not sure how to enable it so I can choose which OS I want at boot.  Ubuntu didn't say anything about it during installation.

Also, in XP I can't see the Linux drive.  I haven't checked in Linux whether or not I could see the XP drive.  I was up late last night, had to go to work.  I'm currently at work now and have been searching the forums.  I came across an article detailing a SATA and IDE configuration but not two SATA drives.  Any help would be appreciated.

Thanks.

---

### Post by stefaan.dutry on 2007-05-21
If it's an option for you; i would suggest installing ubuntu again.

[LIST=1]
[*]back up the files you need on the ubuntu drive
[*]format the ubuntu installed HD
[*]install ubuntu again; this time leaving the windows HD in as main disk (that way the grub will be installed there) and select the formatted disk as location to install.(you should see more than 1 disk in there, if not don't install, ask for help again first)
[*]and there you go, you have a dual boot system
[*]place all the backed up files back on the ubuntu drive.
[/LIST]

If you don't do it with the windows drive hooked in as main i think you will get an error while starting it up from the ubuntu drive; even if it recognises it. (I don't know for sure).

Hope this was of any help.

---

### Post by bcaulkins on 2007-05-21
I'm glad you said that.  I was kind of thinking about just re-installing Ubuntu.  I thought it wasn't working because it didn't see the other OS present, so Ubuntu thought it didn't need to configure GRUB.  There's nothing as of yet that could be lost on the Ubuntu drive.  Thanks!

---

### Post by stefaan.dutry on 2007-05-21
Can you tell me if you were succesful?

I'd like to know ( even if it was just to feel good about helping someone ):)

---

