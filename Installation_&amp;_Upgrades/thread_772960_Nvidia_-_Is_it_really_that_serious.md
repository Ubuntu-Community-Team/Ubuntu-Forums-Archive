---
title: "Nvidia - Is it really that serious?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2008-04-28
There are a lot of people having trouble with upgrades to Hardy & Nvidia hardware, but some very wise forum members have pointed out that people who are happy with their install/upgrade will probably not post about their successes - SO...

In an effort to maybe highlight any issues that actually *are* serious, and perhaps debunk some that aren't, i'm asking ALL upgraders of Hardy to tell us what their Nvidia experience has been.

FYI - I went back to Gutsy, having failed to fix my Nvidia problems.

---

### Post by Pumalite on 2008-04-28
I have 4 installations of Hardy; 32 bit and 64 bit in clean installs and they are all working great.

---

### Post by malfist on 2008-04-28
What is it with people claiming, "a lot of people with X bug..." when they are the only one? I'm running the beta still (gonna upgrade this week) and have no issues with the driver.

---

### Post by IT-Joker on 2008-04-28
Well, for me the driver didn't work with the 2.6.22-14 kernel. When I tried to enable it, it just dropped me to 800x600 resolution and after restart it disabled the driver again.

But when I managed to get past the SATA bug and make the 2.6.24-16 kernel run, the driver works without any problems.

So, which of the options is it for me?

---

### Post by chek2fire on 2008-04-28
I think it is and they must fix this bug.

---

### Post by Pumalite on 2008-04-28
The 2.6.22-14 kernel is Gutsy, which, for me, works great too.

---

### Post by siulca on 2008-04-28
The driver works in my laptop but has stopped detecting my external DVI monitor since the upgrade to Hardy. And because the driver doesn't detect the monitor, there's no tweek or configuration that will fix it. 

So [COLOR="DarkRed"]**for me upgrading to Hardy has been a step back**[/COLOR] as I've had the external monitor working for at least the past two releases. [COLOR="DimGray"]Also my network card didn't work out of the box (rendering the computer offline) but that's another long long story.[/COLOR]

---

### Post by Pumalite on 2008-04-28
Try a clean install. It works every time.

---

### Post by Tweak42 on 2008-04-28
7.10 to 8.04 is the 1st time I've done a Ubuntu download upgrade.  Everything except video got dropped to the vesa driver.  One weekend of aggravation and I fixed it after uninstalling all the nvidia stuff in synaptic, adding the grub kernel entries that weren't changed in the upgrade and using envyng to uninstall then install drivers.  Was a learning experience I hope not to repeat.

---

### Post by transisco on 2008-04-28
I don't have any problems with my nvidia drivers on Hardy. I installed Hardy on as a fresh install and it asked me to download an a nvidia driver. It works fine though the performance doesn't seem to be what I expect. 

With compiz, I do get some unsmooth effects on my 22" and 8600GT.

---

### Post by ShodanjoDM on 2008-04-28
Ubuntustudio 8.04 32bit, upgraded from 7.10. Nvidia 7600GS card.

No problem here.

---

### Post by adi_8079 on 2008-04-28
I have no problems with my nvidia card on Hardy 64-bit (runs on a Thinkpad T61p with Quadro Fx 570M). I installed the driver (169.12) with the Envy tool and got extra visual effects running perfectly :guitar:

---

### Post by alexsabree on 2008-04-28
No one is getting the unfixable compiz-fusion colored shadows?

I've tried doing a fresh install, different drivers. Its got to be my graphics card (8800gt) :(

---

### Post by Xiong Chiamiov on 2008-04-28
Upgraded through adept to Kubuntu Hardy with no problems, as far as video drivers go (I had some other issues, with telinit random disappearing and such).  I also did a fresh install of Xubuntu Hardy on my fileserver (it was doing some rather odd things), and, with a few tweaks, it's working great.  It's semi-headless, as I do have an old FX 5200 with s-video out to our tv for watching videos sometimes.  I could never get the NVIDIA driver to work before (had to use vesa), but now I can, so I'm happy.

---

### Post by nschubach on 2008-04-29
I can get the desktop to look fine, but for some reason I cannot get XGL to load even though it's configured in xorg.conf  I've tried Envy, nv, and now I'm trying binary NVidia drivers if I can figure out how to get GDM shutdown to keep X from reloading on another display!!

8800GT EVGA 512MB 64-bit Hardy

---

### Post by yodermk on 2008-04-29
Works fine here.  Have a laptop with a 7600 + external display.  Configured it as a dual monitor setup under Feisty and it kept on working with Gutsy and Hardy.  No changes or fixes at all.

I hate proprietary kernel modules with a passion, but put up with it for now because I need direct rendering and there's no other choice on this laptop.  And, pragmatically, it does Work Well(tm), excluding Freedom-related issues.

---

### Post by greenm1981 on 2008-04-29
Since I was using NVIDIA's proprietary driver in Gutsy, I forgot that I would need to upgrade it manually when I went to Hardy.

Currently everything is working fine.  Initially I tried to use EnvyNG, with disastrous results. It wasn't until I purged my system of envy, all nvidia restricted drivers, and ran: sudo apt-get install nvidia-kernel-source nvidia-settings that I was able to successfully install the NVIDIA drivers again.

In my case, it was impatience that screwed up my NVIDIA.

---

### Post by NEUR0M4NCER on 2008-04-29
> **malfist said:**
> What is it with people claiming, "a lot of people with X bug..." when they are the only one? I'm running the beta still (gonna upgrade this week) and have no issues with the driver.

I most certainly was *not* the only one, but re-read the first post - heck, look at the poll options - and you'll see that in no way am I dumping on you, Ubuntu, its devs or anything else. Chill out man - i'm just trying to *find out **if*** (rather than assume **that**) there are many people with this problem. A legitimate question to ask, I think.

I'm happy for you if your install works perfectly - but just as you think I might be isolated, and the only one having problems... perhaps YOU'RE the only one with a perfect install? Works both ways, huh?

Regards


*edit*

ALSO - if you look at the questions, you should guess that I have in fact seen all of these in one thread or another, whilst trying to fix my own problem. This isn't just blind guessing.

---

### Post by JasonBr on 2008-04-29
When using the 169.xxxxxx driver I get a bright grey screen with random white lines on it.  When installing any other version of the driver, I get "low graphics mode".

Dell Vostro 1500
Nvidia 8400M GS

---

### Post by perlluver on 2008-04-29
I have two computer running 8.04 and they both have Nvidia cards, My box has a Nvidia Geforce FX 5500, and my wife's box has a Geforce MX 4400, I believe and they both installed fine with the restricted drivers.  Although I did have to fix the resolution on my wifes box, it was at 640 by something.

---

### Post by wkulecz on 2008-04-29
Geforce FX 5500 here.  Worked perfectly on fresh install even picked up 1920x1200 resolution.  Actually the nv driver worked well enough I thought the restricted driver was used by default until I tried turning on desktop effects.

Desktop effects lasted about two minutes before I decided they were useless claptrap.

--wally.

---

### Post by zebog13 on 2008-05-07
> **ShodanjoDM said:**
> Ubuntustudio 8.04 32bit, upgraded from 7.10. Nvidia 7600GS card.

No problem here.

how did you get it working 
1)Clean install I get one perfectly good screen, and the other states input not supported"
2)Install Nvidia driver from restricted drivers: 2 screens cloned wth max 600x480 resolution
3)Install nvidia driver from website input still not supported error on one screen and i lose signal on the other

---

### Post by DocBob on 2008-05-08
Yes, it IS that serious. I tried Hardy, As well. My Graphics worked fine, after adding restricted drivers and tweaking a bit. But, I had no alsa support for my sound card so, i reverted back to Gutsy, as well.

---

### Post by uberlinux on 2008-05-08
8.04 blows if you have an nvidia card.  Not even 'dpkg-reconfigure xserver-xorg' can help me now!

---

### Post by darc on 2008-05-08
8600GT (512MB dual head), x64 system.

Works well after tweaking (about 5hrs).

I briefly tried Compiz, with failed results, but my dual monitor (TwinView) setup is working and I'm getting 6,000FPS on glxgears.  I never used Compiz/Beryl back in Gutsy when I had it working right anyway, so I'm not worried about that "claptrap" as it was labeled above : )

One bug I haven't fixed yet (but haven't assigned it to be "unfixable") is that GDM crashes when using GL screensavers.  For the moment I've just assigned that the "don't care, I just won't use those screensavers" solution, since all the standard stuff is working to my satisfaction.

-darc

EDIT:  I can't say I was surprised though, the core Linux stuff is almost always peachy, but video drivers are always a bitch.

---

### Post by Alpha1Dash1 on 2008-05-08
I've got two PCs, each with a Nvidia 7900GTX in. In one is an Intel Core2Quad, the other an AMD X2. Both were running 7.10 (32bit) with the nvidia drivers installed via Envy. Both were upgraded via Upgrade Manager.

The first machine (my main one thankfully!) upgraded with only one small hitch (a sudo thing). I had un-installed the drivers first using Envy and when the upgrade was done (and the sudo thing fixed), re-installed the drivers using EnvyNG. All worked (and is working) fine.

The second PC I upgraded last weekend, and that is quite a different story. I followed exactly the same procedure, but can't get the restricted or nvidia drivers to load. Luckily the lack of HW acceleration is not a real prob on this PC, since its been downgraded to "the wife's internet shopping PC", but something weird is definitely going on.

---

### Post by Master Orion on 2008-05-08
I have a 64-bit build of kubuntu kde4 remix.  The nvidia drivers installed themselves in a fashion that was much easier than previous installs.  Everytime a new distro comes out, I do a fresh install - I seem to always get better results that way.  

This is the first time I didn't need to run the reconfigure utility or edit xorg.conf out of the box, nicely done.

---

### Post by karlatsaic on 2008-05-09
I can ALMOST get the drivers which get loaded with EnvyNG to work. It took me 3 days of fiddling and sweating, so it's not as easy as it may look. 

I had to do the following:
1. Uninstall everything (from both EnvyNG as well as disable restricted driver).
2. Install nvidia driver (auto-detect) via EnvyNG
3. Enable nvidia restricted driver (System/Adminstration/Hardware Drivers)
4. cp an OLD (prior to Hardy xorg.conf) - without that, 800x600 and 640x480 were the only available resolutions.

Everything works fine except my Matlab desktop and all windows are completely blank, so reverting to nv driver. I'm also registering the situation with the Mathworks, but putting details here to help get this mess straightened out.

I have Hardy 8.04 (7.10 upgrade) on a Dell Latitude D800 with "Nvidia Geforce4 4200 Go AGP 8x" card. My xorg.conf is listed below. I would like everything to return to normal as everything else with the Hardy upgrade went flawlessly for me.

contents of xorg.conf:
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-96
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1200"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by karlatsaic on 2008-05-09
Actually, this was not really a Hardy/nvidia issue after all. I just upgraded to the latest Matlab r2008a on linux and now my restricted driver is working just fine. In fact, I removed ALL the EnvyNG stuff and just went with the standard Ubuntu restricted driver (which seemed to be the same driver anyway just without the ~150MB of kdelibs, etc. that EnvyNG required) - same xorg.conf as in post above. VERY HAPPY with Hardy + nvidia now, but the upgrade could have gone smoother, if it had only disabled my restricted driver during the upgrade and provided a clean xorg.conf during the upgrade.

---

### Post by Coert on 2008-05-09
I've had to remove the nvidia-kernel-common package and recompile the latest drivers directly from the nvidia website to get my GeForce 8500 GT fired up. After that it worked like a charm, compiz and all. 

Can't get my soundcard ( AD1988 ) to work in ALSA though :(

---

### Post by toasterboy1 on 2008-05-09
Compaq Presario V6133CL
Nvidia Geforce GO 6150

Tried EnvyNG and nvidia binary installer. After reboot would get dropped to commandline. Ended up having to do the following:
sudo apt-get remove nvidia*
sudo sh ./NVIDIA-Linux-x86_64-169.12-pkg2.run

because the output from dmesg had something related to different versions of driver and module loaded. Worked after reboot. A little worried about the 8 packages that were removed. Like linux. But so far so good.

Update:
No ttys with 169.12 and would not resume. Went back to driver 96.

---

### Post by NEUR0M4NCER on 2008-05-12
Well so far, around 28% of voters have unresolveable issues with Nvidia. I know that this is STILL a biased number, as people with working gfx will probably not even find this thread (or even come onto the forums?), but still, it seems  a lot of people to me.

On the plus side, my Hardy AMD64 disc arrived in the post today, so if I DO need to do a fresh install, I can use an official disc (yay! kudos to Canonical!).

Hopefully, these results will be seen by the people who do all the hard work for us, and fixes will be just 'round the corner. Thanks all for voting, good to see so many with working setups.

Regards to all

---

### Post by Ghaarnok on 2008-05-12
Running 512MB Zotac 8800GT AMP! Edition.

After installing hardy heron (clean install) I then installed envyNG to install the latest drivers. Everything seems to work fine apart from a couple of things:

Dual screen: It seems to be disabled by default so after installing the drivers I ran "nvidia-settings" and enabled my second monitor. Works a treat now.

Pink or yellow shadows on all window borders. As far as I'm aware this is a recognised problem so I'm going to have to wait for a fix. In the meantime, if I right click the Desktop -> Change Desktop Background -> Click Theme Tab and then select a different theme, then re-select the theme I use it seems to get rid of the problem temporarily

Another gripe is that 3D performance is a little lackluster. I'm getting way higher FPS in XP than I am in Hardy Heron.

Other than that it wasn't too painful to get set up.

---

### Post by RichardG891 on 2008-05-12
Just found this thread (and voted). Had no problems with integrated NVidia on my HP laptop or with my XFX 7900GS.... OpenGL and video playback all smooth-running. I installed Hardy from fresh (had serious issues upgrading from Feisty to Gutsy last time around).

---

### Post by Yannick Le Saint kyncani on 2008-05-12
Hi there,

I'm using the nv driver because i don't need the 3d so I haven't bothered with the nvidia drivers.

My answer to the poll was "Barely works, many unfixable bugs, or fell-back to nv driver". AFAIK, the nvidia drivers were working in gutsy (except for the console mode ...).

---

### Post by darkjesus721 on 2008-06-04
Hey this is my first post so sorry if i haven't abide to the rules but i thought i could shed some light on this. I'm not to great with linux yet this has been my first couple of months using it. i was using 7.10 gutsy have a dell optiplex 745 don't think u really need to know this so im gonna get straight to the point. any way so i have a geforce 8800 gt and i had compiz working great in 7.10 have done an much needed upgrade last night and woke up to a few things being wrong. firstly my login was all blurred like stripes across the screen an multi mouse pointers. managed to sort this problem by editing my xorg.conf and commenting out the lines starting with virtual save then restarting gnome with ctrl+alt+backspace. next when i logged in i notice compizy wasn't working tried to enable it and says cant enable. i then realized there was a nvidia-glx-new update to be installed so downloaded and assumed installed but tried to start compiz again and no such luck. after looking in the forum i came across this blacklisted section and there was some cmd line shell script which said would disable some checks so tryed to enable compiz again, again nothing. then realized there was something called compiz check ran this but it said checks disabled so i have a feeling the shell disabeled something to do with compiz checks. so i have sorta run out of ideas any one got any ideas to point me in the right direction. even just some key words would be enough as im not scared of learning things for my self. cheers jamie :D:D

---

### Post by NEUR0M4NCER on 2008-06-05
Hi darkjesus721 - welcome to the forums.

Unfortunately, I had just as many problems as you did (more maybe), and simply couldn't get them fixed. The only way I could get everything working was with a fresh install...

I never found out if there is an alternative to the old Xorg reconfigure option from Gutsy, but from what I can tell there isn't - an X developer says over on [Ubuntu Brainstorm](http://blog.qa.ubuntu.com/node/9) that by the time a new application to reconfigure X could be written, they hope to have fixed all the problems it would solve anyway, so are not working on it.

... so yeah. I highly recommend a fresh install. It restored my confidence in Ubuntu, and I shall never do a release upgrade again, unless something drastic changes in the way it's done.

Hope you get things going again - let us know how it goes.

Regards

---

### Post by ShadowWraith on 2008-06-19
I only upgraded to hardy because LTS didn't have the correct version of gtk for Firefox 3... And now I'm starting to regret it because I've been working to get my drivers in order for 4 hours now. I'm having trouble with removing the old nvidia-glx in favor of nvidia-glx-new, and nothing requiring OpenGl will work...

---

### Post by darkoblivion on 2008-06-22
Hey guys,

also a n00b here, but been running Ubuntu 7.10 GG for about a year now on this self built computer with a nvidia 6600GT.

Had a few problems with resolution since upgrading this afternoon to HH... browsed through a crapload of forum threads before I found what I needed but everything worked out fine. I remember spending a lot more time when I first installed GG to get compiz to work. Now my only issue left is finding out where all my icons on my Desktop disappeared to and why I can't right click on my desktop at all....

But otherwise, I'm pretty happy with this release. As long as the bugs aren't overwhelming, I think it's kind of intriguing to fix some bugs in a new release for yourself. I mean, unless you keep digging yourself into a bigger and bigger hole... 

Anyway isn't that why we use linux and not windows? So we can have a little more control over our own systems and take advantage of the power and versatility that Ubuntu has to offer? Any release of a newer OS is going to prompt a lot of people who are unhappy with performance and bugs but I'd like to applaud the efforts of the open source community and developers for making my PC experience more enjoyable.

---

### Post by MarilenCorciovei on 2008-10-31
I've did a [clean install]("http://www.len.ro/2008/10/ubuntu-intrepid-ibex/") and I'm having no visible problem with the restricted Nvidia driver (using the 177 version).

---

