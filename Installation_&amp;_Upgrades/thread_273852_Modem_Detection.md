---
title: "Modem Detection"
date: 2006-10-08
forum: Installation &amp; Upgrades
---

### Post by tsheller on 2006-10-08
Complete novice in Linux, but Im one of the many, it seems, softmodem people who need it! 

I have used the scanModem script, and I have a fairly good idea of what I got as far as chipsets go, but following the directions just isnt working for me.

PCIDEV=8086:24c6
CLASS="Class 0703: 8086:24c6"
NAME="Modem: Intel Corporation 82801DB/DBL/DBM "
Vendor=8086
Device=24c6
SUBSYS=14e4:4d64
SUBNAME=" Broadcom Corporation: Unknown device 4d64"
SUBven=14e4
IRQ=7
Test="./scanModem test 8086:24c6 14e4:4d64"
SOFT=8086:24c6
CODECd=BCM64
COD=BCM
TYPE=ALSA
SLMODEMD_DEVICE=modem:1
PORT="modem:1"
Driver=snd-intel8x0m
DRIVER_=snd_intel8x0m
KDRIVER=SND_NTEL8X0M
MPLACE=
ASOUND=1
CODECp=BCM64
CODEC=
COD=BCM
HDA=
IDENT=slmodemd
TST=


I am running the newest, most up to date stuff (2.6.15-27-386) but installing the slmodem and everything still doesnt let me detect my modem. Every once in a while, after I do some work and run the modprobe snd_intel8x0m I get a little alert saying I have a new sound device, but thats it.

Also, from what I understand, Its disabling my modem -because- I dont have drivers installed, is that right? If not I guess the first step would be getting it enabled, but thats not worked out very well either.

Any ideas from the pro's?

---

### Post by Zerksis on 2006-10-09
The 82801DB is an I/O Controller Hub not the modem. 

see; [http://www.intel.com/design/chipsets/datashts/290744.htm](http://www.intel.com/design/chipsets/datashts/290744.htm)

If you need a fast response and are using a USB modem, it may help to add USB  in the post.

Cannot help with USB modem - BTW is it broadband or dial-up?

---

### Post by tsheller on 2006-10-09
from my understanding, I have a softmodem. I looked up my US robotics USB modem that I -also- have, and it was listed as incompatible. The one I have is built into the laptop, which is a Dell Inspiron 8600. I have tried the slmodem drivers and even went through some of the guides on [www.linmodem.org](www.linmodem.org), but there are sooo many options and asides to consider, I just dont think I am doing the whole process right from beginning to end. Its dial-up, yes

---

### Post by Zerksis on 2006-10-10
Hi,

Analog Dial-up modems are a pain in Linux.  
Especially so in Ubuntu, their dial-up modem support is awful.

However, don't give up - try putting this into Google ***+"Dell Inspiron 8600" +"Linux" +"modem"***
and you will find at least 10 pages of people who have Linux & dial-up working on the 8600. 
With some research you should be able to crack it :)

I assume you have access to the internet somewhere / somehow.

You can get an Intel 536EP PCI modem to work OK and many distros support this device out-of-the-box.
If you were a KDE desktop fan - then Simply Mepis 6.0 (which is built on Ubuntu) finds and configures it without 
any problem.  Why Ubuntu cannot do this also mystifies me.
If you do want a low cost PCI modem (not for the laptop) then check out this link;-

[http://www.ubuntuforums.org/showthread.php?t=62394](http://www.ubuntuforums.org/showthread.php?t=62394)

Hope the above helps a bit.

Z

---

### Post by tsheller on 2006-10-10
Yeah. I can actually come outside .. way outside my yard and pick up a nearby wireless. Hurray for open wireless networks. Unfortunately this limits me to about 2-3 hours of battery power searching for solutions, lol. After that I could charge it back up, but my frustration is usually beyond me doing anything productive, bleh. 

As for the dell pages, thanks for the heads up. Unfortunatly I just am -not- doing something right. One suggests to use the module-assistant after cleaning and extracting the files, which works fine (as in, I complete the steps and it gives me pats on the back), but doesnt do anything. A few of the others dont even use the same modem as I have, either. Others have used a modprobe snd_intel8x0m or other, and I havent have any success either. 

I mean, it stands to reason that there would be specific instructions for this somewhere! Step A through Z, I just cant find it. You would think with all the Inspiron 8600's out there, or at least all the mobo's running the chipset, I could find the solution, but alas. I hate to think it, but is there another distrobution more friendly to modem chipsets?

I should note.. that this is a laptop. Im I dont think I can even use a PCI modem like you suggested, unless I am misunderstanding something.

---

### Post by Zerksis on 2006-10-11
*[COLOR="SeaGreen"]I dont think I can even use a PCI modem like you suggested, unless I am misunderstanding something.[/COLOR]*

PCI cards don't go with laptops - but I thought you may have another desktop machine.

My first install of a modem was just like your experience, but it will work - and you will feel great for cracking the problem.

You might try this forum with;-

*[COLOR="Sienna"]Can't get Dell Inspiron 8600 modem to work[/COLOR]*

at least it is specific and might attract another Ubuntu/Dell8600 user.

Good luck Z

---

### Post by _duncan_ on 2006-10-11
Hi. I was able to get on-line by following this guide:

[How to Conexant and Smartlink Modems]("http://www.ubuntuforums.org/showthread.php?t=190728")

It worked for my PCI smartlink modem, not sure if it will work for your USB smartlink modem though.

---

