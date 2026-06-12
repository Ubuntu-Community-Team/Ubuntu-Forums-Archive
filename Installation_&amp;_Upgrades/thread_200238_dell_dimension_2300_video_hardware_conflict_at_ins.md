---
title: "dell dimension 2300 video hardware conflict at install"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by prozaconstilts on 2006-06-20
I am attempting to install Ubuntu on a Dell dimension 2300 that has integrated intel i830 video, and with an ATI All-in-Wonder VE via PCI. The LiveCD hangs at "Installing Hardware drivers" in boot-up for both regular install and with safe video. I figured that having 2 different video cards is probably the cause, but a scour of the internet showed no definate way to disable integrated video through the BIOS. Any suggestions?

---

### Post by SpacePony on 2006-06-20
Easiet way I could imagine would be to pull out the PCI card and install Ubuntu, then when things are working plug the PCI card back in and try getting xorg to use the PCI for graphics instead of the onboard video.

There's a section in the xorg.conf file that can be altered to tell xorg which graphics device to use. Mine looks like this:

[I]Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Screen		0
	BusID		"PCI:3:0:0"
	Option		"NoLogo"
EndSection[/I]

The line in question is the BusID one. The value can be gotten from typing 'lspci' in a console window.

If I glossed over too much let me know and I can elaborate.

---

### Post by prozaconstilts on 2006-06-25
So...hit a bit of a snag on this. After removing the PCI card, and successfully installing Ubuntu, I shut down the system, re-inserted the PCI card, and rebooted...only to find video coming through the PCI card, and hardware driver load hanginig like before. So I removed the PCI card, and rebooted..only to find the system STILL hanging...even though there was only one video device present...i guess I'll need to re-install from scratch.

So at this point, I have no way of figuring out what the PCI bus of the expansion card is, or how to tell Ubuntu to ignore loading drivers for a specific piece of hardware...any suggestions?

---

### Post by Beck on 2006-06-27
I have the same problem with my Dimension 2350 and my PCI Radeon 9100 graphics card ;(.

---

### Post by khdx on 2006-06-27
I have the same with my Dimension 2350 and FX5200.  I got ubuntu running with onboard, now trying to figure out how to get FX5200 working.  If I find out how I will help you out.

Kevin

---

### Post by prozaconstilts on 2006-07-05
*sigh* So I remembered that I can blacklist modules. So, I hopped into my /etc/modprobe.d/blacklist file and added the line:

blacklist i810

and rebooted w/o the ati card. My xorg server failed to start, which indicated to me that I had blacklisted the proper module.

So I then installed the ati card and turned on the system...and it still hung at loading hardware drivers. So I pulled the card, then un-blacklisted the i810 module...only to find X not coming up at reboot. I think I just may have broken it a bit more :(

Any other suggestions about how to go about getting my ati card recognized?

---

