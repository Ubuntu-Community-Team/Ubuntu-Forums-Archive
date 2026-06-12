---
title: "Alpha 2 installation - my experience"
date: 2008-12-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-12-20
Just installed Jaunty Alpha2 64 bit on my PC. The installation so far seems to be fine. The boot time seems to be very impressive (I hope to include comparisons between Jaunty and Intrepid later).
First question - why is the kernel only 2.6.27-7 and not 2.6.28-2 ?
Just downloading some 202 updates and then need to install restricted drivers for wireless and Nvidia display adapter. More soon...

---

### Post by Moop on 2008-12-20
I tried installing 64 bit from the alt cd but it would just hang at the detecting network screen. Installed from the live cd and all went well.

---

### Post by Gina on 2008-12-20
Latest updates should give you 2.6.28-3 - that's what I've got.  Still not had time to try Alpha 2 - maybe later this evening...

---

### Post by Kevbert on 2008-12-20
Just adding the updates that are reported gives me 2.6.27-9 (I had 2.6.28-2 with Alpha1 prior to replacing it with Alpha2 but I had a Nvidia display problem reported elsewhere). The updates had a few problems (see my attached edited /var/log/apt/temp.log which I've just included any errors).
According to Update Manager my System is up-to-date (but it can't be). I'll have to see if anything is shown with terminal.

Just found out that I need to edit my sources.list again (as per Alpha1) as it has the old intrepid sources only. Having done this I now need to install 566 updates...

---

### Post by Gina on 2008-12-20
Have you clicked on the "Check" button?  Alternatively go to Synaptic - Reload, Mark all Upgrades and provided it doesn't want to remove anything without installing a suitable replacement, Apply.

---

### Post by Kevbert on 2008-12-20
I've updated/upgraded via terminal (but no dist-upgrade yet).  Kernel is now 2.6.27-9 after installing 566 (-1) updates. There was a problem with libgnome2-0 -'package libgnome2-0 2.24.1-1ubuntu1 failed to install/upgrade: trying to overwrite `/usr/share/man/man1/gnome-open.1.gz', which is also in package libgnome2-common' which is Bug report #304417. I rebooted into Jaunty and got no network connection, no background, no icons a power manager error (briefly displayed on the screen). I then tried to reboot both via the System menu and via the shutdown icon (that was displaying) and nothing occurred. I've attached a screenshot. I still haven't installed any restricted drivers and Jaunty in this state is unuseable for me (could be due to libgnome bug ???)
I may try a new install much later...

---

### Post by Kevbert on 2008-12-20
Just tried a second clean install of Alpha2. Installed CD then edited sources.list for Jaunty and rebooted (as update icon displayed in top righthand side of top panel). Then installed 595 updates via terminal. Next did a distribution update again via terminal. Now rebooted (only 2.6.27-7 kernel shown in grub menu). Got the same display as attached in previous post. This time got a stop sign that appeared in top right of top panel, clicked on it and a load of updates were installed (????) Unable to reboot and also got a libcanberra error which I couldn't report as web address wrong. Waited a couple of minutes and then did a hard reset. PC booted into 2.6.28-3 kernel. Able to use restricted driver for Broadcom wireless but no restricted driver for Nvidia (so I have an offset display).

---

### Post by jerrylamos on 2008-12-20
Been trying to install CD Live for 3 consecutive day's downloads.  No joy.  Edit partition hangs Ubiquity.  So.....

Real crowbar sledgehammer technique worked this time on three of my four test computers.  I dual boot so I can afford to blow away an install and still be able to boot something.

With jaunty 2.6.27-7, 
booted in recovery mode, 
did root shell prompt dhclient
did fix broken packages
Whee that took a while !  Real diarrhea all over the screen.

Now they boot 2.6.28-3.  Sound even works on all three, did not on previous jaunty.  Shutdown takes 13 seconds on the two different pc's I timed.

Cheers, Jerry

---

### Post by Gina on 2008-12-21
Just tried to boot from USB memork stick on my AMD64 - no joy.  Now need to find out if the USB stick setup didn't work or if it's Alpha 2.

---

### Post by Gina on 2008-12-22
I got the USB memory stick to load Alpha 2 but the Install failed. Have now just burnt a DVD+RW with Jaunty Alpha 2 Alternate AMD64 and tried to install.  Firstly ran the CD check which it passed and all was well until it finished the check and said "Continue".  Then nothing worked - it was if I'd totally lost the keyboard - I had to press and hold the off button on the box to get out.  I then restarted and after the Language setting, chose Install.  Everything proceeded until the keyboard setting then no response again.

I will try the 32 bit version both on my AMD64 and laptop but I cannot install Alpha 2 64 bit.  As I said above, I also tried the Desktop AMD64 version from USB stick - that loaded but went wrong with the Install just like the Alternate version.

I can still continue to test Jaunty as I have working versions (using one now) from Alpha 1 and daily updates.

---

