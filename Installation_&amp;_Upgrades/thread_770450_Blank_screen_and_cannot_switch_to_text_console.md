---
title: "Blank screen and cannot switch to text console"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Czubek on 2008-04-27
Hi all.
I have problem.

I installed Ubuntu 8.04 hardy heron from alternate cd. Everything was ok.
But after first reboot after installation it stopped on blank screen.

Step-by-step:
1. power on;
2. grub, selecting "Ubuntu 8.04, kernel 2.6.24-16-generic";
3. system is starting, ubuntu logo with loading progress bar; 
4. when progress bar is about 99% complete, screen blink;
5. for about 2-3 seconds blinking "_";
6. black blank screen;

7. cannot switch to text console with ctrl+alt+f1
7a. i guess i have switched to text console because even i'm not seeing anything i log in like blind and when i press ctrl+alt+del, after some time ubuntu shutting down progress bar appears and it's going to 0%

I'm using ubuntu since 5.04 and i have the same problem on 7.10 but i haven't solved it and i was still using 7.04 :/

My hardware:
Toshiba satellite 1800-554 laptop:
-celeron 1 ghz;
-2x 256 sdram;
-vga compatible controller: Trident Microsystems CyberBlade/i1 (rev 5d)
-lcd 14.1

Thanks.

---

### Post by liyu on 2008-04-27
it seem that your X window failed to startup. I think you can try to use resuce mode in installation CD to enter system for changing X disaplay adapter to vesa? (in /etc/X11/xorg.conf)

---

### Post by Czubek on 2008-04-27
> **liyu said:**
> I think you can try to use resuce mode in installation CD to enter system for changing X disaplay adapter to vesa? (in /etc/X11/xorg.conf)

I'm not sure of which part of xorg.conf you are talking about. This is my xorg.conf:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by claudio64 on 2008-04-27
Hi,

I manage to access the console chosing "safe mode" in the boot menu.

Then I log as root and edit xorg.conf using vim.

At end of "Section Screen" I included:
SubSection "Display"
    Modes  "1024x768" "800x600"
EndSubSection.

Good luck!
Claudio H

---

### Post by Czubek on 2008-04-27
> **claudio64 said:**
> 
At end of "Section Screen" I included:
SubSection "Display"
    Modes  "1024x768" "800x600"
EndSubSection.


Thanks but it doesn't help me.

Now my xorg.conf looks like:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	[B]SubSection	"Display"
		Modes	"1024x768" "800x600"
	EndSubSection[/B]
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by LeDieu on 2008-04-27
I have the exact same problem. Only this problem occurs at the boot of the live cd. So i cant even install (k)ubuntu.
Is there for this problem a solution yet?

---

### Post by Czubek on 2008-05-01
I also tryied this: [http://www.backports.ubuntuforums.org/showpost.php?p=4553231&postcount=15](http://www.backports.ubuntuforums.org/showpost.php?p=4553231&postcount=15)
but it wasn't help :(

---

### Post by LeDieu on 2008-05-01
For me this topic was the solution.
I hope it will work for you all to.

[http://ubuntuforums.org/showthread.php?t=766372](http://ubuntuforums.org/showthread.php?t=766372)

---

### Post by Czubek on 2008-05-02
> **Czubek said:**
> I also tryied this: [http://www.backports.ubuntuforums.org/showpost.php?p=4553231&postcount=15](http://www.backports.ubuntuforums.org/showpost.php?p=4553231&postcount=15)
but it wasn't help :(

After that it was even worse, so I had to go before those modifications

> **LeDieu said:**
> For me this topic was the solution.
I hope it will work for you all to.

[http://ubuntuforums.org/showthread.php?t=766372](http://ubuntuforums.org/showthread.php?t=766372)

It will not work for me cause I dont have ati card ;)

---

### Post by erginemr on 2008-05-02
What bothers me about your xorg.conf file is that you don't have a "screendepth" line anywhere. There should have been lines like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	**DefaultDepth	24**
	SubSection	"Display"
                **Depth	24**
		Modes	"1024x768" "800x600"
	EndSubSection
EndSection
```

Can you please try these as well?

You can also try backing up your current xorg.conf file and then run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
all the while in the "recovery mode".

---

### Post by Czubek on 2008-05-02
> **erginemr said:**
> What bothers me about your xorg.conf file is that you don't have a "screendepth" line anywhere. There should have been lines like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	**DefaultDepth	24**
	SubSection	"Display"
                **Depth	24**
		Modes	"1024x768" "800x600"
	EndSubSection
EndSection
```

Can you please try these as well?
Didn't help :(

> **erginemr said:**
> You can also try backing up your current xorg.conf file and then run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
all the while in the "recovery mode".
Didn't help :(

---

### Post by Czubek on 2008-05-02
I think problem is bigger than I thought:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162757](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/162757)

---

### Post by yang83 on 2008-10-15
Tried to install 8.04 on to my dell desktop with ATI x700 PCIE video card.  After selecting "noapic apci=no nolapic" by pushing F6 during the installation process. I was able to fully install ubuntu without a problem.  After the installation finished it asked to reboot the system. Upon restart, system goes through grub then a blank screen with "_" on the top left corner.  Alt+ctrl+F1 yields not effect.  Booting into recovery mode does nothing as well.  This is a fresh install.

Dell Optiplex 320
Pentium Core Duo
1gb of ram
ATI X700 pci-e

---

### Post by Czubek on 2008-10-15
> **yang83 said:**
> Tried to install 8.04 on to my dell desktop with ATI x700 PCIE video card.

That's completely different card than my, but looks like the same problem. 
I have this problem from Ubuntu 7.10 to 8.10 beta.

Now I'm using Debian Etch because there is no working and supported Ubuntu version :(

---

