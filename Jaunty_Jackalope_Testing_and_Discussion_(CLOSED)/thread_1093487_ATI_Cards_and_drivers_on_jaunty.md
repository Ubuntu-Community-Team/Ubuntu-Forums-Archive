---
title: "ATI Cards and drivers on jaunty"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sdm_cacto on 2009-03-11
I've been testing Ubuntu Jaunty for a couple of weeks, and cant get to install the drivers for my Ati Radeon x1270. 
I've heard that ATI will cease to support this kind of hardware, does that mean that I have to use the Open Source driver?
Thanks for the help

---

### Post by cubeist on 2009-03-11
It's a well known Jaunty "bug" mentioned in the alpha release notes...
> A new XServer, version 1.6, is included in Alpha 4. The binary proprietary fglrx driver is not yet supported for this server and will exhibit various serious issues if run against it. Users of this driver are encouraged to wait or to switch to the open source -ati driver in the meantime. 313027
[https://bugs.launchpad.net/bugs/313027](https://bugs.launchpad.net/bugs/313027)

And yes, in the future, you can use the proprietary 9.2 release, or open-source ati

---

### Post by michael37 on 2009-03-11
Since I had the same problem, I'd just mention a few things I learned.

If you have used fglrx previously, a few legacy items will interfere with normal operations of the open source ATI driver.  You gotta remove them.  Follow the instructions at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by sdm_cacto on 2009-03-11
Thanks! My bad, I should've read the releasenotes.
Right now i'm using the open source drivers,  so far so good.

---

### Post by xeddog on 2009-03-13
So does this mean that there is no dual monitor support for Radeon cards yet?

xeddog

---

### Post by epitaph on 2009-03-13
Hello. I have not attempted to run Jaunty on my laptop yet but I'm beginning to be concerned on what will happen when I try (doesn't look like I will be attempting anytime soon).

If I understand correctly, the fglrx driver will be dropping support for the R300-R500 chipsets in their new version. My laptop has an x1150 in it.

[http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r500_legacy&num=1)

Will they provide a version of the driver that supports X server 1.6 and the R500 series prior to dropping the support? Or will I be stuck with the open source drivers.

The situation seems to have turned grim:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/313027)

> 

AMD is not making any progress for this, and there's little we can do about that beyond the regular nagging on the status calls. We are now focusing on providing the latest free -ati driver which will work on modern chips as well. Please see bug 334101 for details.

Thus I take this off the release blocker list. That doesn't mean that we shouldn't provide a working fglrx driver in jaunty, of course, but it shouldn't be on the release team radar any more.

My laptop didn't seem too old until I started to look into this.

There have to be a lot of users on integrated R500 chipsets that will be deeply affected by this. Hopefully either a version of fglrx will be released that supports X server 1.6 and the R500 series or the open source drivers will grow quickly, improve 3D acceleration substantially, and provide usable XVideo.

[edit] Please read below -- besides 3D acceleration the open source driver is entirely usable now on Intrepid for me!

---

### Post by epitaph on 2009-03-13
Important update!

The last time I tried using the open source radeon drivers I was having all kinds of issues with suspend/resume and with nearly everything else (composited desktop, XVideo...).

This is no longer the case. Easy install on Ubuntu 8.10 and it has surprised me with how far it has come.

XVideo works wonderfully now with the radeon driver. I have better and more tear-free video with the open source driver than I had with fglrx. Not to mention I get to use xrandr for screen management now instead of bullying around with aticonfig.

The only issue is that Google Earth (OpenGL) runs very slow. I hope that the 3D acceleration will be improved. It's essentially a slide show.

It's possible to switch which screen your xV overlay is on, too! Very impressive -- extremely appreciate of the work the team has done on this open source radeon driver.

Thus, I recommend that if you do not need the benefit of the 3D acceleration support that fglrx provides that you use the open source drivers.

I'm glad this won't be a big issue. I'm sure there will be improvements on the OpenGL performance soon. Everything else "just works".

Looks like I got worked up for nothing! Jaunty shouldn't be a huge problem for R500 chipset users if this support continues.

---

### Post by michael37 on 2009-03-14
Important: fglrx is not expected to work in Jaunty.
[http://www.phoronix.com/scan.php?page=news_item&px=NzExOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzExOQ)

---

### Post by arunthopil on 2009-03-19
hi all,,,,,,,,,,


    why dont you try for a package named "envyng" ...............   install it, u can find it under applications> systemtools> envyNG

it will suggest you the driver tht have to be used..............

[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)           try ths i was having a FGLRX driver issue ............ I fixed it.......I thik ths cud help a lot f people

thnx
arunthopil:D

---

### Post by Stochastic on 2009-03-19
> **xeddog said:**
> So does this mean that there is no dual monitor support for Radeon cards yet?

xeddog

On the contrary, my ATI Radeon Xpress 200m has great dual screen functionality using Jaunty's open source drivers.

---

### Post by zika on 2009-03-19
> **arunthopil said:**
> hi all,,,,,,,,,,


    why dont you try for a package named "envyng" ...............   install it, u can find it under applications> systemtools> envyNG

it will suggest you the driver tht have to be used..............

[http://thopilismaakan.blogspot.com/](http://thopilismaakan.blogspot.com/)           try ths i was having a FGLRX driver issue ............ I fixed it.......I thik ths cud help a lot f people

thnx
arunthopil:D
I do not recommend envyNG. especially not for alpha release. I'm not even sure it works for jaunty.

update: until yesterday fglrx driver is obtainable and installable from Hardware drivers panel so that makes once more envyNG unnecessary.

---

### Post by epitaph on 2009-03-19
> **xeddog said:**
> So does this mean that there is no dual monitor support for Radeon cards yet?

xeddog

I don't think it means that. I still can successfully use a second monitor either in extend or mirror mode. It's a pretty easy configuration when using xrandr and the configuration utility in Ubuntu (Screen Resolution).

It does have one quirk, though. Using aticonfig it is possible to force output to the external connection port. I have yet to find a way to force output to be active on my VGA out with xrandr. A lot of projection systems will not turn on unless they are receiving a signal. Conversely, xrandr does not want to seem to enable the external port until it sees something else on the other end... It's a standoff and I've ended up plugging the laptop into a monitor to make the VGA out active then changing the cable.

Surely there is some way to make xrandr output to a port that isn't plugged in.

[edit] And to the person attempting to recommend envyng: the issue being discussed is not related to difficulty installing the fglrx driver. It pertains to the fact that the fglrx driver is dropping support entirely for the R500 chipset and will not be putting out a version that supports X server 1.6. This means that the open source radeon driver is the only driver choice for R500 users in Jaunty.

---

### Post by Bert Mariën on 2009-03-21
> **sdm_cacto said:**
> I've been testing Ubuntu Jaunty for a couple of weeks, and cant get to install the drivers for my Ati Radeon x1270. 
I've heard that ATI will cease to support this kind of hardware, does that mean that I have to use the Open Source driver?
Thanks for the help

I wrote it already a couple times before at other posts, but read this

[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

### Post by epitaph on 2009-03-31
Gah!

I went back to using fglrx again after they released the final Catalyst that will support the R500 series. They finally fixed composited desktop + OpenGL problems! Looks like I'm going to have a hard choice when 9.04 is released...

1) Stick with 8.10 and Catalyst 9.3 for a seamless desktop experience.

-or-

2) Go to 9.04, deal with extremely low OpenGL performance and wait for the open source driver to support DRI2 to solve flickering issues.

For me, it's a hard choice. Talk about being between a rock and a hard place.

---

### Post by xebian on 2009-03-31
I could not understand this ati drivers.  I swear at one time I had composting once but could not get it back on a Radeon x200M laptop.

I have 8.10 working nicely on a desktop with Radeon x1250 with 9.2 from ATI, but when I upgraded to Kubuntu 9.04 last night I could not get it to work.  In frustration I went to 'ati', removed all fglrx and rebooted.  But lo and behold, I have composting after with all the eye candies.  It's wierd:confused:

---

### Post by epitaph on 2009-03-31
The open source radeon driver supports R500 completely. There shouldn't really be any issues using it except for lackluster performance with OpenGL apps (try using Google Earth). For most with R500 IGP's it should be adequate.

---

### Post by dE_logics on 2009-04-02
Hay...check this out.

[http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html](http://display-and-video.free-driver-download.com/ATI%20Technology/49042/ATI-Radeon-HD-2300-HD-2350-HD-2400-Driver-RadeonHD-1.2-Linux.html)

Does it work?

---

### Post by olskar on 2009-04-02
I haven't installed any proprietary drivers for my x1600 card and the performance with opensourcedriver is very nice

---

### Post by kevpan815 on 2009-04-02
All Of My ATI Problems From Alpha 6 Are Fixed In The Jaunty Beta!

---

### Post by super.rad on 2009-04-02
Got a new pc yesterday with ATI Radeon HD3200 graphics, installed the FGLRX driver using jockey and desktop effects are all working but I can't play videos without turning them off first.
Will the opensource drivers work with my card and will they be better? Will they let me watch videos with desktop effects still on?

---

### Post by zika on 2009-04-02
> **super.rad said:**
> Got a new pc yesterday with ATI Radeon HD3200 graphics, installed the FGLRX driver using jockey and desktop effects are all working but I can't play videos without turning them off first.
Will the opensource drivers work with my card and will they be better? Will they let me watch videos with desktop effects still on?
with fglrx You could try: System->Preferences->MultimediaSystemsSelector->Video->X11(noXv) ... that worked with Intrepid ...
opensource driver doesn't allow me yet to try effects yet (HD3650) ... and I do not like fglrx ... :)

---

### Post by super.rad on 2009-04-02
Haven't got "MultimediaSystemsSelector" or anything similar in the menu's

---

### Post by zika on 2009-04-03
> **super.rad said:**
> Haven't got "MultimediaSystemsSelector" or anything similar in the menu's
Alt-F2:gstreamer-properties
(You can activate it in System->Preferences->MainMenu->Preferences)
p.s. sorry, I've just seen You are (K)ubuntu user. ... something similar to gstreamer-properties must exist in (K)ubuntu.

---

### Post by dE_logics on 2009-04-03
ATI itself provides drivers for almost all its graphs chips except the mighty x1270

To that is the big issue here.

---

### Post by super.rad on 2009-04-03
> **zika said:**
> Alt-F2:gstreamer-properties
(You can activate it in System->Preferences->MainMenu->Preferences)
p.s. sorry, I've just seen You are (K)ubuntu user. ... something similar to gstreamer-properties must exist in (K)ubuntu.

Actually I'm currently using gnome. Thanks that worked perfect, video now plays with desktop effects on.

---

### Post by freedom on 2009-04-03
I'll just say one thing...
I curse the day when I bought laptop with ATI graphics. period.

sluggish performance, issues when X restarts and logoff, no suspend2ram with fglrx...
what else do you need. GO buy nVidia or Intel graphics based laptops... Don't be stupid like I was :D

---

### Post by Locoxella on 2009-04-06
> **zika said:**
> Alt-F2:gstreamer-properties
(You can activate it in System->Preferences->MainMenu->Preferences)
p.s. sorry, I've just seen You are (K)ubuntu user. ... something similar to gstreamer-properties must exist in (K)ubuntu.

This worked like  charm. Now I can see videos with my new laptop disregarding it has an ATI card.

I enable the multimedia icon to the system preferences menu by editing the of main menu.

Thank you very much

---

### Post by amirman on 2009-04-07
i'm supremely impressed by the open source driver for my ati mobility radeon x1400, it works awesome, i can even run some 3D apps while compiz is still on whereas i couldn't with when i was using fglrx with 8.10 - i'm just wondering since i can't play sauerbraten - *THE BEST GAME EVER FOR LINUX* - if making changes to my xorg.conf like specifying the driver and loading modules would help. or maybe i could try installing the radeonhd driver? how much would you folks (the ones with experience) recommend or not recommend taking these actions. should i just wait for the development with Gallium3D to kick in for openGL support?

---

### Post by Neo4 on 2009-04-11
Crap! 

when I try to install 9.3 driver after reboot I get an error and I have to run in low graphics!

with restricted driver it work good but that version don't have fan control and my fan spins too fast :S

---

### Post by amirman on 2009-04-11
that's because 9.3 doesn't work with the new xserver that jaunty uses. you could try 9.4 (it works with the new xserver) if you find it in the repos, it's an experimental version but i've heard it works well for certain ati cards. unfortunately it doesn't work with mine. good luck.

---

### Post by xeddog on 2009-04-14
I have the Jaunty beta installed on my 32-bit 2.4GHz P4.  My graphics card is an ATI Radeon 9600 dual head.  Now If I have this straight, The ATI 9.3 drivers do not work on Jaunty due to the Xserver version 1.6.  The 9.4 drivers are supposed to support the Xserver but not my card.  So I'm screwed coming and going???

I have the open-source drivers installed at the moment, but cannot activate any desktop effects, and no Compiz.  I just get that infamous "Desktop effects could not be enabled" panel.  Is there anything I can do with that?

TIA,

xeddog

---

### Post by Brachabre on 2009-04-14
xeddog, I have a 9600xt and am in the exact same situation as you! I want to use ATI's Catalyst 9.3 but supposedly not supported. And my card is unsupported otherwise for any newer drivers :(

I must admit, the open source ATI driver works great for general Compiz desktop effects out-of-the-box, but just can't handle 3D intensive games.

---

### Post by sansa dude on 2009-04-14
what about the x1650 pro card? how well is it supported with the ati software and theopen source.

---

### Post by michael37 on 2009-04-15
> **sansa dude said:**
> what about the x1650 pro card? how well is it supported with the ati software and theopen source.

Works with both open source radeon and radeonhd drivers.  Test with both, see which one works faster for you. Test with glxgears.

I have slightly older R500 family chipset and radeon 3D performance is faster than radeonhd.  Nevertheless, I can easily use Compiz with all the 3D embellishments and play quite a few games.  Both are slower than fgrlx was in hardy, but it's not an option for jaunty.

WARNING FOR ALL -- don't overdo your xorg.conf.  Jaunty works better with EXTREMELY simple ones.  Files posted below.

WARNING FOR R600 (Radeon HD 2000 / Radeon HD 3000) users -- This may break, melt, destroy, nuke, whatever your computer.  The driver support is very very different for R600 family.  I don't have R600 and don't know how it works.

RADEON:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option          "AccelMethod"    "EXA"  #either XAA or EXA. "XAA" is the default and safe choice
	Option          "DynamicClocks"  "on"   #This is for laptop users, it saves energy when in battery mode.
EndSection

Section "ServerFlags"
	Option         "DontZap" "off"  #allows to restart X with ctrl-alt-backspace, doesnt work by default
EndSection

```

RADEONHD
```

# xorg.conf.failsafe (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeonhd"
	BusID		"PCI:1:0:0"
	Option		"DRI"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "ServerFlags"
    Option         "DontZap" "off"    #allows to restart X with ctrl-alt-backspace, doesnt work by default
EndSection

```

---

### Post by zika on 2009-04-15
> **michael37 said:**
> WARNING FOR ALL -- don't overdo your xorg.conf.  Jaunty works better with EXTREMELY simple ones.  Files posted below.
in my case it work best without xorg.conf (literally ...) with radeon. it did not work with radeonhd (with xorg.conf, I did not get to that at that time) some time ago, I have not tried lately ... new 2.6.30 kernel brings some improvements and some stuff is already in kernel for ATI.
(Asus AH3650 a.k.a. ATI HD3650, 64-bit)

---

### Post by xeddog on 2009-04-15
OK, I have my dual monitors working with Ubuntu Jaunty.  I finally managed to get the open source drivers working.  But I still have a couple of minor issues and I am hoping that someone can help me out with these.

1.  When I first boot the computer, it will come up but display #1 has a black screen.  I can get it back easily enough just by typing ctl-alt-F1, and then without entering any commands type ctl-alt-F7.

2.  When I go to System>Preferences>Appearance and try to enable desktop effects I get "Desktop effects could not be enabled" after a few seconds of the computer "thinking" about it.  

Any ideas how I can resolve these two things?

TIA,

xeddog 

GREATLY abbreviated background information - When I initially installed Jaunty, it came up just fine and I was able to use my dual displays.  I had a lot of "issues" so I decided to try the proprietary 9.1 drivers.  They were better but later on I upgraded to the 9.2 drivers when they came out.  I should have left well enough alone at that point but . . .   Since I was still having some issues I decided to swap video cards with another machine I have.  So I installed an Nvidia 6200 series card.  Took a couple of days, but I got it working.  At that point, I thought that the ATI card might have been a little better so I switched them back.  This time, however, I neglected to remove the nVidia drivers first.  Holy crap!  I have been fighting this for three days now.  I got the nvidia drivers removed and have been installing and removing ATI drivers trying to get SOMEthing to work.  Open source, 9.1, 9.2, 9.3.   Most of the time I get a hung machine with horizontal bands across the display.  Sometimes with two Ubuntu splash screens above and narrow bands below, or just a whole screen full of wider bands.  This last install of the open source drivers seems to be holding.  It has been quite a learing experience. :lolflag:

---

### Post by xeddog on 2009-04-16
I figured it out.  I just had to use the Compiz Fusion Icon to select the window manager.  I think it must have enabled the desktop effects too because now System>Preferences>Appearance>Visual Effects shows  "Custom" instead of "None".

xeddog

---

### Post by alphacrucis2 on 2009-04-16
I recently installed the Jaunty Beta on a laptop with a HD3400 mobility graphics. The open source driver doesn't seem to provide support for desktop effects with this, so I tried the proprietary driver. The performance turned to custard so I backed out to the open source driver. I can live without the compiz stuff so I don't mind to much.

---

### Post by PGHammer on 2009-04-17
> **amirman said:**
> that's because 9.3 doesn't work with the new xserver that jaunty uses. you could try 9.4 (it works with the new xserver) if you find it in the repos, it's an experimental version but i've heard it works well for certain ati cards. unfortunately it doesn't work with mine. good luck.

I have the HD3450 (which 9.4 supports VERY well, thank you).  The issue with 9.4 is not just the new xserver, but the newer kernel.  Generally with most Linux distributions, new kernel + new xserver = teething issues, even with current drivers (usually because of a change in either the kernel or xserver that the driver dev couldn't take into account).  For me, 9.4 works loads better in Jaunty than the radeonhd driver does.

---

### Post by keypox on 2009-04-17
> **PGHammer said:**
> I have the HD3450 (which 9.4 supports VERY well, thank you).  The issue with 9.4 is not just the new xserver, but the newer kernel.  Generally with most Linux distributions, new kernel + new xserver = teething issues, even with current drivers (usually because of a change in either the kernel or xserver that the driver dev couldn't take into account).  For me, 9.4 works loads better in Jaunty than the radeonhd driver does.

How do i install 9.4? 

My hd 4870 is running terrible on 9.04 and my laptop is running terrible as well. 

Both having issues with xorg using 100% of 1 cpu core. [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309776](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/309776)

The beta ran better on both. This is big time fail,

---

### Post by alphacrucis2 on 2009-04-17
> **alphacrucis2 said:**
> I recently installed the Jaunty Beta on a laptop with a HD3400 mobility graphics. The open source driver doesn't seem to provide support for desktop effects with this, so I tried the proprietary driver. The performance turned to custard so I backed out to the open source driver. I can live without the compiz stuff so I don't mind to much.

I had another go at the fglrx driver. Somehow I managed to put X into a frozen state. Had to remove the package from the recovery console. I did some reading and noted that it was suggested to do:

```
sudo aticonfig --initial -f
```

before rebooting but after enabling the fglrx driver via the Hardware Drivers gui.

Well this seemed to work and I was able to enable desktop effects although the performance does seem degraded versus what I had with Intrepid. I also tested with an OpenGL app running (googleearth). Compiz still not compatible with OpenGL apps. Anyway I found another interesting way to blow up X. Try disabling desktop effects while googleearth is running. Fun stuff:biggrin:

I don't really care about desktop effects in any case but one thing the proprietary driver does for me is that it correctly handles my laptop connected external display which didn't work properly with the opensource driver (kept screwing up the resolution and positioning). I also notice that the opensource driver did not list the proper resolution of my laptop display as an option. The fglrx driver defaults it to 1280 by 800 which is correct. The opensource driver doesn't even have that as an option and forced me to use 1280 by 720 which is wrong for the display. I would say that the opensource radeon driver still has a ways to go.

---

### Post by Threedays on 2009-04-18
Worked for me too.  thanks.

---

### Post by DougieFresh4U on 2009-04-18
I cannot get my ATI Radeon HD 3200 to do any thing. Can not get 'desktop Effects'.
Using the .30rc2 kernel
```
dougie@DougiesLeanMachine:~$ sudo aticonfig --initial -f
sudo: aticonfig: command not found
dougie@DougiesLeanMachine:~$ 
```

---

### Post by ktp on 2009-04-18
> **DougieFresh4U said:**
> I cannot get my ATI Radeon HD 3200 to do any thing. Can not get 'desktop Effects'.
Using the .30rc2 kernel
```
dougie@DougiesLeanMachine:~$ sudo aticonfig --initial -f
sudo: aticonfig: command not found
dougie@DougiesLeanMachine:~$ 
```

Seems like drivers not installed correctly. Try purging and letting Ubuntu install them.

---

### Post by DougieFresh4U on 2009-04-18
> **ktp said:**
> Seems like drivers not installed correctly. Try purging and letting Ubuntu install them.

Thanks for reply.
Not sure how or what to purge and don't want to bork machine. Any help would be great

---

### Post by nick09 on 2009-04-18
I can't even login to Jaunty(64-bit). I'm currently using a ATI HD3450 video card(ASUS AH3450/HTP/256M) on my Compaq Presario SR1226NX with 2GB DDR RAM and Athlon 64-bit processor@2.2GHz. I'm willing to bet that the live CD does not have the correct drivers. You can see a example of the login screen below in the attachment. I tested Jaunty in a full install.

---

### Post by markbuntu on 2009-04-18
You need to install in safe graphics mode, get all the updates and then try a driver. This has been going on with my HD3650 since alpha4.

---

