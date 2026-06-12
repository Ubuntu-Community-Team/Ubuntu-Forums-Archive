---
title: "Upgraded monitor - hibernation failed"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by paulEU on 2007-08-25
Hello!

I have problem with hibernation since when I changed monitor into newer model (15" LCD -> 20" LCD). After change monitor, I fixed xorg.conf and it works fine for 1400x1050 resolution, I'm using driver nvidia.

Hibernation works without problems on old monitor, now I'm doing (System -> End -> Hibernate) and it works OK, but when I try get back on the computer, ubuntu is booting (showing splashscreen with progress bar) and it appear login screen window - I have black window (empty) and cursor of mouse is visible. Mouse of course works, keyboard works only with command SysRq, other command doesn't works (for example: Ctrl+Alt+F1).

I tried update initramfs:

sudo update-initramfs -k all -u

But it doesn't work too..

In /var/log/messages I don't have any errors.. see below:

Aug 25 08:33:43 pc-desktop gnome-power-manager: (pauleu) Resuming computer
Aug 25 08:33:46 pc-desktop kernel: [   26.943909] 8139too Fast Ethernet driver 0.9.28
Aug 25 08:33:46 pc-desktop kernel: [   26.946656] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 19
Aug 25 08:33:46 pc-desktop kernel: [   26.949015] eth0: RealTek RTL8139 at 0xf8858000, 00:c0:26:31:af:35, IRQ 19
Aug 25 08:33:46 pc-desktop kernel: [   26.949759] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug 25 08:33:46 pc-desktop kernel: [   26.952329] eth1: RealTek RTL8139 at 0xf8a86000, 00:40:f4:8e:ff:b8, IRQ 18
Aug 25 08:33:46 pc-desktop kernel: [   27.153957] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Aug 25 08:33:46 pc-desktop kernel: [   27.170785] eth1: link down
Aug 25 08:33:46 pc-desktop kernel: [   27.170843] ADDRCONF(NETDEV_UP): eth1: link is not ready
Aug 25 08:33:51 pc-desktop kernel: [   31.684147] input: Power Button (FF) as /class/input/input7
Aug 25 08:33:51 pc-desktop kernel: [   31.684765] ACPI: Power Button (FF) [PWRF]
Aug 25 08:33:51 pc-desktop kernel: [   31.685143] input: Power Button (CM) as /class/input/input8
Aug 25 08:33:51 pc-desktop kernel: [   31.685705] ACPI: Power Button (CM) [PWRB]

I wonder that its wrong mode Vesa where ubuntu is booting (progress bar on the start screen of ubuntu) because it's maybe in mode 1024x768 - who anybody know? If yes, is that file configuration for it: /etc/usplash.conf?

Below config xorg.conf:


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbLayout"	"pl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
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
	Identifier	"nVidia Corporation NV25 [GeForce4 Ti 4200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option  "AddARGBVisuals"		"True"
	Option	"AddARGBGLXVisuals"	"True"
	#Option	"RandRRotation"	"True"
	Option	"NoLogo"	"True"
	Option	"NvAGP"	"1"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV25 [GeForce4 Ti 4200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


Additional info:
Graphics card: GF4 Ti4200
version Ubuntu: 7.04 + updated all now

I tried find in web archive but I didn't find about the similarly problem as me... Who anybody can help me? Where can I find solution?

PS. Its my first post here, and hello for all.


Best regards, PaulEU

---

