---
title: "When moving the mouse on the 8.04 live cd, it leaves a little square..."
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by OrangeCrate on 2008-08-13
On my older computer, which is a HP 512n (integrated video), I upgraded from 7.10 to 8.04 with no problems, and it's working fine.

I ordered several live CDs from ShipIt, to hand out to friends, and I tried one of them in this computer.

It's a little hard to explain this, but on boot, everything looks O.K., until you move the cursor. Then it leaves a small square. Every time you move the cursor, another square. Also, menus appear broken up when you access them.

There's no restricted drivers needed, so I'm a bit confused about what's happening. I've been through several upgrades with this machine, so I wouldn't mind doing a clean install of 8.04, if I could figure out how to fix this.

Several search strings reveal nothing about this on the forums that I could find. If I missed something, please link me to the thread.

Thoughts?

---

### Post by danmux on 2008-08-14
I have the same problem with a clean install on an old server.

If I find out how to fix I'll post back here

---

### Post by OrangeCrate on 2008-08-14
> **danmux said:**
> 
If I find out how to fix I'll post back here


That would be great, thanks. I've done a bit more research on this today, and still can't find a solution.

---

### Post by BrainStorms on 2008-08-17
I'll be darned but that just happened to me this evening...  I re-installed 8.04 on a machine that had no previous problems with the video -- then this.  I just re-installed to try to clear it, and got the same thing.

The worst of it is, this machine's for my mom.  Great selling point! 

ASUS M2V-MX using on-board Trident DeltaChrome video.

---

### Post by BrainStorms on 2008-08-17
More info on this:

When I boot the 8.04 LiveCD, doesn't happen...
When I boot my WinXP partition, doesn't happen...
When I boot my installed 8.04, it happens.

It happened when I re-installed hardy: I split my Ubuntu partition & moved my /home directory to the new ext3 partition, then re-installed with my /home partition mounted in / as /home.  Had the problem, so I repeated the install.  Same symptoms.  There's something about what's on my HD, possibly in my /home tree -- but what???

The only other change is that I added a second 1GB DIMM stick when I had my original install on the drive -- but it ran fine.  I did notice in the BIOS that ECC was turned on; my RAM is not ECC, so I turned it off -- didn't help.

I've got an ASUS M2V-MX mobo, AMD Athlon 64 3800+ 2.4 GHz, with a VIA chipset.  (I'm an Intel guy, but the BIOS reports a "K8/NPT to NB" Vlink, set to 'freq auto enabled'.)  I'm using the on-board Trident DeltaChrome VGA w/ Vlink on Auto, AGPx8.  I've got it configured with 128MB shared RAM frame buffer and a 128MB graphics aperture (i.e., more than enough).

It boots loading the 'openchrome' drivers; the other 'xorg.conf' settings have always been kept at the "out of the box" settings and were driving the video just fine (resolution, etc) to a 1280x1024 LG LCD...

All of which are FINE: The LiveCD boots & operates the VGA with no problems.  It's only when it boots the installed image that this occurs.  It looks as though a HW cursor & SW cursor become "decoupled", then it starts these "square box" cursor trails.  I say this because on boot up to splash screen, I can see the "busy wheel", which persists even when I log in.  When I first move the cursor, I can see the pointer (arrow) appear "out of" the busy wheel cursor, which remains frozen on the screen.  I'm interpreting this that the cursor arrow is a HW cursor and the busy wheel must be a SW cursor -- but why would this decoupling occur?

When this occurs, it's apparently painting the pixels immediately surrounding the cursor's 'hot spot' (a square box centered on the hot spot) with what I would term "the background frame"; that is, when it boots & shows the splash screen, and there is no background, it paints these cursor trails with random garbage that's in this 'background frame buffer'.  After logging in, and opening an app window, it repaints the area around the cursor with the desktop wallpaper image -- i.e., what I'm calling a background frame buffer.  (Which means, when it passes over a menu bar, which has no background, it paints garbage on the menu bar.)

So... What could be causing the video driver to loose its cookies when it comes to cursor control?  And why only when I boot my hard drive image?  Could the data in my /home directories that survived my rebuild be triggering this??

I'll keep working on this, but I'm hoping someone beats me to it...

-T

---

### Post by BrainStorms on 2008-08-17
Problem resolved -- but not solved, unfortunately...

I believe I did it.. But I don't know what it was that caused it.  When I first re-installed 8.04, it was on a newly-created partition.  For reasons I don't recall clearly, I attempted to do an install from a booted LiveCD session, but aborted the install.  I then re-booted the LiveCD and went back to installing once again...

I was doing a manual install since I had a separate (preserved) /home partition, so I partitioned manually, assigning the partitions.  My root partition was going back on the same partition -- the same one that had an aborted install.  I'm not sure if I failed to check "Format this partition" or not.. I think I did (I'm very careful), or the installer looked at it and concluded "Yep, it's already EXT3, no need to do anything".  Whichever reason, it did NOT wipe the partition, and installed on top of its (corrupted), partial install.

Which gave me the cursor trails.  After 6 hours of torturing my 'xorg.conf' file and restarting X until it began swearing at me, I gave up.  Then it dawned on me... I rebooted the LiveCD, found I could *not* delete the target partition (why??), so I re-formatted it as FAT32 to blow it away.  Then I did the install all over again (this time being sure to tell it to format the drive, which it did)...

And the problem was gone.  And as of right now, I'm back to where I started.  Now, back to tackling a recalcitrant VMware dual-boot config!

---

### Post by momcatjane on 2008-08-21
I'm the one whose computer you fixed!  Thank you very much!  :lolflag:

---

### Post by BrainStorms on 2008-09-02
More input for this:  

This seems to be a bug in the 8.04 Hardy installer.  When [this machine, at least] is booted into a LiveCD session, then the installer is invoked by double-clicking the 'Install' icon on the desktop, this problem occurs.  However, when an installation is made by booting the LiveCD and choosing "Install Ubuntu" instead (i.e., no LiveCD session is started), the problem does NOT occur.

Perhaps this will be fixed in 8.10..??

---

### Post by OrangeCrate on 2008-09-05
> **BrainStorms said:**
> More input for this:  

This seems to be a bug in the 8.04 Hardy installer.  When [this machine, at least] is booted into a LiveCD session, then the installer is invoked by double-clicking the 'Install' icon on the desktop, this problem occurs.  **However, when an installation is made by booting the LiveCD and choosing "Install Ubuntu" instead (i.e., no LiveCD session is started), the problem does NOT occur.**

Perhaps this will be fixed in 8.10..??

I took the leap, and tried the install as you outlined. Unfortunately, it still didn't work for me.

So, rather than reinstall Ubuntu 7.10, and then upgrade again, I went with an alternate install CD of Xubuntu 8.04, and it worked fine.

I'd sure like to figure this out though...

---

### Post by geno123 on 2008-09-13
Same problem on Hardy installation that previously was fine.  Since the pointer paints over any icon it touches, I can't get any app to function!!!

---

### Post by geno123 on 2008-09-13
My problem appears related to screen resolution.  If I pick a screen resolution that decreases the desktop size to the size of the monitor screen, the problem disappears.

---

### Post by benali72 on 2008-10-03
Here's my version of what appears to be the same problem---

My machine -- Dell 933r P-III with 512 M ram and Dell 1028L monitor. The video adapter integrated in the Dell motherboard is i810 chipset (Intel 810).

I booted the 8.041 Live CD, it came up fine with 1280 x 1024 screen.  I *really* wanted 1024 x 768 so I could view the screen easier, so I did PREFERENCES -> SCREEN RESOLUTION and changed to 1024 x 768 in the GUI.

The screen was now 1024 x 768 and looking good.  So I double-clicked on the INSTALL icon, and the install went fine.  When I rebooted into Ubuntu afterwards, the GUI login panel looked good, but then after my login the screen went into some bizarre pattern.  I never got to a good desktop screen.

Next couple tries -- I booted Puppy Linux off a Live CD, and edited the Ubuntu install's /etc/X11/xorg.conf file, trying several valid combinations that work for Puppy on this box.  All failed when I booted Ubuntu, producing either a blank screen or some bizarro pattern after booting Ubuntu.

(During this process I learned a better way of testing different xorg.conf files in Ubuntu... just boot into the RECOVERY MODE version of Ubuntu offered by the default /boot/grub/menu.lst file... then select XFIX off the text menu.  This puts you back to your original xorg.conf file without having to use an external operating system like Puppy).

Thought I'd retry the Ubuntu install from scratch -- I booted 8.041 Live CD again, came up with 1280 x 1024 screen.  Tried to install it by double-clicking the INSTALL icon.  This time the install went fine and machine comes up fine to 1280 x 1024 screen. I have a good install and everything works great.

To change to 1024 x 768, this time I try a different tactic.  Instead of using the GUI for changing screen resolution at PREFERENCES -> SCREEN RESOLUTION, I just went straight to editing the xorg.conf file.

I finally ended up with the xorg.conf file listed below.  It gives me a 1024 x 768 screen just fine, but now I get the mouse-leaves-boxes-behind phenomenon (plus the mouse doesn't move smoothly across the screen).

Someone in this thread mentioned the "mouse-leaves-boxes" is a bug.... that makes sense to me, because I've never seen a case where moving down to LOWER resolution presents this kind of problem (normally, it's moving to HIGHER resolution that gives adapter issues).

If anyone has any ideas I'd appreciate it and will try them.

Meanwhile it looks like I'll be developing my expertise in xorg.conf MOUSE sections....  :D


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
    DefaultDepth 16
    Subsection "Display"
        Depth       16
        Modes       "1024x768"
    EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by benali72 on 2008-10-03
I was able to resolve the situation where the mouse was leaving little boxes behind as I moved it.

My basic resolution was--

(1) manually edit the /etc/X11/xorg.conf file
(2) restart X server to test by hitting Ctrl-Alt-Backspace
(3) if the screen fries and becomes uncontrollable, reboot the computer and when Ubuntu starts up, select RECOVERY MODE, then select XFIX to get back to the previous xorg.conf file (the original one that works but leaves little boxes behind the mouse).
(4) if the screen does not fry and become uncontrollable, see whether the xorg.conf solves my screen & mouse issues.  If not, just edit xorg.conf file and try again.

Eventually I came up with the xorg.conf file below that works perfectly for both the screen at 1024 x 768 and also the mouse, solving the "mouse boxes" problem---

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Monitor"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by benali72 on 2008-10-03
My resolution leads me to believe that those having the "mouse box" problem should be able to fix it if --

(1) their computer has sufficient memory
(2) their video adapter can support the resolution they're trying to use
(3) they manuaaly edit xorg.conf to what will work on their computer

The "mouse box" problem appears to me to be a bug in Ubuntu 8.041 that one has to find a work-around with by editing xorg.conf.  (in other words, not every correct xorg.conf file will work due to the mouse-box bug but one should be able to find an xorg.conf file that works around the problem.)  The difficulty here is that this might require xorg.conf coding knowledge, depending on the complexity of the work-around.

hope this helps.

---

### Post by OrangeCrate on 2009-01-29
> **OrangeCrate said:**
> On my older computer, which is a HP 512n (integrated video), I upgraded from 7.10 to 8.04 with no problems, and it's working fine.

I ordered several live CDs from ShipIt, to hand out to friends, and I tried one of them in this computer.

It's a little hard to explain this, but on boot, everything looks O.K., until you move the cursor. Then it leaves a small square. Every time you move the cursor, another square. Also, menus appear broken up when you access them.

There's no restricted drivers needed, so I'm a bit confused about what's happening. I've been through several upgrades with this machine, so I wouldn't mind doing a clean install of 8.04, if I could figure out how to fix this.

Several search strings reveal nothing about this on the forums that I could find. If I missed something, please link me to the thread.

Thoughts?

For those that might have been following this thread, I finally figured this little puzzle out...

On earlier Live CDs, during installation, it recognized that this old chip set couldn't handle any visual effects, and it defaulted to "none" during install. Starting with the 8.04 Live CD, and then the 8.10 disk, it did not recognize that the effects could not run, and it defaulted to "Normal". A conflict then occured, and the little squares show up on the display.

As soon as I went to Appearance Preferences > Visual Effects > and changed the setting from "normal" to "none", everything was fine.

---

