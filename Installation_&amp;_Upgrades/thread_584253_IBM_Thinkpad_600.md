---
title: "IBM Thinkpad 600"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by steve.ewing on 2007-10-20
I've installed Xubuntu on an old IBM Thinkpad 600 and during the boot process get the following error :

loading hardward drives [1521.704343] IBM Thinkpad detected, may corrupt serial eeprom, refusing to load module

The OS loads and my graphics is very low resolution, my wireless card is not detected.  Where do I start in resolving these problems?

Steve

---

### Post by Pumalite on 2007-10-20
At the basics: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Try Xubuntu Alternate CD
Burn at 4x
Do md5sum on iso before burn
Check for corruption of CD before install

---

### Post by steve.ewing on 2007-10-21
This helped but I still have a low resolution video.  Do I need to find a video driver for this laptop? or is there something else I should consider.

Steve

---

### Post by Pumalite on 2007-10-21
Memory?. Graphics?.

---

### Post by bliffle on 2007-10-21
I also have a TP600 that I plan to convert to ubuntu or xubuntu in a few days. So I'm very interested.

So far I've deployed 7.10 to a TP570, T40 and T60 with few problems.

I'll keep an eye open on this thread, but it will be a few days before I have anything to report.

The only real problems I've had so far are with bad CD's which were either the result of bad downloads or bad burns.

---

### Post by Pumalite on 2007-10-21
600  	P233 MMX
P2 233
P2 266 	32(160)
SDRAM SODIMM 	12.1" TFT 800x600
13.3" TFT 1024x768
13.0" HPA 1024x768 	NeoMagic MagicGraph 128XD (NM2160) 	Cirrus Logic CS4237 	  	3.2
4.0 	Int
Ext 	  	IRDA
USB 	  	600

Not good.
Xubuntu Alternate CD, I think.

---

### Post by steve.ewing on 2007-10-21
The laptop has:

P2 266 Mhz
13.3" TFT 1024x768
NeoMagic MagicGraph128ZV/ZV+/XD Driver
294 KB Memory

Graphics are fine when the using Win2000, but the highest resolution is 800x600, large icons, and large fonts with the Alternate CD install.

Steve

---

### Post by gordon ottershaw on 2007-10-29
The ubuntu installation defaults to 24 bit color.

The Thinkpad 600, 600E, and 600X can display UP TO  800x600 at 24bits.

Edit the video configuration file (sorry I can't remember the file name) to use 16 bit color.

EDIT: sudo gedit /etc/X11/xorg.conf

Find this section:

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 8500 (R200 QL)"
Monitor "KDS VS-190is"
DefaultDepth 24  

Change:    DefaultDepth 24
To read:    DefaultDepth 16

This will allow the use of screen resolutions up to 1024x768.  

I've never used 8 bit color, but it should allow even higher screen resolutions.

Hope this helps.

gordon

---

### Post by strikeback03 on 2007-11-03
my old 600E with the 13" screen could run native resolution (1024x768 ) at Windows highest color setting (which they call 32bit, though I don't remember if they fudge that number or not)

---

### Post by SixedUp on 2007-11-03
Gordon has the right answer. I have Ubuntu running on a 600X and Kubuntu on an original 600. In both cases the graphics adaptor cannot run at full resolution on the LCD at 24bit. However, both laptops *are* capable of 24bit colour at a lower resolution. Linux decided to go for more colours, rather than more resolution. 

You just need to alter your /etc/X11/xorg.conf as outlined in Gordons post, and you'll solve the resolution issue. I may be wrong, but I dont think the 600 series Thinkpads could do more than 1024x768x16 even with an external monitor, so I dont think there is anything to be gained by trying even lower colour depths.

The "Loading hardward drives [1521.704343] IBM Thinkpad detected, may corrupt serial eeprom, refusing to load module" message in your kern.log/dmesg is not an error, its an information message to let you know that Linux detected that a driver you might want to load on some hardware, is incompatible with your Thinkpad 600, and could cause damage. Consequently that driver was NOT loaded. Just ignore it.

Re the wireless card, we'd need to know more about the card before we can help you. What card is it?

---

