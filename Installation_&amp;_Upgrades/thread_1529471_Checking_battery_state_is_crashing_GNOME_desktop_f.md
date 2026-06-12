---
title: "Checking battery state is crashing GNOME desktop frequently"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by JohnE1 on 2010-07-12
Dell Optiplex GX260 (w/onboard Intel graphics)
Original install was Ubuntu 9.04.
Upgraded twice, first to 9.10, and 2 months or so ago to 10.04. Problem never occurred before version 10.04.

BUG HISTORY: Googling on this problem reveals that it has been around since at least Ubuntu 8.10.

I'll be working away and all of a sudden the entire desktop blows off the screen and is replaced with a console stuck in a loop. The last message I always see in the console is "Checking battery state", then the endless looping begins.

The only way out is CTRL+ALT+SYSRQ+K (kills Xserver, I think) followed by CTRL+ALT+SYSRQ+B (reboots system).

NOTE: If I attempt to restart Xserver, Ubuntu goes into an endless console loop with the same "Checking battery state" message. Does that help anyone figure out what's going on?

I have tried to remove any laptop program that manages power and they uninstall ubuntu-desktop. What gives with Ubuntu's GNOME being dependent on laptop utilities? I'm running a desktop and have no need of laptop utilities.

I have gone to the extreme of starting Ubuntu in Recovery Mode, dropping to a root shell with networking, then removing GNOME and Xserver completely and re-installing them both. The problem STILL occurs.

I have used the following commands to accomplish this:

apt-get remove --purge gdm ubuntu-desktop
apt-get remove --purge xserver-xorg
apt-get install xserver-xorg
apt-get install gdm ubuntu-desktop

This problem has made Ubuntu extremely unreliable, as it can crash at any time and DOES... MANY TIMES in a day!!

Please help me resolve this very annoying problem. Thank you!

Thanks in advance for any help, advice, suggestions, etc.

---

### Post by djinnkeeper on 2010-08-07
I am interested to know if you are still suffering from these problems, as many of us are.  There are other threads about this general problem, peppering the boards.. but I think only a few fragmented bug reports have been filed.  I really want to get this addressed by the proper party.. whoever that may be.

---

### Post by JohnE1 on 2010-08-08
YESSSSSS!!!!!  I'm so glad that someone is taking this SERIOUSLY, as it IS a SERIOUS problem.

I have not only completely uninstalled and reinstalled Xserver and GNOME; because of other messages I found I completely purged and reinstalled Evolution (another app I don't use that GNOME is absolutely tied to). My last move was to completely uninstall Apache web server. I've also removed the PCMCIA Utilities and cpufreq utilities. That's another nagging area I can't resolve. At the top of the console that loops when GNOME crashes, is a line about the cpufreq kernel module loading, and on the right-side it always shows  [FAILED].

I hope this add'l information helps.

John

---

### Post by dino99 on 2010-08-08
few steps to follow:

- you might have some usefull errors logged: look at .xsession-errors and "system admin logviewer

- report on launchpad if an error is related to: ubuntu-bug numbererror

- apport might report each crash: check apport installation

- the Dell subforum might be a better place to get specific help

---

### Post by mldj81 on 2010-08-09
(10.04) This happens to me on my Dimension 2400 as well.  I have searched the forums for details regarding a fix, but as Im relatively new to ubuntu, Im not sure how to word my searches.  It always occurs if I try to run Celestia, Tux Cart Racer, and various screensavers.  On occasion it creeps up in firefox, but that seems to have settled down.  Hopefully this is addressed soon, Im looking forward to a Ubuntu-only desktop!

---

### Post by edward_moore on 2010-09-22
Hi all.

This seems like the most appropriate thread to post on as I am also stuck in an endless loop when I attempt to start my machine.

Its an AMD 2.5GHZ Phenom chip, an ASUS Motherboard, ATI 4870X2 Graphics card.

The disks are two 2TB Western Digital Caviar Green's in RAID1 ( mirrored ) mode.

The symptom is that on startup there is a brief message about a file that cannot be located, something to do with /dev/DM1 or similar. I am not at the machine at the moment so I can't get the exact wording.

Anyhow, at this point the screen will very rapidly flicker between the 'I am booting' screen with the word UBUNTU and the four or five little dots, and a some text, albeit on the purple background, the last entry of which is "checking battery state"

This is not a laptop, its an unbranded desktop machine I built myself, it has been updated as of two days ago (I only built it on Friday last week!).

The only thing I have done is upload all my photos onto the RAID array (this is what the machine is for!) and started ripping all my Classical CD's to FLAC.

I have a 10.04 laptop that runs absolutley beautifully, not a single issue, but this desktop box has just died on me :(

Any suggestions for a quick and easy fix ? I can get into a root desktop session through the recovery mode but I really dont want to rebuild the box.

-Ed.

---

