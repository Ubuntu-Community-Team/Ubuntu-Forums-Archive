---
title: "trying to live cd"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by allenb.bigal on 2012-02-01
Hi 
I have a new notebook and I'm trying to use the live cd of 11.10 to see how it works on this machine. I'm getting nowhere because all sorts of gunk comes up on the screen and it never gets to the point where it asks if I want to install or just look. I suspect it's something to do with the graphics but I can't be sure of that as I don't have a log of what's happened. Here's the specs of the notebook:-

Medion Akoya Specifications:
Display
Screen resolution			1600x900
Screen size				17.3in
Display technology			LED-backlit LCD

General
Colour					Black, Grey

Graphics card
Graphics card				NVIDIA GeForce GT 555M
Graphics memory				1GB
Discrete graphics card?			Yes
Secondary graphics card?		Yes

Memory
RAM					8GB

Optical drive
Optical media supported			CD, DVD
DVD drive type				Read and write

Power
Battery type				Rechargeable
Removable battery			Yes
Power supply				AC, Battery
Battery life (as tested)		191min

Processor
CPU type				Intel Core i5
Processor speed				2.4GHz
Processor type				Intel Core i5-2430M

Size and weight
Weight					3.3kg
Height					40mm
Width					420mm
Depth					280mm

Software
Operating system			Windows 7 (64-bit),     Windows 7 Home Premium

Storage
Drive speed				5400rpm
Hard drive interface			SATA
Hard drive type				Hard drive
Internal storage			1TB
Supported memory media			SD

Warranty
Warranty length (months)		24

Wired connections
Number of USB 2.0 ports			4
Number of USB 3.0 ports:		2
Wired Terminals / Ports			3.5mm headphone jack, Gigabit Ethernet, HDMI, 								Microphone, USB 2.0, USB 3.0, VGA (D-sub)

Wireless connections
Bluetooth				Yes
Wi-Fi (wireless networking)		Yes
Wireless technology supported		Bluetooth, Wireless 802.11b, Wireless 802.11g, 									Wireless 802.11n

I know that the CD is OK as I've used it on an older PC.

Is there any way I can load the install disc and get a log so that I can see what is causing the problem?
Thanks in advance.

Allen
Oz

---

### Post by mastablasta on 2012-02-02
this seems to be one of those windows only laptops :-)
 
linux does not support graphics switching (manufacturers do not want to support it). However some projects were initiated by community (BUMBLEBEE, IRONHIDE..). GPU could be at fault as well as if this notebook doesn't use BIOS to boot.

---

### Post by allenb.bigal on 2012-02-02
Would it help if I blew the lot of W7 away, did a deep format of the HD and tried again to load U11.10 on a clean machine?
I don't want to do that because I want to keep W7 but I could probably work out a way where I can recover my W7 if I don't succeed.
Allen
Oz

---

### Post by mastablasta on 2012-02-02
no it wouldn't because there are no drivers for switchable grpahics in linux (unless you can find osmehitng in mentioned projects).
 
hmm also it oculd be a bad burn or download. have you checked the md5sum of downloaded image? can you try to install the iso on USB rather than CD?
 
You can use unetbootin for that or linuxliveUSB

---

### Post by allenb.bigal on 2012-02-02
I haven't worried about checking the live cd because I have tried it in another computer and it worked. I have also had the same problem with 11.04, 8.04 and 10.something and they all did the same. They worked in the other computer but I got the error result whenever I tried any of them in the notebook.

---

### Post by mastablasta on 2012-02-03
> **allenb.bigal said:**
> I haven't worried about checking the live cd because I have tried it in another computer and it worked. I have also had the same problem with 11.04, 8.04 and 10.something and they all did the same. They worked in the other computer but I got the error result whenever I tried any of them in the notebook.
 
 
"the other computer" has a different hardware configuraiton (the kind that is linux compatible) i presume.

---

