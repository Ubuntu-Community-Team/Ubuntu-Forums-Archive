---
title: "HP tx1000 Install trouble"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Papeep on 2007-04-15
--------------------------------------------------------------------------------

Hi, I'm having trouble installing on a tx1000 (beautiful laptop by the way, very nice! :D ). I've installed edgy several times on different machines, so I'd say I have a bit of experience.  

I can get the LiveCD working just fine (6.10 i386, 7.04 i386 and 7.04 AMD64) and it says it installs, but I can never boot from the hard disk, it allways gets past the loading bar and then just hangs on a black screen. It's a shame; I still love the laptop though!

-Papeep

---

### Post by bugler on 2007-04-16
Try using -noapic, acpi=off or pci=noacpi (1 at a time) for a boot parameter.  You may have to go into /etc/grub/menu.lst and edit the item that is your partition for that ubuntu install and append to end of the line 1 or all of the boot parameters.  

Let us know how it fairs.

Bugler

---

### Post by ennalax on 2007-05-06
i'm currently running feisty (amd64 version) on a [tx1120us]("http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=RV308UA%23ABA&tab=detailed_specs&storeName=storefronts&landing=rts_notebooks&category=rts_notebooks&subcat1=retail&catLevel=3#defaultAnchor") and to install i used 'doscsi noapic nopcmcia' as options.  the installation process should go smoothly even without the pcmcia module disabled, but it you should than make sure the expresscard slot is left completely empty.  needless to say, make sure you add these options (and any other ones you choose during the installation in your your bootloader's setup - normally /boot/grub/menu.lst)

note that feisty will not install the sound drivers correctly, but it nevertheless successfully installs and configures the touchscreen.

---

### Post by farbird on 2007-05-07
u sure the touchscreen is configured well??

i have a similar model hp tx1005au [ asian model ] and the touchscreen works in a super uncalibrated way and feisty doesnt have any calibration app built in

---

### Post by cjoey19 on 2007-05-08
i have the tx1005 also.... really really nice!! really excited to get my hands on it...


anyway, back to topic, i cant even get the live cd to boot, it boots and show me some error message and then a weird screen, i've used the cd on my desktop n it works perfectly, so can anyone tell me whats wrong?

---

### Post by farbird on 2007-05-08
something to do with vesa/framebuffer..

the livecd comes with a prebuilt kernel with lots of compatibility as gfx card drivers are built as modules..

apparently, some of the module drivers conflict each other..

i suppose its the riva tnt and nvidia module.. both with framebuffer built in..

even with an install on a hdd using this laptop, u need to edit the menu.lst in /boot/grub/ to add in 
vga=0x317 to get the thing working..

the line should be the line that has the word "splash" on it..

remove the word splash and add the above vga=0x317 in it..

sadly, i had given up trying linux on this laptop...
stuck on vista until drivers are available for this piece of junk.

search my posts, u may find some light to find your tx1005 working [ at least some of it works ]

touchscreen doesnt work [ cannot calibrate , super off calibration ]
broadcom wifi needs tweaking and firmware drivers to work..
alsa completely sucks on this machine... took me days to get it working without headphone jack working

the 3 things above is enuff to turn anyone away from trying to get anyone to try linux on this tx1005 junk..

i cant understand how can HP embrace opensource so openly and refuse to create any drivers support on their laptops/desktops..

pity

> **cjoey19 said:**
> i have the tx1005 also.... really really nice!! really excited to get my hands on it...


anyway, back to topic, i cant even get the live cd to boot, it boots and show me some error message and then a weird screen, i've used the cd on my desktop n it works perfectly, so can anyone tell me whats wrong?

---

### Post by ennalax on 2007-05-09
> **farbird said:**
> u sure the touchscreen is configured well??


the screen calibration seems to be completely random upon install.  i tried installing several different distros, feisty x86_64 three times among those.  out of those three times the last two times the screen was calibrated perfectly.

as for booting problems, i fixed them by:
  1. making sure the scsi disk is accessible w/o apic 'doscsi noapic'
  2. either removing the remote from the expresscard or disabling the pcmcia driver ('nopcmcia'). 

as for screen issues when booting, i never had them.  

still not functional:
  1. wireless card;
  2. realtek HD audio (which also controls the headphone jacks)
  3. nvidia does not control beryl properly

---

### Post by farbird on 2007-05-09
for the wireless to work

try this

sudo apt-get install bcm43xx*

sudo gedit /etc/iftab

change your eth0 or eth1 whichever which should be the wireless card to wlan0 instead

sudo gedit /etc/network/interfaces

remove any lines which refer to the eth0 or eth1 which u replaced with wlan0 in the iftab file.

reboot and it should be working
use knetworkmanager to check..

for realtek hd audio,

try this

sudo rmmod snd-hda-intel -w
make sure u quit your kmix before doing this

sudo modprobe snd-hda-intel model=3stack

this should get the speakers to work, but headphone jack will not work.
no jack sense either.
mute light doesnt work also..

there's the new kernel 2.6.21.1 which may be able to support the realtek 660 but i havent yet have the time to try
it uses the command
model=stack-660 to work.. ie append to the modprobe line.
but they changed some variables...
ie no more "snd" prefix to standardize the alsa kernel module..

> **ennalax said:**
> the screen calibration seems to be completely random upon install.  i tried installing several different distros, feisty x86_64 three times among those.  out of those three times the last two times the screen was calibrated perfectly.

as for booting problems, i fixed them by:
  1. making sure the scsi disk is accessible w/o apic 'doscsi noapic'
  2. either removing the remote from the expresscard or disabling the pcmcia driver ('nopcmcia'). 

as for screen issues when booting, i never had them.  

still not functional:
  1. wireless card;
  2. realtek HD audio (which also controls the headphone jacks)
  3. nvidia does not control beryl properly

---

### Post by diatribex on 2007-05-09
It is good to hear that at least someone has been able to get the touchscreen working...

I have  tx1000 class book as well ( tx1120us).  Does anyone know how the calibration is done on the install?  I have been trying for days to get it working.  Without use of the pen, I might have to go back to vista...


Also, my machine seems prone to random booting problems.  Sometime it will just refuse to boot fully.  I think it has to do with ACPI.  Has anyone else seen this in the wild?

As well Beryl work s great, but compiz seems to have an issue with drawing windows.  The corners and the main pane get drawn but the top and sides are missing.

Any help would be great :)

Jordan

---

### Post by farbird on 2007-05-09
yes..

mine also does the erratic booting sometimes stuck at the hp boot logo..
gotta do a ctrl-alt-del before it can work again.

same with vista even.


i maybe will be trying out feisty 64bit...

> **diatribex said:**
> It is good to hear that at least someone has been able to get the touchscreen working...

I have  tx1000 class book as well ( tx1120us).  Does anyone knomaybe w how the calibration is done on the install?  I have been trying for days to get it working.  Without use of the pen, I might have to go back to vista...


Also, my machine seems prone to random booting problems.  Sometime it will just refuse to boot fully.  I think it has to do with ACPI.  Has anyone else seen 
this in the wild?

As well Beryl work s great, but compiz seems to have an issue with drawing windows.  The corners and the main pane get drawn but the top and sides are missing.

Any help would be great :)

Jordan

---

### Post by diatribex on 2007-05-09
I think the hangs might be due to a buggy bios...something with the interrupts.

Hopefully between the groups of us, we can get this thing popping.

I cant see the fingerprint scanner listed on the bus though :(

Jordan

---

### Post by farbird on 2007-05-09
probably irq sharing method not recognisable by ubuntu...

fingerprint device is listed in the device list, i think..
check under usb devices..

apt-get install usbview or usbman...

hehhe
cant remember which one..

---

### Post by ovalenzu on 2007-05-30
hi i have a tx1000 laptop (tx1110us) for instalation i have some many problems
finaly with noapic option y complete the instalation

beryl for me works fine i install de drivers from nvidia site
just install build-essential before install nvidia drivers 

for beryl work i edit xorg.conf 

the wireless with de bcm43xx module works but very slow but you can use in monitor mode
just install bcm43xx-fwcutter for get the firmware

for more speed with ndiswrapper works very good but not have monitor mode :P

the sound for  mi sucks!! i try and try and try diferent ways but no one works for me 
now i have sound with OSS 4.0 for manage sonuds  lowvolume,  raisevolume and mute with multimedia keys i made some scricpts for that and with xbindkeys  now i can raise a low de volume with multimedia keys, but i want alsa if someone could explain me how i can get work thanks very much

---

### Post by netvampire on 2007-05-30
I have the HP TX1120US laptop. I love it to death.

I am at the intermediate level with linux, and was successful in getting KUBUNTU loaded. I also succesfully managed to configure my wireless network adapter.

To successfully load the os, i used the boot parameters as specified in the thread. To configure the wireless lan drivers I followed the guide located at [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092). It worked flawlessly, just follow it to the T.

The Touch screen does not work and I have no idea how to configure it. I have yet to test the sound.

Good luck everyone.

---

### Post by sayamindu on 2007-05-31
I am considering buying one of these laptops (my primary OS would definitely be Ubuntu). Could someone please copy-paste the output of the commands lspci and lspci -n please ? Also, does suspend to disk/ram work ?

---

### Post by manu456 on 2007-06-01
Here is the output of the commands that you had requested

lspci

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

```

lspci -n 

```
00:00.0 0500: 10de:02f0 (rev a2)
00:00.1 0500: 10de:02fa (rev a2)
00:00.2 0500: 10de:02fe (rev a2)
00:00.3 0500: 10de:02f8 (rev a2)
00:00.4 0500: 10de:02f9 (rev a2)
00:00.5 0500: 10de:02ff (rev a2)
00:00.6 0500: 10de:027f (rev a2)
00:00.7 0500: 10de:027e (rev a2)
00:02.0 0604: 10de:02fc (rev a1)
00:03.0 0604: 10de:02fd (rev a1)
00:05.0 0300: 10de:0244 (rev a2)
00:09.0 0500: 10de:0270 (rev a2)
00:0a.0 0601: 10de:0260 (rev a3)
00:0a.1 0c05: 10de:0264 (rev a3)
00:0a.3 0b40: 10de:0271 (rev a3)
00:0b.0 0c03: 10de:026d (rev a3)
00:0b.1 0c03: 10de:026e (rev a3)
00:0d.0 0101: 10de:0265 (rev f1)
00:0e.0 0101: 10de:0266 (rev f1)
00:10.0 0604: 10de:026f (rev a2)
00:10.1 0403: 10de:026c (rev a2)
00:14.0 0680: 10de:0269 (rev a3)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
03:00.0 0280: 14e4:4312 (rev 01)
```


Suspend does not work for me. The computer freezez after suspend.

---

### Post by creatureofthedark on 2007-06-21
i have the same laptop with the same problems but i cant even boot the live CD!! i am also a noob and have no idea what u gets just said! i have tried the kubuntu 64bit that installed but did not boot. can u give me a noob how to guide?? thx for your help

---

### Post by cjoey19 on 2007-06-22
hp tx1000 users are definitely desperate for a guide..... that includes me! i love ubuntu, beryl and everything!!! give us linux noobs a guide!

---

### Post by farbird on 2007-06-22
after email correspondence with the realtek techsupport, this was their final answer...

```

HP don't provide the machine here.
And I don't know the Hardware layout of your machine.
I can help you, but no more information that I can not modify the driver.
This machine only support vista, so HP was not lend it to us.
Do you know what I mean?

----- Original Message ----- 
From: "--------" <farbird@------.com>
To: <kailang@realtek.com.tw>
Sent: Wednesday, June 20, 2007 8:58 PM
Subject: Re: alc861-660 linux drivers


> HP told me that they are only committed to supporting vista related driver
> issue...
>
>
> I hope realtek can provide some support..
>
> else putting up linux drivers at your site is just going to make users
more
> frustrated when using them doesnt guarantee it to work with mainboards
with
> your audio chipsets..
>
>
>
> ----Original Message Follows----
> From: "Kailang" <kailang@realtek.com.tw>
> To: "-------" <farbird@----------.com>
> Subject: Re: alc861-660 linux drivers
> Date: Wed, 20 Jun 2007 14:52:53 +0800
>
> Sorry!!
> The codec.txt infomation shows that verb table is not clear.
> You could visit the vendor HP, because I don't have the hardware layout of
> your NB of audio parts.
>
```

---

### Post by Cuppa-Chino on 2007-07-03
> **farbird said:**
> yes..

mine also does the erratic booting sometimes stuck at the hp boot logo..
gotta do a ctrl-alt-del before it can work again.

same with vista even.


i maybe will be trying out feisty 64bit...

have you tried the new BIOS F13? does it help

---

### Post by kyrox on 2007-07-18
how to do you update the bios in linux? All I can find is windows apps for it.

---

### Post by farbird on 2007-07-18
only windows can update the bios..

hp doesnt release any linux bios updates

---

### Post by kyrox on 2007-07-19
ok .. so it is possible to load windows vista, without installing (from a CD for instance)?

---

### Post by Cuppa-Chino on 2007-07-20
> **kyrox said:**
> ok .. so it is possible to load windows vista, without installing (from a CD for instance)?

hmm not really easy but [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/) bart's pe cd exists.. not sure if it can do vista or if you can update bios from xp/2000 (but would not see why that would not work).. 

the BIOS is one of the reasons why I left a small Vista Partition alive...

---

### Post by rajivrajagopal on 2007-07-20
i am using hp tx1003au..i am not able to install ubuntu..error when i nstall.it is gtng stukd..it says some error bcm...xxxsomething..pls help me..

---

### Post by Cuppa-Chino on 2007-07-24
> **rajivrajagopal said:**
> i am using hp tx1003au..i am not able to install ubuntu..error when i nstall.it is gtng stukd..it says some error bcm...xxxsomething..pls help me..

are you using the graphical installation from the live cd or the alternate installer cd ?

you might want to try the alternate installer.. please give a couple more details on what screen you are getting stuck at

---

### Post by rajivrajagopal on 2007-08-01
ya..graphical..it stucks now when the display window starts..a blank screen.

---

### Post by matashman on 2007-08-03
I had the same issue, during the install goto options[F6] and at the end of the line type in noapic and continue with install.

---

### Post by zarshark on 2007-08-21
Hi people,

I've solved some common problems..


INSTALLING AND BOOTING:
To install and boot correctly the hp tx1000, remember the option noapic.


3D GRAPHIC:
To configure the GeForge 6500 Go (necessary to use beryl and 3d games and   apps):

First, you must search on google the software envy by alberto milone. It is a tool to auto configuring an nvidia or ati graphic card on ubuntu. Open it with the debian package software and accept. You must accept to satisfy all dependences.

Then, start envy and install nvidia driver (under root!). Envy will search and configure the best driver. Accept always default choices.

Then reboot! (or restart the gdm).

Go to Applications/System Tools/Nvidia Setting (always under root) and sets under X Server Display Configuration, millions of Colors. (Then reboot! (or restart the gdm). The nvidia logo will appear.

Now 3d games and apps will start correctly.
It is possible than beryl don't start yet. Don't worry! 

sudo gedit /etc/X11/xorg.conf  and put your pwd.

Then you must set enable to the composite option that you find to the end of file. 
Then reboot! (or restart the gdm). Now beryl start correctly.

WIRELESS
using synaptic search and install:
bcm43xx-fwcutter
ndiswrapper

SOUND CARD
I'm able to reproduce sound. I try so:

boot with recovery mode. (or in normal way, but closing the sound server).
enter as root.

rmmod snd-hda-intel -w
modprobe snd-hda-intel model=3stack

-- Then

startx

Note then the next boot there will be no sound. It is necessary to load the module snd-hda-intel during booting.
I must try again, but the way is right!

---

### Post by zarshark on 2007-08-21
About sound card!! some news:

To reproduce sound:

# manage the options of sound daemons.
sudo gedit /etc/modprobe.d/alsa-base

# add the line (to the end of file):
options snd-hda-intel model=3stack

Then reboot the system.

Note: 
now speakers plays correctly, but no sound in your headphones.

It depends on the choice of the model.
My tablet supports SPDIF, but no model designed for SPDIF works!
I tried also other models but nothing!
At least 3stack model works!

 




If anyone is interested to try, a list of models is the following one:

Module snd-hda-intel
  --------------------

    Module for Intel HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

    model	- force the model name
    position_fix - Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size)
    single_cmd  - Use single immediate commands to communicate with
		codecs (for debugging only)
    enable_msi	- Enable Message Signaled Interrupt (MSI) (default = off)

    This module supports one card and autoprobe.

    Each codec may have a model table for different configurations.
    If your machine isn't listed there, the default (usually minimal)
    configuration is set up.  You can pass "model=<name>" option to
    specify a certain model in such a case.  There are different
    models depending on the codec chip.

	  Model name	Description
	  ----------    -----------
	ALC880
	  3stack	3-jack in back and a headphone out
	  3stack-digout	3-jack in back, a HP out and a SPDIF out
	  5stack	5-jack in back, 2-jack in front
	  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
	  6stack	6-jack in back, 2-jack in front
	  6stack-digout	6-jack with a SPDIF out
	  w810		3-jack
	  z71v		3-jack (HP shared SPDIF)
	  asus		3-jack (ASUS Mobo)
	  asus-w1v	ASUS W1V
	  asus-dig	ASUS with SPDIF out
	  asus-dig2	ASUS with SPDIF out (using GPIO2)
	  uniwill	3-jack
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20/LW25 laptop
	  tcl		TCL S700
	  clevo		Clevo laptops (m520G, m665n)
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)

	ALC260
	  hp		HP machines
	  hp-3013	HP machines (3013-variant)
	  fujitsu	Fujitsu S7020
	  acer		Acer TravelMate
	  basic		fixed pin assignment (old default model)
	  auto		auto-config reading BIOS (default)

	ALC262
	  fujitsu	Fujitsu Laptop
	  hp-bpc	HP xw4400/6400/8400/9400 laptops
	  benq		Benq ED8
	  basic		fixed pin assignment w/o SPDIF
	  auto		auto-config reading BIOS (default)

	ALC882/885
	  3stack-dig	3-jack with SPDIF I/O
	  6stck-dig	6-jack digital with SPDIF I/O
	  arima		Arima W820Di1
	  auto		auto-config reading BIOS (default)

	ALC883/888
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack digital with SPDIF I/O
	  3stack-6ch    3-jack 6-channel
	  3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
	  6stack-dig-demo  6-jack digital for Intel demo board
	  acer		Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
	  auto		auto-config reading BIOS (default)

	ALC861/660
	  3stack	3-jack
	  3stack-dig	3-jack with SPDIF I/O
	  6stack-dig	6-jack with SPDIF I/O
	  3stack-660	3-jack (for ALC660)
	  uniwill-m31	Uniwill M31 laptop
	  auto		auto-config reading BIOS (default)

	CMI9880
	  minimal	3-jack in back
	  min_fp	3-jack in back, 2-jack in front
	  full		6-jack in back, 2-jack in front
	  full_dig	6-jack in back, 2-jack in front, SPDIF I/O
	  allout	5-jack in back, 2-jack in front, SPDIF out
	  auto		auto-config reading BIOS (default)

	AD1981
	  basic		3-jack (default)
	  hp		HP nx6320
	  thinkpad	Lenovo Thinkpad T60/X60/Z60

	AD1986A
	  6stack	6-jack, separate surrounds (default)
	  3stack	3-stack, shared surrounds
	  laptop	2-channel only (FSC V2060, Samsung M50)
	  laptop-eapd	2-channel with EAPD (Samsung R65, ASUS A6J)

	AD1988
	  6stack	6-jack
	  6stack-dig	ditto with SPDIF
	  3stack	3-jack
	  3stack-dig	ditto with SPDIF
	  laptop	3-jack with hp-jack automute
	  laptop-dig	ditto with SPDIF
	  auto		auto-config reading BIOS (default)

	STAC9200/9205/9220/9221/9254
	  ref		Reference board
	  3stack	D945 3stack
	  5stack	D945 5stack + SPDIF

	STAC9227/9228/9229/927x
	  ref		Reference board
	  3stack	D965 3stack
	  5stack	D965 5stack + SPDIF

	STAC9872
	  vaio		Setup for VAIO FE550G/SZ110
	  vaio-ar Setup for VAIO AR

---

### Post by farbird on 2007-08-21
nothing new to me...

---

### Post by matth45 on 2007-08-23
re: sound - none of those models will work.  The ALSA driver will only even let you try models listed under the ALC861VD/660VD chipset.

check out my post here:

[http://ubuntuforums.org/showpost.php?p=3243087&postcount=141](http://ubuntuforums.org/showpost.php?p=3243087&postcount=141)

---

### Post by farbird on 2007-08-27
thanks..

u made my day happy after hearing sounds from my headphone jack!

---

### Post by apksr on 2007-08-29
I have the TX1220us with Broadcom wireless 4321G chip set running 64bit 2.6.22.2 and got it working following this post using ndiswrapper:

[http://ubuntuforums.org/archive/index.php/t-336654.html](http://ubuntuforums.org/archive/index.php/t-336654.html)

Using this driver and removing bcmwl5.sys so that only bcmwl564.sys was available. 

[http://ftp.us.dell.com/network/R140746.EXE](http://ftp.us.dell.com/network/R140746.EXE)

Good luck!

---

### Post by damawa42 on 2007-09-18
did anyone get the touchscreen working? I have the tx1250ea and am having no luck at all - sometimes it registers touches, sometimes not (but when it does register, the calibration is way out).

Cheers guys!

---

### Post by Cuppa-Chino on 2007-09-24
touchscreen description is in this thread: [http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000]("http://ubuntuforums.org/showthread.php?t=442483&highlight=tx1000")

works a treat

---

### Post by zarshark on 2007-10-07
if someone still needs to configure the sound system in tx1000, then:

1. download the last alsa driver:
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2)

2. then:
tar -xvjf alsa-driver-1.0.15rc3.tar.bz2
cd alsa-driver
./configure
make
# under root
make install

3. Then:
gedit /etc/modprobe.d/alsa-base
and add the following line:
options snd-hda-intel index=0.

Then restart the system.
you will see that the mute button will be blue. Headphone and mic now are enable.

---

### Post by sauronsmatrix on 2008-01-17
sorry if this is gravedigging, but installing ubuntu (or kubuntu :) ) 8.04 alpha 3 makes sound work out of the box

---

### Post by vibhor goyal on 2008-01-31
follow this link for perfect guide to installing ubuntu on hp tx1000:

i got evrythng wrking ...   [http://www.codepencil.com/index.php/installing-ubuntu-gutsy-gibbon-on-my-hp-tx1003au-laptop/](http://www.codepencil.com/index.php/installing-ubuntu-gutsy-gibbon-on-my-hp-tx1003au-laptop/)

---

### Post by magicfab on 2008-02-11
This thread has interesting information about the tx1000 series:
[http://ubuntuforums.org/showthread.php?t=442483](http://ubuntuforums.org/showthread.php?t=442483)

I am also documenting setting up Ubuntu Hardy (8.04) on that same model (except canadian):
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca)

---

### Post by LazyEngineer on 2008-05-15
Hello all - new user here.

A couple items I'm having troubles with - perhaps someone can help?
Basics:
HP Pavilion TX1000 (1308) with 4 GB of RAM (known good).  
Installed Ubuntu 64bit (in order to use all 4GB of RAM)


1) I can't get the wireless on my laptop to work.  I've tried following the suggestions on other threads, but these don't work.
[http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310](http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310)

In my case, I first performed System/Administration/Update Manager.

After the necessary installs and reboot, I launched applications/accessories/terminal

I then typed in the following string of commands into terminal (input in blue, responses in red - not all responses are included herein):


[COLOR="Blue"]sudo rmmod ndiswrapper[/COLOR]
response was
[COLOR="Red"]sudo: unable to resolve host lazy-laptop
[sudo] password for laptop:[/COLOR]


sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils

Some of these I typed in multiple times until it started giving me the same answer. (weird that you have to do that)  My first question is: [COLOR="DarkGreen"]why am I getting the unable to resolve host error message?[/COLOR]

I then run:
[COLOR="Blue"]sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`[/COLOR]
wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)  
[SIZE="3"] The FIRST time I tried this, I typed in the above R151517.exe command.  In the end, the process did not work.  So I repeated everything a second time, this time using the driver file from HP - which is sp34167.exe - alas, that didn't end up working either. [/SIZE]

After every command, I got the annoying [COLOR="Red"]unable to resolve hostname[/COLOR] response, after which it then did stuff anyway, so I'm assuming the commands actually worked.  

[COLOR="Blue"]wget [http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.5](http://superb-east.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.5)**2**.tar.gz
[/COLOR]
which it did.

[COLOR="Blue"]tar -xzvf ndiswrapper-1.52.tar.gz[/COLOR]
and it then extracted a mess of files into a "drivers" directory.

[COLOR="Blue"]sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist[/COLOR]
[COLOR="Red"]bash: /etc/modprobe.d/blacklist: Permission denied[/COLOR]
well this can't be good.  but wait!  the instructions say this might happen, and give an alternative suggestion:
[COLOR="Blue"]
sudo -s
echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
exit[/COLOR]
[COLOR="Red"]exit[/COLOR] 
A little odd that it repeated the word exit back to me, but ok.

I then do the suggested reboot.

[COLOR="Blue"]cd ndiswrapper-1.52
sudo make uninstall
[/COLOR]
Still getting the unresolved host nag message, but it does things, so this is good.  repeat the [COLOR="Blue"]sudo make uninstall[/COLOR] command a few times as per directions.

[COLOR="Blue"]sudo make distclean
sudo make
sudo make install[/COLOR]
Does lots of things after each of those commands - good sign.  Now I have to change directors to where my driver file is located.  I had put it in a directory called Drivers1. so...

[COLOR="Blue"]cd
cd Drivers1
cabextract sp34167.exe
sudo bash
ndiswrapper -i bcmwl5.inf
ndiswrapper -l
ndiswrapper -m
modprobe ndiswrapper
ndiswrapper >> /etc/modules
exit
[/COLOR]
all seemed to work good

reboot

Still no sign of a wireless network option anywhere.  :confused:
is it because I'm trying to use ubuntu 64 bit?

---

### Post by LazyEngineer on 2008-05-19
To answer my own reply - the wireless was solved by following the instructions posted here:

[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

---

