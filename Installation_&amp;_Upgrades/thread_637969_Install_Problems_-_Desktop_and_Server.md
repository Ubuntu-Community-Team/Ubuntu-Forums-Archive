---
title: "Install Problems - Desktop and Server"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by OldManRiver on 2007-12-11
Latest update (12/20/07)

All,

Been working on my installs for over 3 weeks now and still having trouble finishing both Ubuntu desktop and server installs.  I went throught the myriads of HELP and HOWTO guides but still facing a lot of the problems.  The two most problematic are the sound and video installs, because sound installs with the Realteck ALC655/AC96(SIS) are documented everywhere as problematic and my AMW MR19C-AB LCD monitor has huge sync issues.

I originally posted to other threads, but thought the issues I was facing might benefit someone else as the start of a HOWTO, so thought a new thread was in order.

Since I have been working of these some of the issues are closed so I am giving a status and priority to each and highlighting that.

Here I outline my eight(8) install issues, with the four of the eight currently resolved (12/13/07).

**Closed (12/13/07)**
1. Sound (DT).  Following the instructions from the following links:

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=91501](http://ubuntuforums.org/showthread.php?t=91501)

Downloaded the "alsa-info.sh" bash script from the first.  Ran is and results posted at:
> 
   [http://pastebin.ca/804854](http://pastebin.ca/804854)

Then researching found my onboard sound chipset was Realtek ALC655 which uses the AC97 driver set (that led me to second link).  Once I ran the install from the second link, sound still did not run, so re-ran "alsa-info.sh".  Results posted at:
> 
   [http://pastebin.ca/814829](http://pastebin.ca/814829)

You can see the difference, but not being a sound techy I have no idea what still needs tweaking.  Just do not have enough working knowledge of this to know what I do next.

When I run the set of cmds in the debugging guide I get:
```

	a.	cat /proc/asound/cards		No such file or directory
	b.	/etc/modprobe.d/alsa-base	Permission denied
		Then with chmod 775 /etc/modprobe.d/alsa-base
		I got:
		install: target `snd-card-0' is not a directory
		install: target `snd-card-1' is not a directory
		install: target `snd-card-2' is not a directory
		install: target `snd-card-3' is not a directory
		install: target `snd-card-4' is not a directory
		install: target `snd-card-5' is not a directory
		install: target `snd-card-6' is not a directory
		install: target `snd-card-7' is not a directory
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		install: unrecognized option `--ignore-install'
		Try `install --help' for more information.
		/etc/modprobe.d/alsa-base: line 29: options: command not found
		/etc/modprobe.d/alsa-base: line 30: options: command not found
		/etc/modprobe.d/alsa-base: line 31: options: command not found
		/etc/modprobe.d/alsa-base: line 32: options: command not found
		/etc/modprobe.d/alsa-base: line 33: options: command not found
		/etc/modprobe.d/alsa-base: line 34: options: command not found
		/etc/modprobe.d/alsa-base: line 35: options: command not found
		/etc/modprobe.d/alsa-base: line 36: options: command not found
		/etc/modprobe.d/alsa-base: line 37: options: command not found
		/etc/modprobe.d/alsa-base: line 39: options: command not found
	c.	Make sure that all users needing access to the Sound Device can
		"Use audio devices" in the "User Privileges" tab of users-admin
		(System->Administration->Users and Groups).
		Having noting here indicating how to set this.
	d.	lsmod | grep snd	Produces nothing
	e.	lspci -vvnn		Results follow:
		(Non-sound related edited out)
		00:02.7 Multimedia audio controller [0401]: Silicon Integrated
		Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
		Subsystem: Elitegroup Computer Systems Unknown device [1019:1891]
		Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- 
		ParErr- Stepping- SERR- FastB2B-
		Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium 
		>TAbort- <TAbort- <MAbort- >SERR- <PERR-
		Latency: 32 (13000ns min, 2750ns max)
		Interrupt: pin C routed to IRQ 5
		Region 0: I/O ports at e000 [size=256]
		Region 1: I/O ports at e100 [size=128]
		Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,
		D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	f.	Re-run of "./alsa-info.sh"		Results follow:
		cat: /proc/asound/version: No such file or directory
		grep: /proc/asound/cards: No such file or directory
		cat: /proc/asound/cards: No such file or directory
		cat: /proc/asound/modules: No such file or directory
		ls: /dev/snd/*: No such file or directory
		aplay: device_list:204: no soundcards found...
		arecord: device_list:204: no soundcards found...
		Uploading information to www.pastebin.ca ...  Done!
		Your ALSA information is located at http://pastebin.ca/808718
	g.	Re-run of "aplay --list-devices"	Results follow:
		aplay: device_list:204: no soundcards found...
	h.	Re-run of "lspnp -v"			Results follow:
		The program 'lspnp' can be found in the following packages:
		 * pnpbios-tools
		 * pnputils
		Try: apt-get install <selected package>
		bash: lspnp: command not found
	i.	Run install of "apt-get install pnpbios-tools"
	j.	Run install of "apt-get install pnputils"
	k.	Re-run of "lspnp -v"		Results follow:
		00:00 PNP0c01 System board
		    state = active
		        mem 0xc8000-0xcbfff
		        mem 0xf0000-0xf7fff
		        mem 0xf8000-0xfbfff
		        mem 0xfc000-0xfffff

		00:01 PNP0a03 PCI bus
		    state = active
		        io 0xcf8-0xcff
		        io 0x480-0x48f
		        io 0x1000-0x10df
		        io 0x10e0-0x10ff

		00:02 PNP0c02 Motherboard resources
		    state = active
		        io 0x10-0x1f
		        io 0x22-0x3f
		        io 0x44-0x5f
		        io 0x62-0x63
		        io 0x65-0x6f
		        io 0x74-0x7f
		        io 0x91-0x93
		        io 0xa2-0xbf

		00:03 PNP0200 AT DMA controller
		    state = active
		        io 0x0-0xf
		        io 0x80-0x90
		        io 0x94-0x9f
		        io 0xc0-0xdf
		        dma 4

		00:04 PNP0b00 AT real-time clock
		    state = active
		        io 0x70-0x73
		        irq 8
		
		00:05 PNP0800 AT speaker
		    state = active
		        io 0x61-0x61
		
		00:06 PNP0c04 Math coprocessor
		    state = active
		        io 0xf0-0xff
		        irq 13

		00:07 PNP0700 PC standard floppy disk controller
		    state = active
		        io 0x3f0-0x3f5
		        io 0x3f7-0x3f7
		        irq 6
		        dma 2

		00:08 PNP0501 16550A-compatible serial port
		    state = active
		        io 0x3f8-0x3ff
		        irq 4

		00:09 PNP0401 ECP printer port
		    state = active
		        io 0x378-0x37f
		        io 0x778-0x77b
		        irq 7
		        dma 3

		00:0a PNP0f13 PS/2 port for PS/2-style mice
		    state = active
		        irq 12

		00:0b PNP0303 IBM enhanced keyboard (101/102-key, PS/2 mouse 				support)
		    state = active
		        io 0x60-0x60
		        io 0x64-0x64
		        irq 1
	l.	"tail -2 /proc/asound/oss/sndstat"	Results follow:
		tail: cannot open `/proc/asound/oss/sndstat' for reading: 
		No such file or directory
	m.	"amixer"				Results follow:
		amixer: Mixer attach default error: No such device
	n.	"asoundconf list"			No Results
	o.	"cat /etc/asound.conf ~/.asoundrc*"	Results follow:
		cat: /etc/asound.conf: No such file or directory
	p.	"dmesg"					No Audio Results
	q.	"cat /proc/interrupts:			Results follow:
           	CPU0       
		  0:    1022757    XT-PIC-XT        timer
		  1:      10223    XT-PIC-XT        i8042
		  2:          0    XT-PIC-XT        cascade
		  6:          2    XT-PIC-XT        floppy
		  7:          9    XT-PIC-XT        parport0
		  8:          3    XT-PIC-XT        rtc
		  9:          0    XT-PIC-XT        acpi, ohci_hcd:usb3
		 10:      30020    XT-PIC-XT        ohci_hcd:usb1, eth0
		 11:        132    XT-PIC-XT        ohci_hcd:usb2, sata_sis
		 12:     273809    XT-PIC-XT        i8042
		 14:      24534    XT-PIC-XT        libata
		 15:     136278    XT-PIC-XT        libata
		NMI:          0 
		LOC:          0 
		ERR:          0
		MIS:          0
	Got help at IRC.frenode.net#ubuntu from bsdunix
		bsdunix: BIOS settings; on-board sound disabled, plug and play 
		OS = no. then try to cat file-foo >/dev/dsp. you should hear 
		the file in your speakers
	Try both off, both on, each on/off, each off/on, still no sound.

```
Latest testing (12/10/07) I ran the command: "alsaconf" with the following results:
```

	modinfo: could not find module snd-opl3sa2
	modinfo: could not find module snd-cs4236
	modinfo: could not find module snd-cs4232
	modinfo: could not find module snd-cs4231
	modinfo: could not find module snd-es18xx
	modinfo: could not find module snd-es1688
	modinfo: could not find module snd-sb16
	modinfo: could not find module snd-sb8

```
Also discovered that I have no "/proc/asound" directory, which is suppose to be there.  Do not know why all this is failing, but need better understanding so I can debug this right.

According to all I can find the correct driver set is the file:
> 
	realtek-linux-audiopack-4.07a.tar.bz2

Latest alsa driver set is:
> 
	alsa-driver-1.0.9rc4a.tar.bz2

Downloaded both.

Looking in the Readme.txt file, after unzipping this archive, I worked the install both ways with autoconfig/install of:
```

	cd /home/<user>/myfiles/realtek-linux-audiopack-4.07a
	./install

```
and the manual step-by-step of:
```

	cd /home/<user>/myfiles/realtek-linux-audiopack-4.07a
	./configure
	make
	make install
	./snddevices

```
The following output, with errors, occurs on the make install cmd:
> 
	rm -f /lib/modules/0.0.0/misc/snd*.*o /lib/modules/0.0.0/misc/persist.o 
		/lib/modules/0.0.0/misc/isapnp.o
	make[1]: Entering directory `/home/<user>/myfiles/alsa-driver-1.0.9rc4a/acore'
	mkdir -p /lib/modules/0.0.0/misc
	cp snd-hpet.o snd-hwdep.o snd-page-alloc.o snd-pcm.o snd-rawmidi.o 
		snd-timer.o snd.o /lib/modules/0.0.0/misc
	cp: cannot stat `snd-hpet.o': No such file or directory
	cp: cannot stat `snd-hwdep.o': No such file or directory
	cp: cannot stat `snd-page-alloc.o': No such file or directory
	cp: cannot stat `snd-pcm.o': No such file or directory
	cp: cannot stat `snd-rawmidi.o': No such file or directory
	cp: cannot stat `snd-timer.o': No such file or directory
	cp: cannot stat `snd.o': No such file or directory
	make[1]: *** [_modinst__] Error 1
	make[1]: Leaving directory `/home/<user>/myfiles/alsa-driver-1.0.9rc4a/acore'
	make: *** [install-modules] Error 1

Found the realtek driver set contain another tar file of:
> 
	alsa-driver-rt20071002.tar.bz2

so re-running the manual step-by-step against this file with:
```

	cd /home/<user>/myfiles/realtek-linux-audiopack-4.07a
	tar xfvj alsa-driver-rt20071002.tar.bz2
	cd alsa-driver-rt20071002
	./configure
	make
	make install
	./snddevices

```
This ran successfully, so rebooting.  See where I'm after this.	

**Finally this is what was missing. Right driver set from the right directory!**.  Final PB with alsa-info.sh at:
> 
	[http://pastebin.ca/814907](http://pastebin.ca/814907)



**Open - High**
2. Video - In low res (800x600)

Talked with a NeddySeagoon on IRC who has a link to forum entry about using "ModeLine" for a custom res builder, which resolved this on my Gentoo box.  Found NeddySeagoon again and link is:
> 
	[https://forums.gentoo.org/viewtopic-p-3276263.html#3276263](https://forums.gentoo.org/viewtopic-p-3276263.html#3276263)


with link to autogen script at:
> 
	[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Ran the modeline generator script but still having problems.  Reboot comes to X-Win "Low-Res" Pop-up with "Configure", "ShutDown", "Continue".  Configure hangs and machine has to be manually rebooted.  Continue of course puts you back in the Low-Res mode.  I was forced to level of 15 with my Gentoo configuration, trying to resolve this.

(12/20/07 Entry)
Worked with "soundray" on IRC and ran the "ddcprobe" command (had to boot to "recovery" mode because command locked the machine forcing hard reboot.  Later found that "/etc/init.d/gdm stop" will allow the command to run without locking the machine.).  I found the native information for my monitor to be:
> 
	Res:	1280x1024
	Vert:	55-75
	Horz:	30-80	(anything about 77 however produces errors)
	Name:	A911B
	VRam:	2048

Working with this I again reset the vals in the xorg.conf and restarted gdm, with "No Signal" response from the monitor, forcing me back to "failsafe".

I had been emailing to NeddySeagoon and he responded, after viewing the xorg.conf and Xorg.0.log file with:
> 
RL has soaked up some of my free time.  Lets have a look at your log.

(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules//libglx.so

(II) Module glx: vendor="NVIDIA Corporation"

	compiled for 4.0.2, module version = 1.0.9639

	Module class: X.Org Server Extension

	ABI class: X.Org Server Extension, version 0.1

Tells that your glx library is provided by nVidia. Thats no use to you 

as it only works with the nVidia binary blob driver, which in turn 

needs nVidia hardware.

Gentoo keeps the various glx libraries separate and provides eselect 

opengl to chose one to be used. Binary distros normally have no need of 

this. You need to get the xorg replacement for /usr/lib/xorg/modules//

libglx.so to fix this.  Its only a problem if you tried to use OpenGL. 

Everything else should work, so its not your blank screen issue.



This section tells about your display the data is read from the EDID 

data provided by the display.

(--) s3(0): Max pixel clock at this depth is 135 Mhz

(II) s3(0): AMW MR19C-AB: Using hsync range of 30.00-160.00 kHz

(II) s3(0): AMW MR19C-AB: Using vrefresh range of 55.00-120.00 Hz

(II) s3(0): Clock range:  15.60 to 135.00 MHz



The Using vrefresh range of 55.00-120.00 Hz is a little worrying as 

most LCDs start lower and don't go so high. Google dosn't help and the 

AMW web site is totally useless.



From your config file 	

	HorizSync	30 - 160

	VertRefresh	55 - 120

Xorg seems to be doing what you tell it. Comment those two lines out.

For testing, comment out your Modeline, which xorg has picked up.  It 

may use that in preference to the EDID provided values.





The EDID should provide correct values. If that fails try a fixed 

	VertRefresh	60

As every LCD ever made will operate at 60Hz. Do not specifiy a 

HorizSync. 



It may well be that your monitor does not support 1152x864@73 but a 

lower refresh rate will be ok.



Starting here

(--) s3(0): Virtual size is 1152x864 (pitch 1280)

(**) s3(0): *Mode "1152x864@73": 107.7 MHz, 66.3 kHz, 73.1 Hz

(II) s3(0): Modeline "1152x864@73"  107.74  1152 1184 1592 1624  864 

881

891 908

(**) s3(0): *Default mode "1152x864": 121.5 MHz, 77.5 kHz, 85.1 Hz

(II) s3(0): Modeline "1152x864"  121.50  1152 1216 1344 1568  864 865

868 911 +hsync -vsync

xorg tells its operating at 1152x864 but its not clear which modeline 

is in use. 





(**) s3(0): Depth 8, (--) framebuffer bpp 8

(==) s3(0): Default visual is PseudoColor

Says the system is operating in 8 bit colour This ties in nicely with 

your 	

DefaultDepth	8 

statement in the config.  





The log says (--) s3(0): videoRam = 2048 Kb

so you have at most 1Mb for your pixel buffer while you use the double 

buffer extension (dbe)  1152x864 just fits, you need 995,328 bytes





Everything else looks normal.



Its worth reading   man s3 to see if the s3 driver supports any LCD 

specific options. Some drivers need to know if the display is an LCD or 

CRT, some don't.



Just now, I suspect your display is blank because it does not support 

the resolution you are trying to operate in.



I hope that helps,

Followed the advise and restarted gdm but still the same results.

I sure am frustrated with this.


**Closed (12/13/07)**
3. CUPS/Printing (both - use localhost on DT for pre-production development)

Both show printing active but used to admin of CUPS through Web Browser, using Launcher in Launch Panel and not able to run this way.  Current Ubuntu Admin locks if config fails.  Also the current Ubuntu printer admin will not find my printer on the network which is an HP4L attach via a NetGear PS110 print server box.  Had to load customer drivers on the Gentoo box and suspect same here but do not have any options to work with, especially directory searching for drivers, like from the Browser based CUPS environment.

Finally found info on this for CUPs on localhost at: localhost:631.  Then had config problem and had to download new .ppd file from:

	[http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)
	
Then install of new printer corrected the problems (deletion of old).  Also cleaned up the extra .ppd files in /etc/cups/ppd.  Also edited the .ppd with the following 2 lines changed:

	*ImageableArea Letter/US Letter: "18 36 582 744"

	*PaperDimension Letter/US Letter: "600 780"

to set up correctly for lp/lpr printing.

Sometime printing is sending .PDF version of .ppd file to printer and therefore sending out garbage.

**Closed (12/04/07)**
4. LAMP (both - use localhost on DT for pre-production development)

Boot shows all this loading by having trouble with accessing it all, espacially the phpmyadmin that I'm used to using to drop-in my SQL code.

The config file /etc/apahce2/httpd.conf is blank an finally realized the install is using file /etc/apahce2/apache2.conf.  Do not see the "include" link there, for the PHP5 or phpmyadmin, which shows on my other machines.

Finally got through all this and got it working, but want to build a launcher, similar to the WAMP launcher for Window, where everything pops from the menu.  If you know a pre-built launcher for this, link please.  If we can not find that and you have launcher build experience let's talk.

**Closed (12/05/07)**
5. Domains-Virtual Hosts (Apache)

I had a Virtual Host problem, which I posted my problem on ApacheLounge at:

[http://www.apachelounge.com/forum/viewtopic.php?t=2093&highlight=](http://www.apachelounge.com/forum/viewtopic.php?t=2093&highlight=)

But now have that solved.

**Open - Low**
6. Launchers(DT) - Launch Panel

Trying to build Launch Panel launchers for CUPS, ?? and Remote Server SSH.  Know how to build them in the Menu system with file in:

	/usr/share/applications/<men_lauch>.desktop

Just no experience with Launch Panel launchers.

**Open - High**
7. Ubuntu Server - Load Balancing

Have onboard NIC and two 3-Com NICs.  Inet served on two 3-Coms.  Network on the onboard NIC.  Need to do:

   a. IP monitoring - to know if one or both are up,
   b. IP routing - to route IP specific traffic through the right provider 
      (such as email, due to "no forwarding" on most)
   c. Load Balancing on the lines 
      (like merging them together, but both have seperate ISPs)

**Open - Low**
8. VM-Ware (both)

Once I get the problems with both installs resolved, so I am steady and fully operational, I want to install VM-Ware so I can port all my Windows apps and get off Windows.  I have over 5,000 apps and 20 development platforms on the Windows box, so full operation is critical before transitioning.

Hope I can get some help.

Thanks!

OMR

---

### Post by OldManRiver on 2007-12-12
All,

Why is it so hard to get help with Sound and Video?

These are my two main problems, for now!

OMR

---

### Post by OldManRiver on 2007-12-12
All,

Why is it so hard to get help with Sound and Video?

These are my two main problems, for now!

OMR

---

### Post by OldManRiver on 2007-12-13
All,

Finally resolved the Sound problem, so updated the beginning post as HOWTO.

OMR

---

### Post by OldManRiver on 2007-12-14
All, 

Adding the xorg.conf file and the captured log file.

I attached the xorg.conf, but the log was too large so it is at:

[http://pastebin.ca/816131](http://pastebin.ca/816131)

OMR

---

### Post by OldManRiver on 2007-12-18
All,

Why is there no response on my post.  Is there not at least some small contribution, which can be made somewhere to assist?

OMR

---

### Post by OldManRiver on 2007-12-20
Help Please!

---

### Post by oldsoundguy on 2007-12-21
You seem to indicate that your are dealing with an on board sound chip .. as to the video, if that is also ON BOARD, you should seriously consider replacing both with plug in cards unless this is a laptop.
Creative for sound an nVidia or ATI for the video are cards that WORK (nVidia has Linux support) (ATI is coming on board, but is late for the party!) and have worked through all types of builds from all types of sources.

---

### Post by Sef on 2007-12-21
You should post each problem separately.  You could get them more quickly resolved.  If you want to keep a track of all of them, then when you post each problem, change the notification type.  (It is just below manage attachements.)

---

