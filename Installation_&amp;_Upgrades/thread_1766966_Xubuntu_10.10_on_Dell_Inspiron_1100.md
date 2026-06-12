---
title: "Xubuntu 10.10 on Dell Inspiron 1100"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by regnier on 2011-05-25
Hello,
I recently migrated from ubuntu 10.10 to xubuntu 10.10 on my Dell inspiron 1100. After many tries I "succeed" (with internet) in solving partially the issue related to the video chipset (Intel® 82845G Graphics) by using a "vesa" driver in the xorg.conf. Some discussion here mentioned the possibility of deleting ASCI 8086:2562 from a blacklist in usr/bin/compiz but even with ghex editor I could not find any matching string. Hereafter my grub and xorg.conf for those who are interested.
I have another issue now. How can I create an iso file of my installed xubuntu. I did download ubuntu 10.10 and created a CD but I migrated after to xubuntu (since most of the files were there) and it would be great to burn a CD of xubuntu.
regards,
JL

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset nosplash nolapic"

#GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which you”quiet splash acpi=off”r graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start

#GRUB_INIT_TUNE="480 440 1"

##############################################################################

Section "Module"
Load "dri"
Load "glx"
EndSection


Section "Device"
	Identifier	"Intel 82845G/GL"
	Driver		"vesa"
#	Driver 		"intel"
#       Driver 		"i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Internal monitor"
	Option "DPMS"
	HorizSync 28-80
	VertRefresh 43-60
EndSection

Section "Monitor"
	Identifier "External monitor"
	Option "DPMS"
	HorizSync 28-80
	VertRefresh 43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
        Device "Intel 82845G/GL"
	Monitor "Internal monitor"
	DefaultDepth 24
	SubSection "Display"
	Depth 16
	Modes "1024x768" "800x600" "640x480"
	EndSubsection
	SubSection "Display"
	Depth 24
	Modes "1024x768" "800x600" "640x480"
	EndSubsection
	Option "AddARGBGLXVisuals" "True"
	Option "DisableGLXRootClipping" "True"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

Section "DRI"
Mode 0666
EndSection
```

---

### Post by mörgæs on 2011-05-25
You can get the Xubuntu ISO here:
[http://www.xubuntu.org/news/10.10-release](http://www.xubuntu.org/news/10.10-release)

---

### Post by regnier on 2011-05-25
Thanks,
actually I did download many things this month and my internet provider is charging me additional fees if I exceed 4GO...never mind I was just wondering whether or not it was possible to create this CD from the installed OS.
Regards

---

### Post by mörgæs on 2011-05-25
Yes, you could try Remastersys.

---

### Post by regnier on 2011-05-25
thanks ! I will try

---

