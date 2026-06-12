---
title: "Install failure on Sony Vaio VGN-FS515H"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by patbuntu on 2007-12-05
Hi there.

Just tried installing gutsy dual booting with XP on a friends laptop (Sony Vaio VGN-FS515H) - didn't go too well.

Heres what I did:

1: Install XP - delete all partitions, format entire drive
2: Install XP Service Pack 2 (probably irrelevant)
3: Checked gutsy live cd for defects
4: Booted into live cd session

So far so good - sound worked, display was set up correctly, everything looked promising.  Didn't try wireless or wired net connections.

5: Start install process from desktop icon
6: Resized the windows partition (which was the full disk) to leave 15GB to install Ubuntu to
7: While the install was ongoing, I started opening a few apps to show my friend what he could expect
8: Accidentally opened Soundjuicer - this may have caused the problem because...
9: When the install was ~ 90%, the hardware probe hung.  The only thing I could do was a hard reset - no virtual terminals, couldn't kill x from the keyboard etc

So I booted back into the live cd session - started the installer again and this time selected the partition that was created in step 6

10: When the installer was ~90% all install dialogs just disappeared.  the live session was still working fine though.

11: Shutdown the laptop from the menu option, removed live cd and rebooted.

This is where it got nasty...

12: No operating system found.  Bugger.

I thought maybe grub didn't install properly or something so:
13: Boot from XP cd - recovery console, ran fixmbr.  I thought this would rewrite the boot record and give me windows back.  restarted the laptop.

14: No operating system found

15: Boot from the XP cd - recovery console, ran fixboot, ran fixmbr

16: No operating system found.

At this point I was out of ideas, so I reinstalled XP wiping all partitions and reformatting the drive.  I left a 15GB partition free this time though, to install ubuntu into without having to resize the windows partition first.

Question is, should I try again?  My friend has now installed all the usual tat that he wants on windows, and restored all his files from the backup he made before we started.  So hes got what he asked me for, a fresh install of xp running how he likes it.  He won't be too happy if we have to start again.  Theres an empty partition sat there waiting for Ubuntu though.

Any suggestions as to what may have gone wrong?  I only singled out opening soundjuicer while installing because i figure it would try and access the cd drive, then the hardware probe would do the same, but thats probably nothing to do with it.

If I do try this again, and the same thing happens, and assuming i've not been dozy enough to delete / format / overwrite the xp partition, what would I do to get XP back?

Cheers

-Pat

---

