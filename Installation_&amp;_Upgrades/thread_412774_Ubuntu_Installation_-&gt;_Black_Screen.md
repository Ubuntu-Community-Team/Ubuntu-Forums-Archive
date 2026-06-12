---
title: "Ubuntu Installation -&gt; Black Screen"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by NiteRidah on 2007-04-18
Greetings,

I've burned the Ubuntu 6.10 Live CD and booted my PC with CD in drive.

It works fine and I get the menu. When I choose to install, I get the loading bar, and after that, the screen is black with a line blinking on the top left corner. Then comes some text; *Activating Swap, mount not implemented, checking files systems...* (can't remember exactly what).

But after that, the screen turns totally black, CD stops spinning and nothing happens.

My PC is old;

Celeron 1Ghz, 192mb RAM, 8Gb HD, GeForce 4 420MX 64mb. And I'm currently using Windows XP.

I'd hope to be able to use Ubuntu only (no dualboot). If you need any more info, I'll try to provide that. This is my very first time trying out Linux. I've searched forums and docs for info, but no luck (though I'm sure there is).

Thank you for any help.

---

### Post by mick0142 on 2007-04-18
have you tried the install in safe graphics mode?

---

### Post by Lise on 2007-04-18
I' ve just the same problem:
I took the option : safe graphics mode

I've an acer 1694
ATI RADEON X700 256MB (which is probably the cause)
intel pentium M processor 2,0 GHz
100GB HDD

---

### Post by NiteRidah on 2007-04-18
Unfortunately, *safe graphics mode* doesn't work either...

---

### Post by Voland on 2007-04-18
Try alternate CD

---

### Post by Lise on 2007-04-18
> **Voland said:**
> Try alternate CD

This worked indeed, but only if i changed ati to vesa. 
Hopefully that it works with feisty to.

---

### Post by UrbanFallout on 2007-04-24
Hi

I too have a an Acer 5024 WLMi, but I think will help anyone with an ATI express card on a laptop.

I managed to get x going by doing the following:

1. Select the default option for booting and wait the 3 minutes or so for it to boot up. You will of course be presented with a blank screen.

2. **Press Ctrl+Alt+F1**. You will be presented with a text terminal screen.

3. Type 
```
sudo dpkg-reconfigure xserver-xorg
```
This will start a script to reconfigure your xserver. You will be presented with a series of text dialogs requesting choices to be made or telling you how to select options appropriately. In almost every case you can select the default option.

4. However on screen 2 for the [COLOR="Red"]X server driver[/COLOR], **Select "vesa"**. You can navigate to it by using the up down arrow keys. Then **Press Enter**. 

5. In some information windows "OK" is not highlighted. **Press the TAB button** to select OK and then **Press ENTER**.

6.On about screen 10 or so, you will be presented with a "[COLOR="Red"]X.org server modules[/COLOR]" screen. **Make sure "int10" is deselected**. You can do this by navigating to "int10" with the arrow keys and Pressing the SPACE BAR.

7. About 5 screens after that you will be presented with a dialog requesting what [COLOR="Red"]video resolutions[/COLOR] are valid for your monitor. **Select the relevant resolutions** (in my case 1280x800) by navigating to it with the arrow keys and pressing the SPACE BAR.

8. About 5 screens after this is a dialog requesting what [COLOR="Red"]bit-depth[/COLOR] to use. **Select 16** with the arrow keys and press ENTER. 24 bits appears to fail for some reason.

9. Press enter for the remaining few dialogs.

10. Now type
```
startx
```
in the terminal window.

This should get you far enough to start the actual installation. After installation you will probably need to read the howto on installing the ATI driver. Don't be too daunted. This is not as difficult as it first seems.

Hope this helps
Nick

---

### Post by UrbanFallout on 2007-04-25
Actually, if your network is up and running this post gives a more elegant solution:

[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=414723]("http://ubuntuforums.org/showthread.php?t=414723")[/COLOR]

---

### Post by Biotech80 on 2007-04-25
I have a similar problem with the 64bit version of feisty and the ATi X700 video card. After some trouble i successfully installed Ubuntu, but now when i start the system after the GRUB my monitor turns off. it goes in stand-by mode. And Caps-Lock and Scroll-Lock leds on the keybord starts winkling!
If i select the "Recovery mode" option instead, the system loads correctly and with the "exit" command i can login and use ubuntu. 
Any suggestion to fix this problem is welcome :)

---

### Post by FlavianiC on 2007-04-25
I had the same issue:
My machine is an ASUS FJP - Dual Core2 and ATI Radeon mobility X1700 256 MB video card.
I installed Ubuntu 6.10 without any problem by selecting the safe video option.
With Kubuntu 7.04/Feisty, it did not work. My screen was not recognized. I had a black screen with the cursor blinking in the left upper corner.
Checking /var/log/Xorg.0.log gave me at the end "Fatal server error: no screens found" (you can switch to a console by CTRL+ALT+F1...)
I copied the following into /etc/X11/xorg.conf
```
Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```
Reboot the kdm/X server /etc/init.d/kdm restart and you'll get your X window, allowing you use the live CD and install 7.04 / Feisty

Regards,

Christophe

---

