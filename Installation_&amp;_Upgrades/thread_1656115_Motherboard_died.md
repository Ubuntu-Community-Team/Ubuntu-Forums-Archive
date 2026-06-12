---
title: "Motherboard died"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Runaway1956 on 2010-12-30
My old reliable SK8V gave up the ghost, and caught me unprepared.  I have another Opteron on a socket 939 board - it's actually a better, faster CPU on a better, faster board, with better, faster video.  All around, one heckuva upgrade in hardware.

Problem is, I plugged in my SATA drive, and I can only boot to the terminal.  X won't run, and I'm kinda stuck.

How do I tell Ubuntu 10.4 to re-detect all hardware, and to install/uninstall drivers as required?

I know, Ubuntu is supposed to detect new hardware on boot - but for some reason, this isn't happening for me.  Or, if it is happening, Ubuntu and/or X is barfing on what it is finding.

Part of the problem may well be that the old video was NVidia, and the new video card is an ATI . . . . 

Hmmmmm.    I suppose that maybe I should start with aptitude.  I'm sort of used to apt-get, but I don't know the names of all those packages.  Aptitude has a graphic menu - if I can figure out how to navigate it.  Uninstall NVidia and install whatever ATI driver is offers, I guess.

If anyone knows any shortcuts, or sure fire ways of getting this little chore done, please, let me know!

I'm headed to the other room to look at Aptitude . . . .

---

### Post by Frogs Hair on 2010-12-30
I don't this applies in all cases but , a mother board installation disc is normally required prior to installation of the operating system.

---

### Post by Runaway1956 on 2010-12-30
Installation disk?  Only for Windows, I think.  I could be wrong, but all the install disks I've ever seen had Windows driver, for installation after Windows was installed.

Anyway - I think I've solved this.

apt-get purge nvidia*

apt-get install xorg-driver-fglrx

I have very limited bandwidth - I'll know in about half an hour or so if X will run.

---

### Post by coffeecat on 2010-12-30
You're right - you only need the motherboard CD for Windows. In fact you only really need it for Windows versions prior to 7.

Whatever, you also seem to have solved the issue that prevented you from booting up with the new motherboard - proprietary video drivers. Ubuntu - Linux in general - does detect hardware on bootup and you don't have to do anything. The main exception being proprietary video drivers. If you had been using the open source video drivers you wouldn't even have had to do anything about them. The appropriate one would have been loaded when the video hardware was detected.

By the way. What ATI card are you using? For many cards the open source driver is preferable to the fglrx one. The open source ATI driver is more advanced than the open source nouveau driver for nvidia.

---

### Post by Runaway1956 on 2011-01-01
Thanks for your answer, CoffeeCat.

The video card is an ATI early offering on PCI-E.  It's a 1600, with some kind of silly name - Extreme, or something like that.

Anyway - my migration has worked, sort of, but flopped too.  I have the machine running, and I can do almost anything I want to do.  One real bug with the system, is, trying to force Java into high graphics mode.  Something got lost or garbled in the migration, and Java crashes.  (I play Runescape, where you get to configure what sort of graphics Java uses.)

I have a couple smaller glitches, and I may or may not find more as time passes.

I'm cheating, though.  I've put that hard drive aside, and stuck another into the computer.  Right this minute, Ubuntu is being installed, fresh.  

Let's say that I've lived with a few other headaches, as well, for quite some time.  That installation has been distribution-upgraded a couple of times, not to mention that I've butchered it in a number of ways.  (installing OSS instead of Alsa is a beginning of butchery, in and of itself, LOL)

So - in 1/2 hour or so, I'll have a clean install, at which time, I'll browse the other hard drive for stuff I really want to keep.  Dumping all the user config files seems a good idea, if for no other reason than, a lot of the options available 3 versions ago no longer apply.

If/when I find myself needing to migrate a system in the future, I'll try to remember to uninstall any proprietary drivers FIRST!

---

### Post by Frogs Hair on 2011-01-01
Glad it's working , just wanted to add that some Asus installation discs include Linux drivers. My build experience is limited to Asus mother boards.

---

