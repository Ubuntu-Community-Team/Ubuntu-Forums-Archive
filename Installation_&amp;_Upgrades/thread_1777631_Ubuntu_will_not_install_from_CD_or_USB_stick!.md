---
title: "Ubuntu will not install from CD or USB stick?!"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by RapidDissent on 2011-06-08
Hey guys; loosing hair over this one...

Just built a new computer (MSi H61M-P23, i3 2100, 4GB DDR3 dual channel @1333, GeForce 210, 2x WD Caviar Black [1TB, 2TB], 500W Coolermaster PSU, Samsung SH-S223F CD/DVD). I've got plans to turn this into a server (file, vpn, etc), hence the modest specs.

Every time I try to start up on an Ubuntu CD, after the loading screen (with the 5 white/red dots), it drops to an ash shell talking about "**Unable to find a medium containing a live file system**", and when I type 'exit' twice (as I've noted from similar threads), it starts talking about a kernel panic, and goes catatonic on me. For added insult to injury, I have to restart my system a couple of times before the BIOS will even SEE the CD/DVD drive again. This is most worrysome...

Try to load Windows 7 once the drive comes back, and seems to work fine. I get in far enough to initialize the system drive, but want GParted to handle the formatting, so I go back to linux to see if that helped anything. 15 minutes later, I'm still waiting for it to get past the loading screen with the 5 white/red dots, and the drive indicator stopped flashing... ugh.

Unplugged the secondary drive to see if that makes a difference; it didn't.

OK, forget that, time to make a thumb drive do it for me!!!! Deleted old .iso a while back, so redownloaded the ISO. Make thumb drive per Ubuntu download page instructions, and start it up. When I selet EITHER 'install ubuntu' or 'start ubuntu', the loading screen comes up (same screen as CD), hangs out there for a (rather long) while, and dumps ENORMOUS amounts of text, not sure what any of it meant (didn't look too closely at this point, but the last entry was something like (17000)yadda yadda yadda; don't know what it was going for, but it didn't seem to work.

Verified .iso MD5 checksum; it's good. Burn new CD with verified .iso. Now it's unloading huge amounts of text on load, too!! Last entry I can see (text runs off screen in all directions) is '(14100) /dev/loop0 (/cdrom/...(runoff)...system.squashfs) on //filesystem.squashfs.

I'm losing my mind on this one... help!?:confused:

---

### Post by RapidDissent on 2011-06-08
UPDATE: Installed Windows 7 out of desperation; partitioned half the drive for windows, and installed, leaving the other half unclaimed. After I got that all set up, I decided to try Ubuntu to see if anything had changed... 

I got past the loading screen somehow, and I'm at GParted screen now! :confused:

The only thing I can think of is the first CD was in fact corrupted, and somehow, having the USB drive plugged in during startup screwed with the verified CD (removed the USB drive before this try).

I'm going to mark the thread 'solved', but I would still like to know what happened, if anyone's got any ideas?

---

