---
title: "Asus M4A88TD-M EVO/USB3 installation failing"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by counterpoint on 2011-01-08
I'm struggling to know where to look for a problem.  A newly upgraded machine uses the following main parts:

[LIST]
[*]Asus M4A88TD-M EVO/USB3 motherboard
[*]AMD Phenom II X2 560 processor
[*]4GB Crucial high speed memory
[*]Onyx OCZ 32 GB SSD
[/LIST]

Every attempt at installing Ubuntu 10.10 fails with a message about copying from the CD to the disk.  The CD has been burned again, and can be run as a live CD on a different machine.

The motherboard has had the BIOS upgraded to the latest version.

Swapping the Onyx OCZ SSD for a Seagate Barracuda 320 GB (taken from a working system) fails in the same way, although it takes a little longer.

A basic install of Windows XP worked, apparently without problem.

Running the Ubuntu 10.10 live CD does not work properly - attempting to start Firefox causes a message to appear in the bottom bar saying it is starting, but it disappears again without Firefox actually starting.  (Works OK with the same CD on an older machine).

Where should I be looking for a problem?  Is there any way to pin it down?

---

### Post by cascade9 on 2011-01-08
Are you using AHCI or 'ide mode'?

---

### Post by counterpoint on 2011-01-08
I was using the default of IDE mode.  Changing to AHCI, the install seems to run for a little longer, but still halts with the same message about a disk copying failure.

---

### Post by cascade9 on 2011-01-08
Odd. 

All I can suggest is try intalling in the working computer you pulled the HDD from then transfer the HDD to your new computer, or try a different distro.

---

### Post by counterpoint on 2011-01-08
Hmm, must remind myself never to ignore the obvious :)

Installing from a USB memory stick worked perfectly!

It was a rebuild of an existing machine, retaining the case, PSU and DVD/CD drive.  As is the way with a machine that's been in use for a while, there was plenty of dust and fluff - I guess some of it must have got into the DVD/CD drive and was causing the failures.

---

### Post by cascade9 on 2011-01-08
Doh! I should have thought of that. :( 

Nice to see its fixed though. 

I'd doubt that its fluff in your DVD drive, since XP worked. Its more likely to be the JMicron JMV368 PATA controller.

---

### Post by counterpoint on 2011-01-08
Why would that behave differently between Windows XP and Ubuntu?

---

### Post by cascade9 on 2011-01-09
There was some nasty issues with the JMV368 controller a few years ago, and some motherboard manufacturers put in extra 'RAID' chips in between the jmicron controllers and the drives, which IIRC makes the controller stuff up with linux.

---

### Post by counterpoint on 2011-01-09
Thanks for the info.

So far as I can see, the problem seemed to be with the input side of the installation.  The DVD/CD drive is an older IDE type, using the IDE connector on the motherboard.  Would an issue with the JMV368 affect that?

---

### Post by cascade9 on 2011-01-09
Sicne the JMV368 is the PATA controller, yeah, an issue there could (would?) stop your PATA drives working.

---

### Post by drim on 2011-03-08
hi!
i am about to buy a pc with a configuration like yours..
i'd like to kwon something about the integrated graphic....does it work properly with ubuntu? otb or need something?

my config would be:

Hard Disk Western Digital Caviar Green 1TB 3.5" Intellipower 64MB SATA2 WD10EARS
SCYTHE Mugen 2 Rev.B AM3/AM2+/754/939/478/775/1366/1156
ASUS M4A88TD-M EVO/USB3 AM3/DDRIII AMD880G
Middle Case Cooler Master Silent Pro M500 500W 80plus V2.91 Sli cerificated
CPU AMD Phenom II X2 560 3.3GHz Socket AM3 80W Callisto Black Edition Boxed HDZ560WFGMBOX
Case Midi Cooler Master Centurion 5 II ATX Nero
Internal DVD Burner LG GH22NS50 22x DVD/CD Sata RETAIL black
RAM DDR3 Corsair Dominator CMP4GX3M2A1600C9 1600MHz 4GB(2x2GB) CL9

thanks a lot!

drim

---

### Post by counterpoint on 2011-03-08
Seems good to me!  I have a problem that the display is messed up during login, but I've not made any attempt to find a solution for that.  Just key in the password and then everything comes right again.  Running on a 1600 x 1200 NEC monitor.  Mine is a SSD instead of hard disk.  Otherwise pretty similar.  It's very fast for software development - I don't do any specialist graphical stuff, but for general use the on board graphics is fine.

---

### Post by drim on 2011-03-08
thanks for the fast reply!

neither i need to do something professional with my graphic...but i mean are you able to watch a 1080p movie? ant what about the audio is the dolby working?

thanks again!!

---

### Post by counterpoint on 2011-03-09
Sorry, I don't know.  I use my system for software development and never watch movies on it.  Sound makes noises, but I don't know to what standard.

---

### Post by drim on 2011-03-09
ok, thank you btw.

---

### Post by djshortsleeve on 2011-03-09
I have almost the same mobo, not the evo.  For some reason, I cannot install from USB.  I can boot Live, but when I attempt to install, it hangs at step 3 of 7 (10.04), and hung for 10.10 as well.  Im thinking I need to format my new hard disk somehow...

---

### Post by lem79 on 2011-06-16
I'm going to share a very peculiar situation with this motherboard and Ubuntu 10.04 LTS, and Ubuntu 10.10 (AMD64 desktop, and AMD64 alternate, respectively).

The system comprised of:

Asus M4A88TD-M USB3
Phenom II X2 555 3.2GHz
4Gb (2x2Gb) G.Skill RipJaws DDR3-1600 8-8-8-24 1.6V
IDE LiteOn DVDRW
IDE LiteOn CDRW

The RAM *had* to be run at 8-8-8-24 (only tried 1333MHz, not 1600MHz), anything else would result in memtest errors after about 15 minutes of testing. The SPD for the RAM tries to run it by default at 1333 9-9-9-24 or so, and even that failed. 8-8-8-24 @ 1333MHz, perfect. That's an aside anyway, back to Ubuntu.

Both Ubuntu 10.04 LTS and Ubuntu 10.10 would hang during boot up, always during probing the disk controllers. Ubuntu 8.10 however worked fine.

We tried unplugging the IDE LiteOn CDRW drive, and voila.. 10.04 LTS booted up without a hitch, no hangs. I'd wager that 10.10 would also work perfectly.

Very odd situation. So if there's anyone out there with Ubuntu hanging on bootup with this motherboard, try unplugging your IDE optical drive(s) :)  No idea what the issue might be .. master/slave switches were set correctly etc (moved from an old system).

Hope that helps someone :)

---

