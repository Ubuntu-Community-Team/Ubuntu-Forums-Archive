---
title: "New install, huge black margins on screen."
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by moonshinerat on 2008-03-02
Hello again all,

been a while since I posted but I've just got round to reinstallng Gutsy after a brief fling with Solaris (required by work, not me).

Got a major problem with my widescreen monitor though (stop groaning at the back!). My system is shared with Windows XP which has had no problems at all. However, after installing Gutsy my monitor will not display correctly at 1440 x 900. This is not your usual 915resolution problem because Gutsy is apparently displaying at this resolution according to the "Set Resolution" dialog. Problem is I have a 7cm black margin down the left hand side and a 1cm margin down the right hand side. It is like the monitor is running at 1024 x 768 across the full screen but displaying a 'virtual' 1440 x 900 squashed up and offset to the right. The text is barely readable and reminds me of my old Atari on an SM124.

I've been across hundreds of posts and many of them don't have even 1 response never alone a solution. I've tried playing with xorg.conf and the modelines without success. I've tried to follow another post on Ubuntu forums which 50% of the readers claim working but I don't understand the thread, there is no final solution.

Please can someone help out with this. My monitor is a Samsung 920NW 19" Widescreen TFT. I have an Intel 945 chipset with integrated graphics. If it is any help I've tried the Fedora LiveCD, a Debian install and PClinuxOS all with the same issue. I've only used these for testing, I need Ubuntu because work depends on it.

Many thanks everyone.

---

### Post by Rocket2DMn on 2008-03-03
It seems to me like this is something you would have tried, but since nobody else has offered help, here goes.
Did you reconfigure X manually?  Here's how: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
You would select the "intel" driver, there is no difference between i810 and i915 now, it's all in one driver.
You can also post your xorg.conf file (before or after you reconfigure, just state which):
```
cat /etc/X11/xorg.conf
```
Let me know what happens.

---

### Post by moonshinerat on 2008-03-03
No luck unfortunately. Worst thing is that there are only two monitors available in the whole city where I live (no exageration) the LG192 and the Samsung 920NW. The LG was aweful and couldn't produce any kind of native mode, even in Windows.

Here is my xorg.conf. I've cleaned it up since playing with the modelines.

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x900" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"



I really hope someone can help me out, I've only got 48 hours left til I'm back at work and all the machines there use Ubuntu. Thanks Rocket for at least providing a response and a possible solution.

---

### Post by Rocket2DMn on 2008-03-03
From all my experience dealing with configuring X and helping out people on the forums with their graphics stuff (and it's a lot), I have found it to be a rare occasion that manually editing xorg.conf in a text editor actually works, so I recommend against that.  (When I said manual above, I meant running the script and answering the questions it asks rather than having it auto-generate a new xorg.conf file by using the -phigh flag.  Sorry for any confusion.)
If doing the configuration in the link I provided above doesn't work, you may want to give the "vesa" driver a try to see if you can get the correct resolution to work in that safe graphics mode driver.  Otherwise it would seem to be a problem with the monitor itself, so you should check to see if others have had problems with this monitor, and see if there are any buttons on the screen to adjust the appearance.

---

### Post by tm8992 on 2008-03-04
I'm having *this exact same problem*--a few inches of black on the left, a cm of black on the right, squashed screen.  I'm using a Viewsonic 19" wx1935wm and an Intel graphics card.
I believe this problem is either ubuntu-specific or due to an outdated intel driver (which seems unlikely because it is close to the latest version, :s)
Using Arch Linux, I am able to use the intel driver and [this xorg.conf](http://hippo.us.to/tim/files/xorg.conf).  But using ubuntu, this same xorg.conf has no effect--still the squashed screen.
This xorg.conf has also worked in Debian Etch, and Fedora was able to auto-detect the hardware/have a correct resolution without the xorg.conf (which was impressive).

Thoughts?

---

### Post by moonshinerat on 2008-03-04
Evening folks.

I can now confirm this is definitely an Ubuntu issue. I have spent the last two days downloading and installing distros. Debian, Fedora, PCLinuxOS, Mint, Slackware, Gentoo (compiled in 7 hours!!!), Mandriva and DSL all work without a problem. I have reinstalled Xorg on Ubuntu and the Intel drivers. I have tried the Intel i810 and Experimental drivers along with every modeline combination I can find that is compatible with this monitor.

What I have also found is that once I had this monitor connected (in preference to my old 15" CRT Syncmaster) I couldn't use any desktop effects including Compiz or even just shadowed text.

I have now found many 'supposed' solutions but I have tried them all from LinuxForums, LinuxQuestions, UbuntuForums, and even a solution from Samsung by email. None of the methods have worked so I'm pretty convinced it is Ubuntu.

I hope they do something about this for Hardy because I'm trying to promote Linux in South America and the Samsung 920nw is one of only two monitors available at the moment in most countries down here. I know there are other distros but Ubuntu is the one that is known and has a chance against Windows.

---

### Post by heatpumpcontrol on 2008-07-07
Hey guys,

I've discovered that if you just use the nvidia settings control panel instead of the System->Preference->Screen Resolution option then you can obtain the desired graphics display. That is what I'm using right now in Gutsy. Should be the same in Hardy.

---

