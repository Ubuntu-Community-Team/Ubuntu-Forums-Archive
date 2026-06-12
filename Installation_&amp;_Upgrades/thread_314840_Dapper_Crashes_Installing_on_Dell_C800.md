---
title: "Dapper Crashes Installing on Dell C800"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by AEngineer on 2006-12-08
I just posted the following to [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug)
 as requested when Dapper crashed for the fourth time while installing.  That site gives no information about whether they'll help individuals so I'm posting the same here in hopes that someone can help me get going reliably.  At this point I have to conclude that something is badly wrong, but I have no idea where.  MSW sure looks good compared to my Ubuntu experience.

*************
[https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug)

I've now tried four times to get Ubuntu running on a Dell C800 laptop
- I've checked the CD using the self-check on the CD - all OK
- I have to install in "safe graphics" mode because in the default the screen is split in three pieces 
- It runs fine in the CD-only mode so far as I can tell
- I ran Steve Gibson's SpinRite on the HD and found no problems (2+ days for an 80GB HD)
- I install using the "erase HD" mode which I assume ought to blow away any prior problems
- Several times it has installed, but then when I attempt to update the software, or in one case attempted to upgrade to 6.10 via
	gksu “update-manager -c”    the system crashes at different point
- FYI I've tried also to boot from a 6.10 CD - I cannot do so because I have the split screen problem and cannot boot in safe graphics mode.

I'd surely appreciate a suggestion of what I can do beyond what I've done.  More specifically
-	Are there hardware checks I can run from the live CD - nothing 

- This last time it crashed with the following message that I had to type in from the screen. Obviously I cannot send the files.

Traceback (most recent call last):
File "/usr/bin/ubiquity", line 130, in?
	install(sys.argv[1])
File "/usr/bin/ubiquity", line 55, in install
	ret = wizard.run()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
	self.progress_loop()
File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538 in progress_loop
	raise RuntimeError, ("install failed with exit code %s; see "
RuntimeError: Install failed with exit code -11; see/var/log/installer/syslog and /var/log/syslog

---

### Post by wpshooter on 2006-12-08
What are the hardware specs. of your computer ?

Are you installing using the DESKTOP CD or the ALTERNATE CD ?

Do I understand correctly that you are going to be running ONLY Ubuntu on this computer ?

---

### Post by AEngineer on 2006-12-08
Running Ubuntu Only
Desktop CD (I'm pretty sure)

Specs:
	Processor(s)
	Model	Mobile Intel(R) Pentium(R) III
	Speed	997MHz
	Performance Rating	PR1196 (estimated)
	L2 On-board Cache	256kB ECC synchronous ATC

	Mainboard and BIOS
	Bus(es)	X-Bus AGP PCI PCMCIA CardBus USB FireWire/1394 SMBus/i2c
	MP Support	No
	System BIOS	Dell Computer Corporation A21
	Mainboard	Dell Computer Corporation Latitude C800
	System Chipset	Intel Corporation 82815/EM/EP/P 815/EM/EP/P (Solano) Host to I/O Hub Bridge
	Front Side Bus Speed	1x 100MHz (100MHz data rate)
	Installed Memory	256MB SDRAM
	Memory Bus Speed	1x 100MHz (100MHz data rate)

80GB HD

---

### Post by wpshooter on 2006-12-08
If you are going to be running Ubuntu ONLY and have no material on the hard drive that you need to keep then do this:

Get the KILLDISK program and WIPE your hard drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then assuming you have a good integrity checked CD, boot from the live CD and run the memtest to make sure your memory is O.K.

If it is, then boot back to the CD again and this time attempt to go to load the CD and install to your hard drive once you get to the desktop.

Make sure when you are going thru the parameters to install to your hard drive that you let your CD spin down to a stop between answering each of the parameters.  On the parameter regarding the keyboard language, click on the test typing box at the bottom (you don't have to type anything in it just click on it) and then click back to the language choice and then click on next.  Be patient !!!

If after attempting this several times and it still does not install without error, then you may want to consider downloading and installing from the ALTERNATE (text mode) CD.

Good luck.

---

### Post by AEngineer on 2006-12-09
I followed your advice.  Kill disk identified a bad hard disk, something I'd begun to suspect because of the extended times some actions took although nothing identified it, including SpinRite.

I put an older, smaller one in and all seems to be going well.

Many thanks

---

