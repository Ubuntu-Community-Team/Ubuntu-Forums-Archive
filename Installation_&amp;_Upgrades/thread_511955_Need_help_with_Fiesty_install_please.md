---
title: "Need help with Fiesty install please"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by partsmutt on 2007-07-28
There are tons of install threads here, and I'm sorry to have to start another one.  I can't find anything that addresses my problems.

Get this out of the way first:
3.xGHz intel.  Foxconn motherboard
MB supports SATA and IDE, I'm using IDE
built in video and audio
1G RAM

This machine was running XP with an old 30G HDD.  I do not want dual boot of anytype.  Microsoft isn't allowed in my home normally (we're a Mac house - but want to try Linux).  The old drive is gone, replaced with a newer 120G IDE drive.

Trying to install Edubuntu (this is a machine for my young son, hence the edubuntu).  I checked the cd, all is good.

The workstation install gets through the base system install part but hangs at 85% in the software installation section.
The hang is my problem.  Don't know what to do.

I've guessed that 'maybe' there's a problem with the drive?  Bad sectors or something?  So after lots of bad luck I made a successful install with the command line only version.  That is up and running right now.  It's currently running (while I type this in fact) e2fsck.  It gave me the warnings about destroying the filesystem, etc.  But I had nothing to lose and thought it might tell me something.  Hasn't told me anything so far.  I figure I can reinstall another command line version when it's done.

Any ideas?  I'm completely blocked out here and don't know if it's a hdd thing or a linux thing.

One other oddity.  It sees my drive as sda.  Isn't that the scsi designation?  It's not a scsi drive, it's ide (pata, whatever).  Shouldn't the device be hda1 or hde1 or something like that?

Thanks
Dave (a mac user, "lightly" familiar with unix from work, no experience with Linux)

---

### Post by Pumalite on 2007-07-28
I don't quite understand you. You have a system running. What is the problem?

---

### Post by partsmutt on 2007-07-28
I have a command line only system running.  It's for my 9 year old.  I'd like to have gnome running and applications that he can use.  The install of that system won't work.

---

### Post by Pumalite on 2007-07-28
Try: ' sudo apt-get install gnome-desktop'

---

### Post by partsmutt on 2007-07-29
I appreciate the reply, but that doesn't help my situation.  Then I'm still stuck with a system that isn't the full install I wanted.

However, I did find a workaround for this and I'm posting it here in case anyone else finds it useful.  I was using the Server install cd and chose the option to install a workstation.  After several tries I started from scratch and downloaded the Desktop CD, which from what I gather used to be called the "live cd."

That booted fine as the OS comes up and runs off the cd.  There is an icon of the desktop for installing.  I double clicked that and everything worked perfectly.

Dave

---

