---
title: "Intrepid freezes after update on Firefox use"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by cataboom on 2008-11-20
Dear all,

help!

I upgraded my desktop to 8.10. About 5 days ago I installed the normal updates proposed for Intrepid. After that Firefox (and thunderbird on html emails) started to freeze the system on some web sites such as gmail or google!! The keyboard is not responsive, the only way is to RESET the pc. No CAPS LOCK blinking.
I turned off flash. No change. 

The same happens with Epiphany. A bit less with opera.

I look preceding posts and I noticed that some reports analogous problems. But i found no working solutions. 

What can I do? The only solution is a downgrade to 8.04?
Please help!!

:-)

---

### Post by frankleeee on 2008-11-20
> **cataboom said:**
> Dear all,

help!

I upgraded my desktop to 8.10. About 5 days ago I installed the normal updates proposed for Intrepid. After that Firefox (and thunderbird on html emails) started to freeze the system on some web sites such as gmail or google!! The keyboard is not responsive, the only way is to RESET the pc. No CAPS LOCK blinking.
I turned off flash. No change. 

The same happens with Epiphany. A bit less with opera.

I look preceding posts and I noticed that some reports analogous problems. But i found no working solutions. 

What can I do? The only solution is a downgrade to 8.04?


Please help!!

:-)

It might help to post your computer specs, so the people who know compatibilities might be able to see anything amiss. You also might just do a backup and do a fresh install, if you upgraded via the update manager something might have gone wrong. Also were you running the FF that came with whatever dist you were using before.

---

### Post by cataboom on 2008-11-20
> **frankleeee said:**
> It might help to post your computer specs, so the people who know compatibilities might be able to see anything amiss. 


Here we are:
SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 8.10 (intrepid) release.
	GNOME: 2.24.1 (Ubuntu 2008-10-24)
	Kernel version: 2.6.27-8-generic (#1 SMP Thu Nov 6 17:33:54 UTC 2008)
	GCC: 4.3.2 (i486-linux-gnu)
	Xorg: unknown (24 October 2008  08:00:16AM) (24 October 2008  08:00:16AM)
	Hostname: luisa-desktop
	Uptime: 0 days 0 h 9 min

CPU INFORMATION
	AuthenticAMD, AMD Athlon(tm) XP 1800+
	Number of CPUs: 1
	CPU clock currently at 1533.379 MHz with 256 KB cache
	Numbering: family(6) model(6) stepping(2)
	Bogomips: 3066.75
	Flags: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up

MEMORY INFORMATION
	Total memory: 1009 MB
	Total swap: 2047 MB

STORAGE INFORMATION
	SCSI device -  scsi2
		Vendor:  ATA      
		Model:  Maxtor 6Y060L0   
	SCSI device -  scsi3
		Vendor:  ATA      
		Model:  Maxtor 6Y160P0   
	SCSI device -  scsi3
		Vendor:  HL-DT-ST 
		Model:  DVDRAM GSA-H10N  

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
		Subsystem: Elitegroup Computer Systems Device 0996
	PCI bridge(s)
		VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
	USB controller(s)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
		VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
	ISA bridge
		VIA Technologies, Inc. VT8233A ISA Bridge
		Subsystem: Elitegroup Computer Systems Device 0996
	IDE interface
		VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
		Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE

GRAPHIC CARD
	VGA controller
		ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
		Subsystem: PC Partner Limited Device 7194

SOUND CARD
	Multimedia controller
		VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
		Subsystem: Elitegroup Computer Systems Device 0996

NETWORK
	Network controller
		RaLink RT2561/RT61 802.11g PCI
		Subsystem: RaLink Device 2561


> **frankleeee said:**
> You also might just do a backup and do a fresh install, if you upgraded via the update manager something might have gone wrong. 

Yes. But I would like to try first to fix the problem without reinstall, and all the reconfig work related to it.
I upgraded via the manager. However the strange thing is that the upgrade did not produce any problem! Everything was fine. It was only after an UPDATE few days ago that FF started to freeze the system! So it seems something that was introduced after the release of intrepid...


> **frankleeee said:**
> 
Also were you running the FF that came with whatever dist you were using before.  

uh? i dont get this... The dist in was using before without any problem was ubuntu 8.04. Then I upgraded to 8.10 (after final release) --> no problems. Then few days ago I updated the 8.10 ---> systematic freeze.

thanks! :-)

---

### Post by frankleeee on 2008-11-20
> **cataboom said:**
> Here we are:
SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 8.10 (intrepid) release.
	GNOME: 2.24.1 (Ubuntu 2008-10-24)
	Kernel version: 2.6.27-8-generic (#1 SMP Thu Nov 6 17:33:54 UTC 2008)
	GCC: 4.3.2 (i486-linux-gnu)
	Xorg: unknown (24 October 2008  08:00:16AM) (24 October 2008  08:00:16AM)
	Hostname: luisa-desktop
	Uptime: 0 days 0 h 9 min

CPU INFORMATION
	AuthenticAMD, AMD Athlon(tm) XP 1800+
	Number of CPUs: 1
	CPU clock currently at 1533.379 MHz with 256 KB cache
	Numbering: family(6) model(6) stepping(2)
	Bogomips: 3066.75
	Flags: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up

MEMORY INFORMATION
	Total memory: 1009 MB
	Total swap: 2047 MB

STORAGE INFORMATION
	SCSI device -  scsi2
		Vendor:  ATA      
		Model:  Maxtor 6Y060L0   
	SCSI device -  scsi3
		Vendor:  ATA      
		Model:  Maxtor 6Y160P0   
	SCSI device -  scsi3
		Vendor:  HL-DT-ST 
		Model:  DVDRAM GSA-H10N  

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
		Subsystem: Elitegroup Computer Systems Device 0996
	PCI bridge(s)
		VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
	USB controller(s)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
		VIA Technologies, Inc. USB 2.0 (rev 63) (prog-if 20)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
		VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
	ISA bridge
		VIA Technologies, Inc. VT8233A ISA Bridge
		Subsystem: Elitegroup Computer Systems Device 0996
	IDE interface
		VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
		Subsystem: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE

GRAPHIC CARD
	VGA controller
		ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
		Subsystem: PC Partner Limited Device 7194

SOUND CARD
	Multimedia controller
		VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
		Subsystem: Elitegroup Computer Systems Device 0996

NETWORK
	Network controller
		RaLink RT2561/RT61 802.11g PCI
		Subsystem: RaLink Device 2561


 

Yes. But I would like to try first to fix the problem without reinstall, and all the reconfig work related to it.
I upgraded via the manager. However the strange thing is that the upgrade did not produce any problem! Everything was fine. It was only after an UPDATE few days ago that FF started to freeze the system! So it seems something that was introduced after the release of intrepid...


 

uh? i dont get this... The dist in was using before without any problem was ubuntu 8.04. Then I upgraded to 8.10 (after final release) --> no problems. Then few days ago I updated the 8.10 ---> systematic freeze.

thanks! :-)

I asked if you were running FF3 in Hardy due to a number of people not being happy with it a going back to FF2. You might try installing Ubuntu Tweak 0.4.3 and in the 3rd party area you can get the latest FF3, if this is your only problem.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by cataboom on 2008-11-20
> I asked if you were running FF3 in Hardy due to a number of people not being happy with it a going back to FF2. 

I run FF3.04 and it was fine for me till few days ago.


> You might try installing Ubuntu Tweak 0.4.3 and in the 3rd party area you can get the latest FF3, if this is your only problem.

Thanks nice program! However the installed FF is already the last version (3.04). Furthermore, the same problem is there with thunderbird when opening html mails... :-(

...

---

### Post by frankleeee on 2008-11-20
I don't know if this will help but here is a link to speeding up FF.
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by cataboom on 2008-11-20
no. it does not... :-(

---

### Post by mickcalcara on 2008-11-20
I am having a similar problems with Firefox 3.0.4. and Thunderbird. Yes this issue started after the Firefox update a few days ago. ( I was not having these issues before with Ibex ) My problems are that Firefox and Thunderbird appear to keep attempting to connect to the network but are unable to. This occurs after my computer is idle for a certain amount of time. I have another machine with Ibex on it and it has not had this issue. I am assuming it is because I have not applied the Firefox 3.0.4 updates.

---

### Post by gnwiii on 2008-11-20
I have two systems, both with a fresh install of 8.10rc, upgraded to 8.10.  All was well until the firefox 3.0.4 update.

I'm not seeing freezes, but problems with layout on some pages on one of the two machines.  The gmail message list, in particular, has way too much space between lines (e.g., the display size of the fonts is smaller than the space gmail provides), so instead of 20 or so headers visible on the screen only about 8 are visible without scrolling.  I tried google's suggestions to fix display problems (tools, clear private data).  On the problem machine, trying to adjust fonts in Edit/Preferences/Content crashes Firefox.  

The problem machine has mach64 display hardware.  Firefox on this machine is 
prone to crashing, but on the other machine, which uses the intel driver, is
not having problems.

Opera is working nicely on both machines.

---

### Post by Annoying Moose on 2008-11-20
I am also having similar problems.  I don't use Thunderbird, Gmail, or any web browser other than Firefox, but several web pages cause Ubuntu 8.10 to temporarily freeze when viewed in that browser.  I will try getting the sources for the problematic pages and viewing them in other web browsers (specifically, Epiphany, Galeon, and Lynx).

For the record, I have Ubuntu 8.10 amd64 (fresh disk-format and install), 4 GB memory, and an Intel Core 2 Duo T8100 CPU (2.10 GHz).  So, this is highly unlikely to be a performance issue.

---

### Post by cataboom on 2008-11-21
in the end i decided to downgrade to 8.04, fresh reinstall. everything works fine again, luckily. the moral is, i will never go for an unstable again. thanks everybody. :-)

---

### Post by prostar on 2008-12-11
I just wanted to add a "me too".  I am using 8.10 with "proposed" updates on an Acer TravelMate 8100 (with ATI Radeaon mobility x700) and I get random and complete system lockups.  

Only the mouse cursor will move, no "REISUB" sysrq, no CTL-ALT-BKSPC.  I did discover that I could SSH in and do stuff, but nothing would affect the display.  Even on shutdown(via SSH), the display does not change until the final power down.  Without SSH I have to hard power cycle.

---

### Post by Deadpan110 on 2008-12-15
I had heard this was due to using proprietary drivers with Nvidia graphics cards... (oddness)

but seems here are similar problems... mainly with people using x86_64...

Anyways... try what I posted in this link and see if it works for you...

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/289964/comments/20](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/289964/comments/20)

I just disabled the Ubuntu Firefox Modifications addon and all seems well so far...

Can any one else confirm this helps?

---

### Post by Deadpan110 on 2008-12-15
Spoke too soon... all seemed well for a while and then things started Freezing again... I guess we can rule that out!

---

### Post by prostar on 2008-12-15
Thanks for the possible help, though I am on x86 32bit and ATI graphics.  I am pretty sure it's something with the graphics card though.  Like it gets stuck displaying the wrong layer or something...

---

### Post by EpidemiaN on 2008-12-30
Hi,
Has anybody found a solution for this problem?

I have recently upgraded from 8.04 to 8.10 and. After that, my system has been suffering from sudden, and total, freezes.

This freezes are no so frequent, so it's quite hard for me to tell what causes them. The only thing I can say is that the system might freeze even when the screensaver is running (no interaction is needed =P). And, asi I se Firefox nearly all the time, I don't event know if FF is related to this.

My graphic card is an ATI X700 and I'm using the proprietary drivers downloaded from ATI's website.

Thanks =)

---

### Post by cb34 on 2008-12-30
from what i can tell from my 100 crashes and reboots and re-logins and freezes, and with no life changing to every single version of firefox with complete purging and removal of dirs/files/plugins each time, with and with out this and that plugin.. testing like mad... all the way from firefox 2.0.20(last ver2 firefox) and using every 3.0...3.0.4..5.....3.1b1...b2.. all of em one by one with and without tweaks and plugins... the conclusion is..

every single setup is stable, as long as libflashplayer.so is not there.
all 9 versions.. and ver.10.0.12.36, and the new 15.3 all are not stable and either crash the session and or X, or freeze the whole machine entirely after a while.. that includes trying firefox version from the repo, and from tar.gz's off mozilla's site.. same with flash, from repo and from adobe's site, with .deb's and tar.gz.. i went nuts and said to figure this out i would have to systematically find the cause, so not to get mixed up, i did everything 1 by one for a few dayz, because i would then test and use firefox for a while in between each change to check its stability.

in every situation.. when libflashplayer.so is not installed/present, firefox is completely stable, and will never crash on me.. all versions.

and from the begining i alwayz have samba/winbind purged all the way, and i tried with a fresh install on some crappy laptop i have around.. same thing with the crashing..

also just a note.. i purged pulseaudio all the way and made completely sure firefox and the sytsem are are not still looking for pulseaudio and maybe causing a problem.. so it's got nothing to do with pulseaudio.

it is something with flash/firefox integration together or SOMETHING.. IDONT HAVE A CLUE how these things work, just know that theydont work together.. and the wierd thing is.. even if you use an old version of firefox, and an old version of flash, the crash and instability is there.. so something that they both use in the operating system.. this is the worse problem i think. thought it was xulrunner.. crash is there with xulrunner stuff purged, i have no avahi, or cups installed/running.. no pulseaudio.. no samba/winbind installed, and made sure these things are not just removed, but completely nuked and purged any settings to do with them.

it is flash.. with no flash installed, every version of firefox is stable.. very wierd.. but this is my conclusion. and i truly beleive there is no answer except from adobe and mozilla to look at this.. together. or maybe some super shmooper developers of ubuntu up at the top if they'd take a look at this HUGE problem.

peace.

this problem exists in opera, and epiphany also.. even when they are setup with no linking and all independant of eachother, with flash independantly installed to a different browser, it crashes with flash installed, no flash, no crashing/freezing/bad things..

or maybe its not flash on its own causing the problem????
some connecting module/files.. ??SOMETHING is broken. its very frustrating, and the people that dont suffer from this, i think do, just dont feel it to the full extent that alot of us do.. or dont use flash all that much to notice.

or they have some special 1 little setting somewhere in ubuntu's files that we all need to know about..:p

---

### Post by EpidemiaN on 2008-12-30
Thanks a lot, cb34!

Thats quite a huge work that you have done!

Well, by now I will have the libflashplayer.so disabled and see if everything works fine (no freezes by now =)...)

byee

---

### Post by madmaxnj on 2008-12-31
I'm having the same/similar problem.  I am running Intrepid and everything was working fine until I performed the recommended updates.  Something 'crashed' during the updates, and I didn't write it down, and just rebooted when everything was done but FF3 doesn't work.  It attempts to connect but then dissappears.  Here's what I started on a new post.  There is some problem with xulrunner 1.9 but I can't fix it.

xulrunner 1.9 - Bus error, exit status 135, now no Firefox 

--------------------------------------------------------------------------------

Well it was telling met that there were a bunch of updates that I needed so I clicked to install them all. Something failed during the installation of the updates. It flagged and crash error, but I didn't write down what it was. After that I rebooted and Firefox wouldn't launch. It would start to, I would see it start on the status bar, but then would just go away. I went into Synaptic Package Manager and tried to reload Firefox. Here i get an error:
E: xulrunner-1.9:subprocess post-installation script returned error
exit status 135
E:firefox-3.0:dependency problems - leaving unconfigured (and a bunch more of these 'leaving unconfigured messages).

Digging into the detailed printout it starts to go south with:
Setting up xulrunner-1.9 (1.9.0.5+nobinonly-0ubuntu0.8.10.1)...
bus error
dpkg: error processing xulrunner-1.9 (--configure):
subprocess post-installation script returned exit status 135


So I tried to reload xulrunner and get the same thing.

I've gone through this now in a couple of different orders include deletes and new installs to no avail.

Any ideas? Can I go back a version on xulrunner and Firefox somehow? I don't see older versions in the Synaptic Package Manager.

Help? I configured this box to be a web surfer and now I can't surf the web. Thanks!

---

### Post by cb34 on 2009-01-01
oops...

---

### Post by cb34 on 2009-01-08
i hope this helps:

[http://ubuntuforums.org/showthread.php?t=1034369](http://ubuntuforums.org/showthread.php?t=1034369)

---

### Post by prostar on 2009-03-31
I just wanted to update that I have fixed my crashing issue. It was, as I suspected, a graphics issue. I went off the restricted drivers, then back on, so as to download a newer version. All is working well for a week now.

Good luck to anyone else with this issue, it nearly broke my 4 year streak of not using windows on a regular basis...

Regards,
Tony

---

