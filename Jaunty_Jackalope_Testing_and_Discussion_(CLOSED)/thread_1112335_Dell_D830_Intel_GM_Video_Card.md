---
title: "Dell D830 Intel GM Video Card"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by u.2 on 2009-03-31
Hi,
Ubuntu 9.x.x seemed to fix alot of my issues, and now my remaining is my video card.  I am OK but the laptop resolution is only at 1024x768 and using dual monitors also isn't working.

How can I fix this?  I fan lspci and go this.

 lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by ivanvajar on 2009-03-31
Intel VGAs are troublemakers. I solved it on my friend's computer by installing SuperUbuntu. It's Interpid Ibex based.

---

### Post by ivanvajar on 2009-03-31
Did you try:
> sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

---

### Post by u.2 on 2009-04-09
Hi,
I have searched everywhere and can't find the answer or how to solve my issue.  I have a Dell laptop with an intel integrated video card GM965 chipset.

I can't get the resolution on my laptop to work right - no option to set it to the higher resolution needed.  I then can't get my external monitor to work either.  I can use it but can't use the dual displays and the external monitor doesn't have the option for the right resolution either.

My laptop is a Dell D830 and I should be able to set the resolution up to at least the 1440 and the 1600 is the one that it should go to.

The external should go to the 1440 as well and I have no options.

I have tried xrandr command, grandr, and have updated the system daily.  I tried Ubuntu 8 before going to 9.04 and it was worse with hardware issues.  This is my last problem but i can't work because I can't connect to remote systems using vnc or remote desktop as my screen locks up, etc.

This was much worse on Ubuntu 8.x but still a problem.
I have googled everywhere and tried a ton!

---

### Post by u.2 on 2009-04-10
Yes, I tried the updates and I am on 9.0.4.  Things were alot worse on version 8.  

I have tried xrandr, and a bunch of things.  Now back to a new install and just hoping to find the answer.  I have searched google from top to bottom, no clear instructions yet.

I don't have the resolution to choose on my laptop and on my external monitor that resolution is also to low, and no option for extended desktop. 
I ran "lspci" and it shows the intel video adapter.

---

### Post by overdrank on 2009-04-10
Threads merged and moved to Jaunty Jackalope Testing and Discussion

---

### Post by u.2 on 2009-04-10
Thanks for moving this thread.  My basic problem is on a Dell D830 and I have an intel integrated video card.

I have tried xrandr/grandr and tried but failed to add new modes, but also I am confused about the xorg.conf file and if that is needed.  One article I read stated that xorg.conf wasn't used any longer?

I have google'd, searched, read, and tried a ton of stuff, I am sure I am just not doing something right.

How can I get resolutions to show up that aren't available in my list for my laptop?  I know the default should be something around the 1600 or 1440 area.

Then I have an external monitor and want to do dual displays, but right now I can't even get my external monitor to go to the right resolution.

The external monitor is a ViewSonic VA1912wb.

The lspci output is:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

The xorg.conf file is:
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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

---

### Post by u.2 on 2009-04-12
Anyone?

---

### Post by Favux on 2009-04-12
Hi u.2,

It sounds like you've tried a lot so I hesitate to suggest anything.  Have you tried adding "Intel" to video device.  See post #8 here:  [http://ubuntuforums.org/showthread.php?t=1108732](http://ubuntuforums.org/showthread.php?t=1108732)

---

### Post by dro0g on 2009-04-12
Hi,

I have a D630 and the same Intel video card. It's running at 1440x900 and I'm able to use two external monitors on a docking station. I have not installed from scratch since probably 7.10 so I'm not sure of the specifics of what need to be configured. 

There's nothing special in the xorg.conf save for turning on UXA and a "virtual 2720 1924" under "screen" which is the resolution for both external monitors. have you tried a dpkg-reconfigure xserver-xorg?

if you run xrandr with no options what does it list for available resolutions?

---

### Post by u.2 on 2009-04-13
thx, when I ran xrandr I got the output below, but not even the 1280x1024 is showing up to choose when I go to "Display" from the system menu.  

The xorg.conf file is also below, is it something in there I am missing?

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
1280x800 60.0*+
1024x768 85.0 75.0 70.1 60.0
832x624 74.6
800x600 85.1 72.2 75.0 60.3 56.2
640x480 85.0 72.8 75.0 59.9
720x400 85.0
640x400 85.1
640x350 85.1

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device

---

