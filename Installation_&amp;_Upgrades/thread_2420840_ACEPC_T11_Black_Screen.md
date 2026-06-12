---
title: "ACEPC T11 Black Screen"
date: 2019-06-11
forum: Installation &amp; Upgrades
---

### Post by texaswheelock on 2019-06-11
I have an ACEPC T11 that came with Windows 10 pro. I installed latest release of Ubuntu and now only get a black screen. The installation was successful but shortly after the picture went black. I have tried to get to boot menu with no luck. 

Any ideas how I can correct or reset the box?

Thanks

---

### Post by Bashing-om on 2019-06-11
texaswheelock; Welp !

A bit more info please.

As Win10 requires installation in EFI mode - and IF ubuntu is installed also on the same drive, then ubuntu must also be installed in EFI mode.

So, describe the ubuntu install process that you employed.
As well, what is the hardware ? Nvidia graphics? optimus/hybrid graphics at play here ?

When we know more
[INDENT][INDENT]we can tell more
[/INDENT][/INDENT]

---

### Post by texaswheelock on 2019-06-12
@Bashing-om
Thanks for your response. I am a bit new to this, sorry if that affects my lack of knowledge/info. 

You are probable on to something with EFI mode. Windows 10 was installed on the drive. I booted from a USB with the full Ubuntu installer on it. I did the full install that included formatting the drive. [COLOR=#1D2228][FONT=&quot]When I plug the device in the blue light long blinks then goes off. I can press the power button and see a brief red light then long blue but nothing on the monitor display. 

Device Specs for ACEPC T11 are[/FONT][/COLOR][COLOR=#454545][FONT=&quot]CPU:Intel Z8350[/FONT][/COLOR][COLOR=#454545][FONT=&quot]GPU:Intel HD Graphics
RAM:4GB DDR3L
ROM:32GB eMMC
WiFi:Dual Band&#65292;2.4G/5G
LAN:10/100M
Bluetooth: Version 4.0[/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][B]Interface: 
USB port:1xUSB 3.0;3xUSB 2.0;1xMicro USB for OTG
Card reader: TF Card &#65288;up to 128GB&#65289;
HDMI Port :HDMI 2.0
Microphone audio: 3.5mm Microphone jack x1
VGA Port:VGA 1920*1080[/B][/FONT][/COLOR]
[COLOR=#454545][FONT=&quot][B][B]More Support: 
Video format Support: HD MPEG1/2/4, HD AVC/VC-1,RM/RMVB,Xvid/DivX3/4/5/6 , RealVideo8/9/10, etc.
Audio format Support: MP3,WMA,AAC,WAV,OGG,AC3,DDP,TrueHD,DTS,DTS,HD,FLACAP
Photo format Support: JPEG/BMP/GIF/PNG/TIFF,etc.
Mouse/ Keyboard: Support mouse and keyboard via USB;Support 2.4GHz wireless mouse and keyboard via 2.4GHz USB dongle[/B][/B][/FONT][/COLOR]

---

### Post by Bashing-om on 2019-06-12
texaswheelock; Hey -

Not to know is not a sin - we were all new at one time, We all start at the same place. This is a process in learning ( for all of us).

> 
When I plug the device in the blue light long blinks then goes off. 

Let us establish a sound foundation from which to work.
We need to know that the ,ISO download is sound and that the copy to USB is good:
verify:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
[https://help.ubuntu.com/18.04/installation-guide/](https://help.ubuntu.com/18.04/installation-guide/)

Once we are sure of the installer, we can move forward to the booting process.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by texaswheelock on 2019-06-17
I want to apologize for my lack of response lately. Not going to lie some of the job aides are intimidating. I took the easy way out and returned the box to Amazon and got a replacement one. 

That said I need/ want to install Ubuntu on the new box without breaking it. Any walkthroughs or job aides that i should review to ensure I am not in the same boat as before?

---

### Post by jglen4902 on 2019-06-17
The specs from an online source for the ACEPC T11 shows that for storage there is an eMMC of 32GB.  With Windows 10 installed, there's not going to be much free space left for Linux.  Now, that same spec also indicates that an additional drive can be connected via SATA, so do you have an additional drive attached that can be used for the Ubuntu installation?

---

### Post by texaswheelock on 2019-06-18
That is a really good idea and yes I have a few to try. Right now I am wiping an old 500GB I pulled out of a Macbook Pro. So my thought was to use the secondary hard-drive for Ubuntu and keep Windows where it is. Then use the boot menu to get into the Linux drive. Is that what you were thinking? 

Thanks

> **jglen4902 said:**
> The specs from an online source for the ACEPC T11 shows that for storage there is an eMMC of 32GB.  With Windows 10 installed, there's not going to be much free space left for Linux.  Now, that same spec also indicates that an additional drive can be connected via SATA, so do you have an additional drive attached that can be used for the Ubuntu installation?

---

