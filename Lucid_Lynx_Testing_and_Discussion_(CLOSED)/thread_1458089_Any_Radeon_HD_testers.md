---
title: "Any Radeon HD testers?"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fluteflute on 2010-04-19
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790)

I was just wondering if anyone else could try using the open source driver (not the fglrx) for a day or two and see if they get any crashes on these cards. Or on any other similar ones. 

I want to know if everyone with the HD4350, HD4650 and HDHD4670 graphic cards experience crashes? And if any other cards are affected?

Thanks in advance, it's just this seems a major issue at present (to me and potentially others)!

---

### Post by djchandler on 2010-04-19
> **fluteflute said:**
> [https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790)

I was just wondering if anyone else could try using the open source driver (not the fglrx) for a day or two and see if they get any crashes on these cards. Or on any other similar ones. 

I want to know if everyone with the HD4350, HD4650 and HDHD4670 graphic cards experience crashes? And if any other cards are affected?

Thanks in advance, it's just this seems a major issue at present (to me and potentially others)!

I don't have those cards, but I do know there's a confirmed and high priority bug causing heat issues with the [xserver-xorg-video-ati]("https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790") driver. The bug has been passed upstream to freedesktop.org.

Don't get too freaked out by the following. I'm speculating, and I'm certainly not always 100% correct.

In my case, because it's a laptop perhaps as well as having an IGP on the northbridge, which makes heat issues more critical for overall system stability, my system was turning itself off due to a safety setting in the BIOS. After reading your report, I'm thinking it may be the same bug as the one I reported causing your problem. But because it's just the GPU overheating, it's making the screen go wonky before you can do anything about it. You may want to check your video card on the flip side of where the GPU is mounted for discoloration or outright scorching. I have burned Nvidia discrete cards before and had similar problems to what you describe in your bug report before they finally blew out a capacitor or slightly melted the board around the GPU soldering points.

Here's my original report at launch pad:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/557829](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/557829)

Apparently this is not a specific Ubuntu problem. This could be affecting all Linux users with newer (RV6xx, RV7xx, and newer) ATI GPUs. You may want to amend my report upstream here:

[http://bugs.freedesktop.org/show_bug.cgi?id=27705](http://bugs.freedesktop.org/show_bug.cgi?id=27705)

In the meantime, my advice is to run the fglrx driver no matter what other problems it causes, and help fix those issues. IMHO using the current xserver-xorg-video-ati driver could be putting your hardware at risk.

AFAIK, this is the first ATI FOSS driver that has been able to support compiz that's been included in Ubuntu. New features create new issues. It would be nice to know what kind of GPU cooling apparatus the FOSS driver developers are using.

---

### Post by jjcv on 2010-04-19
> **fluteflute said:**
> [url]
I want to know if everyone with the HD4350, HD4650 and HDHD4670 graphic cards experience crashes? And if any other cards are affected?!

I am running an ATI Mobility Radeon HD 4670 on a Dell Studio XPS 16 under Lucid Beta 2 with all updates.  Have not had any problems with the open source driver.  Have been running since Alpha 3 without issues.  Runs at 1920 x 1080.

Have not tried the fglrx.  Mainly because my experience with on 9.10 was not good, very slow performance and videos not possible to watch in full screen mode.  As the open source driver is working well for me I see no reason to change.   

Also run Gnome-Shell with no problems.

---

### Post by Reiger on 2010-04-19
Replied to the bug report. In short try radeon.modeset=0 or pci=nomsi as boot parameter.

---

### Post by Mars73 on 2010-04-21
I have a HP 4710s notebook with Ati Radeon HD4350 mobility in it and installed 10.04 2 days ago.
I had about 4 'crashes' where the screen would just go blank. Not black or weird characters but backlight is still on, sort of white glaze.
Nothing reacts anymore, no ctrl/alt/del, shift f2 etc, only turning it off and on again.
Not sure if it has anything to do with the videocard. I'm currently on for about 4 hours without any crashes.
Other then that (I'm sure it will get fixed) I'm quite pleased with Lucid.
Not very pleased if it constantly overheats my laptop though, if that is whats happening, though the laptop doesn't feel warm/hot.

---

### Post by buellman on 2010-04-21
I have the following card
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]
and had also the problems the Threadstarter described.
After adding pci=nomsi to grub the system did not crash one single time the last 16 hours so it seems to be a workarround for now.

Greets. Buellman

---

### Post by BrokeMahPC on 2010-04-21
ATI Radeon HD 4670 here - I switched to the open source driver to see if Plymouth would display correctly at startup. At the time I was not aware of the power management bug. I experienced temperature problems and crashes on my desktop PC, particularly when using gimp and watching a video / TV at the same time. Problems solved by switching back to proprietary fglrx.
 
_I would take the above view from djchandler seriously!_
> IMHO using the current xserver-xorg-video-ati driver could be putting  your hardware at riskIf using open source video drivers check your hardware temperatures and it should be noticeable that your fans are spinning at very high speed anyway. My PC case developed a resonant rattle!

I have not tried this yet:
> In short try radeon.modeset=0 or pci=nomsi as boot parameter.

---

### Post by buellman on 2010-04-21
> **BrokeMahPC said:**
> I experienced temperature problems and crashes on my desktop PC,

May I ask how you know that there are problems with the temperature?
I have the sensors-applet running and see temps from my hdds, my CPU and rotation from the fans. I didn't notice any problems.

Does lm-sensors support temp-messurement of the GPU? Problem is that my 4670 is passive cooled so I dont hear any fan spinning as there is none ;-)
But none the less I would hate to fry the card.

Btw: I tried to use fglrx but it crashed the system also randomly. But not only in Lucid... Karmic was the same. Even with my former card (ATI HD 3470).

But I noticed some problems in dmesg after the crash (with radeon... not fglrx!):
```
[ 4752.331431] [drm:radeon_fence_wait] *ERROR* fence(ffff88005f5f8d00:0x00027D00) 510ms timeout going to reset GPU
[ 4752.331443] radeon 0000:01:00.0: GPU softreset 
[ 4752.331449] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0xE00014A4
[ 4752.331455] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00100002
[ 4752.331460] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200020C0
[ 4752.516240] radeon 0000:01:00.0: Wait for MC idle timedout !
[ 4752.516245] radeon 0000:01:00.0:   R_008020_GRBM_SOFT_RESET=0x00007FEE
[ 4752.516301] radeon 0000:01:00.0: R_008020_GRBM_SOFT_RESET=0x00000001
[ 4752.516366] radeon 0000:01:00.0:   R_000E60_SRBM_SOFT_RESET=0x00000C02
[ 4752.565091] radeon 0000:01:00.0:   R_008010_GRBM_STATUS=0x00003028
[ 4752.565096] radeon 0000:01:00.0:   R_008014_GRBM_STATUS2=0x00000002
[ 4752.565102] radeon 0000:01:00.0:   R_000E50_SRBM_STATUS=0x200000C0
[ 4752.567381] [drm:radeon_fence_wait] *ERROR* fence(ffff88005f5f8480:0x00027D02) 510ms timeout going to reset GPU
[ 4752.567394] radeon 0000:01:00.0: GPU softreset
```
and so on. I looked for this error at google and did find bug-reports on this from 2009 so this seems to be an older bug.

Hmmm...

---

### Post by buellman on 2010-04-21
Ok... forget it. Crashed a minute ago... maybe I shoud give radeonhd a try?

---

### Post by BrokeMahPC on 2010-04-21
You can't get the GPU temp without FGLRX, correct, lm-sensors does not support it as far as I know - the madly spinning fans plus warmer than usual air being expelled from the case alerted me that something wasn't right.

Now using fglrx I can get the GPU temp by:
```
aticonfig --odgt
```

which gives:
```
Default Adapter - ATI Radeon HD 4600 Series
                  Sensor 0: Temperature - 32.00 C
```
With fglrx:
When not doing anything GPU temp varies between 32C and 34C.
Playing full screen video 1080x1920 - GPU temp varies between 37C and 39C
I don't get madly spinning fans or very warm air blowing out of the case.

I agree this isn't very scientific but I'm convinced there was a difference. The PC does not crash with FGLRX. It would help if we could access the GPU temp somehow when not using FGLRX so we could be more thorough when looking at this.

I just noticed I have this entry in lm-sensors that roughly seems to follow the temp of the GPU from aticonfig - is it the GPU or not, anyone?
```
coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +37.0°C  (high = +76.0°C, crit = +100.0°C)
```

---

### Post by buellman on 2010-04-21
Ok... I will give fglrx a new chance... maybe I can see what happens if X crashes with fglrx to. I did not look at dmesg when using fglrx the last time.

---

### Post by BrokeMahPC on 2010-04-21
Just un-installed fglrx and reverted to the open source drivers to see if that lm-sensor reading shows anything amazing.

We have had an update since the other day - now at:
xserver-xorg-video ~ 1:6.13.0-1ubuntu5

No mad fan speeds, lm-sensors:
```
sensors
```
gives:
```
coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (high = +76.0°C, crit = +100.0°C) 
```

I did get one crash, black screen with vertical thin white stripes and a stuck sound loop but it seems much improved. Oh well back to fglrx for now.

---

### Post by andrewthomas on 2010-04-21
The latest version of sensors-applet (2.2.5) has added support for ATI GPUs using proprietary drive.  

[http://ubuntuforums.org/showpost.php?p=9062095&postcount=27](http://ubuntuforums.org/showpost.php?p=9062095&postcount=27)

[http://sensors-applet.sourceforge.net/index.php?content=source](http://sensors-applet.sourceforge.net/index.php?content=source)

I compiled it myself, but there is a link to a deb in the forum post.

---

### Post by psusi on 2010-04-21
I have a Radeon HD 4850 and have had no issues at all with the open source drivers.  I have been so pleased with them I haven't even bothered trying fglrx.

---

### Post by Longinus00 on 2010-04-21
I too have been using a 4850 for about half a year with the open source drivers with no problems.

---

### Post by djchandler on 2010-04-21
> **psusi said:**
> I have a Radeon HD 4850 and have had no issues at all with the open source drivers.  I have been so pleased with them I haven't even bothered trying fglrx.

Perhaps the problem only appears with passive cooling on your GPU. Thay's one of the reasons I would like to know what cards and cooling solutions the freedesktop.org developers are using.

One thing I can tell you all for certain is I have never seen such quick action at launchpad on a bug report that I have filed. Status, confirmation and passing the bug upstream was done very quickly, a matter of 2 days total.

Hopefully things are improving overall. I'm using fglrx while running the AMD64 RC with a fresh install from a Final ISO candidate. System cooling is better on my laptop and Plymouth is working without me needing to add or delete boot parameters.

I'm still bug-hunting though, just in case.

---

### Post by lavinog on 2010-04-21
according to the radeon man page, many of the power saving features require kms to be disabled.  Also they are disabled by default and need to be enabled in Xorg.conf
You could try experimenting with them.

One thing I noticed with my 200m (Not HD but uses radeon driver) lucid has about half the battery life as karmic...it is most likely due to the lack of power saving features.

---

### Post by BrokeMahPC on 2010-04-21
I didn't have any troubles with the open source drivers in Karmic - it's only recent developments. It's not passively cooled either - has a fan. Thank you for the info on sensors-applet - will compile it! (can't see a deb anywhere on that page?)

---

### Post by lavinog on 2010-04-21
> **BrokeMahPC said:**
> I didn't have any troubles with the open source drivers in Karmic - it's only recent developments.

Kms wasn't enabled by default in Karmic.

---

### Post by Mars73 on 2010-04-21
For monitoring your gfx temperature without using fglrx you could use gkrellm.
It's in synaptic.
When started, rightclick on top, go to Configuration, then Buildins, Sensors, Temperatures and choose GFXZ.
You can now watch the temp of your gfx card.
My mobility HD4350 is 72 degr Celius at idle, which I think is too hot for just doing nothing.
I can install fglrx but I can't use compiz then. And somehow it says Ati Fire GL in the Hardware Drivers menu. Is that normal?

---

### Post by Reiger on 2010-04-21
Well fgl in fglrx originally referred to the Fire GL line of cards? And if I am not much mistaken (although it's equally likely that I am) the r refers to Radeon.

---

### Post by clhsharky on 2010-04-21
HI all


1 OP fluteflute concern on this bug
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790)
> Bryce Harrington 
If it is correct that this regression started April 10th, that roughly coincides to when we brought in the 6.13.0 version of -ati.
Changed in xserver-xorg-video-ati (Ubuntu):
status:	 Confirmed &#8594; Incomplete
Driver bug for ATI devs


2 djchandler After looking at bug reports on this thread, I also agree that most probable cause inadequate cooling from card & board builders. Not All Hardware Is Created Equal.

Entry level graphic card  HD4350
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/565790)

IGP  R780  '3200' known to run hot
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/557829](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/557829)

IGP '3100' low end value chip
[http://bugs.freedesktop.org/show_bug.cgi?id=27705](http://bugs.freedesktop.org/show_bug.cgi?id=27705)


3 R600/R700 laptops that need Power Management that fglrx has but is not a delight on linux can now be tested in OSS drivers.

You need KMS its default in Lucid and the 2.6.34 kernel-ppa/mainline/drm-next
[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-next/current/) 
and you may need radeon.dynpm=1 in the boot string

I also recommend xorg-edgers PPA
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

Sharky

---

### Post by Reiger on 2010-04-21
Thanks for providing the outline of the installations/ppas needed; might give it a whirl over the weekend or something. Sounds like an excellent opportunity to fry my laptop just before the replacement arrives... :P

---

### Post by clhsharky on 2010-04-22
HI Reiger

The R600 have been out for over 2 years. Because of some fglrx problems and many FOSS users have used OSS drivers, and with no PM by default. Theres little chance, but anything is possible. BIOs should shut down before- 
  
> Sounds like an excellent opportunity to fry my laptop just before the replacement arrives..

Checking temp, battery time, any issues, you know

> Re: Any Radeon HD testers? 


Sharky

---

### Post by Mars73 on 2010-04-22
I must say that since yesterday morning it has not crashed anymore.
I've been checking my temperature constantly while having some java sites open, running a youtube 'movie' (I have the standard flashplugin-installer from synaptic installed), watching a HD movie with smplayer and running a clamscan all at once and while cpu gets higher, the gfx temperature only gets higher a few degrees. It sits between 68 and 75 degr. Celsius.
This is with standard open source ati drivers, not the xorg edgers.
I still feel that idle temp around 70 is a bit high and I think because of this fan is blowing constantly, though not at high speed.

---

### Post by shindz on 2010-04-22
I hear about this bug  and see it on the wiki page. I want to know how I could help on testing. I have an ATI X200M, I don't know if I'm using the DR1 or DR2 thing.  With my graphic card, could I help testing or my card is not affected at all ?

---

### Post by clhsharky on 2010-04-22
HI Mars73

Power Management in OSS drivers 'the kernel is now part of the stack' another reason for KMS. PM is not yet as good as fglrx but I'm sure it will get better  with tweaking, its still very new.
Good to hear you had some success.

Sharky

CPU Frequency Scaling controls = CPU
OSS power management controls = video chip, memory 
BIOs controls = Fan speed 
They all work towards reduce heat, noise, and increase battery time.

---

### Post by clhsharky on 2010-04-22
HI shindz

What bug are you talking about

Sharky

---

### Post by shindz on 2010-04-22
> **clhsharky said:**
> HI shindz

What bug are you talking about

Sharky
I mean this memory leak on the X.org module

---

### Post by clhsharky on 2010-04-22
HI shindz


You need a Launchpad account
 
Directions
[http://ubuntuforums.org/showpost.php?p=9154424&postcount=7](http://ubuntuforums.org/showpost.php?p=9154424&postcount=7)

wiki page
[https://wiki.ubuntu.com/X/Testing/GEMLeak](https://wiki.ubuntu.com/X/Testing/GEMLeak)

Sharky

---

### Post by Infil on 2010-04-22
I'm experiencing this issue with a fully updated Lucid beta 2 with no other relevant changes. I have a HD4570 Mobility.

Compiz works fine which I guess means that Ubuntu uses the RadeonHD drivers. But it appears that you guys are talking about this as an issue with the radeon- or ati-driver so I'm a bit confused. Does this issue affect all open source ATi drivers, or am I not using RadeonHD?

---

### Post by buellman on 2010-04-22
There are three drivers:
radeon (default), radeonhd and fglrx.
If you have not chosen one of them explicitly you most likely have the normal radeon-driver installed.

Greets. Buellman

---

### Post by BrokeMahPC on 2010-04-22
> There are three drivers:
radeon (default), radeonhd and fglrx.
If you have not chosen one of them explicitly you most likely have the  normal radeon-driver installed.

Greets. Buellman 	
Might help to explain how to do that as it does not give you the option to choose?

RE temperature monitoring - the best I could find was Xsensors from synaptic - a GUI that user the data from lm-sensors. If you have configured lm-sensors with:
```
sudo sensors-detect
```
it works well and updates every 2 seconds (adjustable) - create a launcher for it by right clicking on the desktop and adding "xserver", no quotes to the name and command fields in -.create launcher.

---

### Post by Infil on 2010-04-22
Then I guess there has been som changes in the radeon-driver (which Ubuntu packages as "ati" ?) since I have excellent Compiz performance with my card.

I'll try RadeonHD, fglrx and the kernel options in grub and see what happens.

---

### Post by Yellow Pasque on 2010-04-22
> **BrokeMahPC said:**
> Might help to explain how to do that as it does not give you the option to choose?
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

---

### Post by Infil on 2010-04-22
The info in that guide made me believe that I was using RadeonHD by default. In any case, it doesn't tell you how to start using it if not.

---

### Post by Yellow Pasque on 2010-04-22
Are we reading the same document? :lolflag:

> **Infil said:**
> The info in that guide made me believe that I was using RadeonHD by default.

The first two sentences should make it clear:
> This document explains how to install and use the open-source radeonhd drivers on Ubuntu. This shouldn't be necessary... unless you're having problems with **the open-source "ati/radeon" driver that comes pre-installed with Ubuntu**. 

>  In any case, it doesn't tell you how to start using it if not.
You explicitly specify it in xorg.conf, like this part shows: [https://help.ubuntu.com/community/RadeonHD#Configuration](https://help.ubuntu.com/community/RadeonHD#Configuration)

---

### Post by ronparent on 2010-04-22
My first problem with using the open source drivers with my card is that when I try to boot with two dvi connected monitors I get a black screen and find the system unusable. A reboot is necessary with one monitor unplugged, My first step then is to install the restricted drivers (which do work beautifully for me). Would otherwise respond to your request.

---

### Post by stefanauss on 2010-04-23
I'm having the same issues on my Mobility Radeon HD and radeon module.
Although i do not have any power management settings (i understood this is because of radeon module defaults, right?) this bug does not come with heat problems in my case

I would say that, beetween Lucid Beta 1 and Beta2, i used the radeon module for 10+ days uptime and compiz enabled without any sort of problems and with amazing performances (but no PM, of course).

Then a massive update, i'm almost sure there were new radeon 6.13.xx series AND a new kernel, broke up the situation.

I tried downgraded packages of xserver-xorg-video-radeon, but the issue remains.

I have not tried any boot parameter, yet. Should i try something in particular?

---

