---
title: "Lubuntu stuck on installation routine..."
date: 2022-06-17
forum: Installation &amp; Upgrades
---

### Post by David2009 on 2022-06-17
I have chosen to install Lubuntu 22.04.  The ISO downloaded easily.  The Checksum was correct.  I put the disk in the DVD drive, and at the boot the installation routine began.  A beautiful screen with a blue background and a bird.  Then that went away, and at a terminal screen I have received a few lines, and now it is stuck with the drive whirring and nothing else happening.  Here is what I have:

[    0.574655] ACPI BIOS Error (bug): \_SB.PCIO._OSC: Excess arguments - ASL declared 5, ACPI requires 4 (20210730/nsarguments-162)
[    0.582972] pci 0000:02:00.0: unsupported PM cap regs version (7)
            Starting Set console scheme...
[  OK   ] Finished Terminate Plymouth Boot Screen
[FAILED] Failed to start Disk Manager.
[FAILED] Failed to start Snap Daemon.
[FAILED] Failed to start Snap Daemon.

That's all that has happened, and as I've typed on another computer the computer continues to try.  

Ideas?  I'm going to use a hard shut down with the power button.

EDIT: When I hit the power button I received a notice to wait until something happened...Snap Seed?...the message went by quickly, and now I'm back at the initial blue screen with the bird and the DVD opened, with the message remove installation medium, then press ENTER.  The computer shut down.

Thank you.

David

---

### Post by guiverc on 2022-06-17
I'd recommend using a USB THUMB_DRIVE instead of DVD.

Ubuntu has for some time, assumed THUMB_DRIVE is used for installation media; particularly on releases of 20.10 (ie. *2020-October release*) or later.  

*Note: it was assumed before 20.10 too, but it became ~real from 20.10 onwards*

The 22.04 release will read the whole media to perform a self-validation of the media to ensure there are no unexpected errors.. this isn't done starting from the media sector 0 and then reading each sector until the end, but is done file by file, meaning it's extremely slow on media such as DVDs.

There is a [low priority *bug report*]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1971905") that may disable some of the scans where optical/slow media is detected, but the effects of this aren't present in current 22.04 released ISOs.

I'll refer you to this thread

[https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246](https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246)

and tell if you if repeatedly boot the media; you'll be able to perform an install, but you'll need to allow a AWFUL LOT OF TIME as what can take mere minutes on thumb-drive can take hours using optical media.  I'd suggest not using *snaps* whilst running from DVD, yes they do on occasion work, but the media is so slow you get repeated timeouts that cause snap errors that aren't that helpful (*in realizing it's media timeout* *related*).

---

### Post by David2009 on 2022-06-17
Thank you for the quick reply!  I restarted the install, and went to the UPS store.  It took a while (rush hour), and when I returned there was a nice looking desktop waiting for me.  So, I have begun the installation (before was only loading the DVD). 
- I cannot figure out how to have it recognize my WiFi.  The computer next to it sees the WiFi.
- I got a message on the Finish tab: Installation Failed.  
-- The installer failed to create a partition table on ubuntu-vg.
-- Create a new partition table (type:msdos) on '/dev/ubuntu-vg' 
-- Job: Create new partition table on device 'dev/ubuntu-vg'
 
My only option is to close.
 
Hummm...

Ideas?

---

### Post by guiverc on 2022-06-18
Providing details as to what type of install you used would help.  Are you using "*Erase disk and install*"? encryption?, "*Manual Partitioning*"? or other option(s) etc.

I'm somewhat reminded of [https://discourse.lubuntu.me/t/calamares-rare-failure-to-create-partition-mkfs-errors/2774](https://discourse.lubuntu.me/t/calamares-rare-failure-to-create-partition-mkfs-errors/2774) but that tends not to occur with simple partition installs. Using DVD/optical media though has been shown to throw random *timeout* issues that software can misinterpret in error messages (eg. *snaps*, maybe `calamares` (installer used by Lubuntu) too).

Lubuntu is just a different desktop (*including toolkit/libraries used by desktop, plus desktop apps*) on the same Ubuntu base as main Ubuntu and other *flavors*, thus wifi is no different.  I'd thus recommend using [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and especially the [*Device Recognition and Operation *]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices")section link for clues about getting Wifi working on your device. If however your issue is the operation of Lubuntu's *nm-tray* I'll suggest the Lubuntu manual - [https://manual.lubuntu.me/stable/3/3.1/3.1.4/nm-tray.html](https://manual.lubuntu.me/stable/3/3.1/3.1.4/nm-tray.html)

---

