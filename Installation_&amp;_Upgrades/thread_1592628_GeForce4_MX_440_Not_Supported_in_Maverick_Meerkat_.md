---
title: "GeForce4 MX 440 Not Supported in Maverick Meerkat 10.10 Upgrade?"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2010-10-10
Hi,

I updated my Dell Dimension 8300 from 10.04 this morning. I tried to boot up after the restart, and got pages and pages of text. So I did a bunch of research here and elsewhere all day long..

I tried Startx command at the prompt
[username]@username-desktop:~$

And got the typical error messages I have seen posted...
Basically:
(EE) Failed to load /usr/lib/xorg/extra~modules/nVidia-drv.so
(EE) Failed to load module "nvidia" (loader failed, 7)
(EE) No drivers available
Fatal server error: no screens found
Please consult the  The X.Org FOundation support at [http://wiki.x.org](http://wiki.x.org) for help
Please also check the log file at "/var/log/Xorg.0.log" for additional information

ddxSigGiveUp: Closing log
Xinit: No such file or directory (errno2): unable to connect to X server
X init: no such process (error 3): server error

So I used grub and a lower version to log in after rebooting.
I used the lower graphics and got the screen. I uninstalled and re-installed 
nvidia-current
Then rebooted. 
Same problems. :confused:
I searched the Nvidia site and according to their site 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
"The following GPUs are no longer supported in the regular NVIDIA Unified  UNIX Graphics Driver. Instead, these GPUs will continue to be supported  through special "Legacy GPU" drivers that will be updated periodically  to add support for new versions of Linux system components (e.g., new  Linux kernels, new versions of the X server, etc)."

The version apparently that will support my card is **The 96.43.xx driver**
They also recommend using the open source version supplied in the distribution.

So my question is...

1. Is there such a driver existing or coming for Maverick Meerkat 10.10
Or...
2. If not, is there a good work around anyone can suggest.

Thanks for your help and advice... I have been at this since 9am and it is now 8:18 pm
It's kind of frustrating if you know what I mean.

---

### Post by efflandt on 2010-10-10
Apparently nvidia 96 and 173 did not work with the new 1.9 X server earlier.  Not sure if the 173 version that now works is in the repos yet, but I they are still working on the 96 version.  So it should be available eventually.

Until then you will have to use whatever works nouveau or nv.

---

### Post by LaughingHorse on 2010-10-11
Hi efflandt,

Thank you for your reply.

How would I use nouveau or nv
I know some things, but am not familiar with these terms.

Right now I am able to log in and getting a really sucky resolution.
I had a look at NVIDIA X Server settings in 
System > Preferences and got the following message:

"ubuntu maverick You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I am totally confused at this point. And if there is an update coming, and I modify settings now then when the update comes will I be in bad shape and have to change all sorts of settings manually?

Thanks in advance for any advice and/or insight.

---

### Post by spcagigas on 2010-10-11
I'm seeing the same error message -- I'm also running the GeForce4MX440 on an older Dell.  I rolled back to 10.04, and the -96 driver loads and runs OK again.  I guess I'll hold off on upgrading back to 10.10 until I hear that the legacy GPU drivers are running OK.

Or, I break down and buy a new graphics card for my ancient PC... nah.

---

### Post by dreamCatalyst on 2010-10-11
I'm experiencing the same problem here.
The guy at Nvidia said he's working (or gonna, can't really tell) on the 96-drivers. [http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5](http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5)

---

### Post by antoinem01 on 2010-10-11
Might not be perfect but good enough for me:

sudo su to become root
run nvidia-xconfig (this was in: /usr/lib/nvidia-96/bin/nvidia-xconfig)
go into /etc/X11/xorg.conf - I used vi
modify driver from nvidia to nv - in my case this was on line 94
save file
run startx
when ok - reboot machine - should go straight into your x-windows session

Resolution either 1600X1200 or 1400X1050
Screendept 16

Machine is a Dell Latitiude 840C

---

### Post by jakell on 2010-10-11
> **dreamCatalyst said:**
> I'm experiencing the same problem here.
The guy at Nvidia said he's working (or gonna, can't really tell) on the 96-drivers. [http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5](http://www.nvnews.net/vbulletin/showpost.php?p=2326233&postcount=5)

This is the wrong way around, it's not Nvidia's problem.
The drivers are ok, they worked fine, it's Maverick that's the problem, or more accurately, Xorg.

---

### Post by ekd on 2010-10-11
> **antoinem01 said:**
> ...
run nvidia-xconfig (this was in: /usr/lib/nvidia-96/bin/nvidia-xconfig)
go into /etc/X11/xorg.conf - I used vi
modify driver from nvidia to nv - in my case this was on line 94
save file
...

This worked out great for me. I have an old MX 440 and just a little change to the driver name is all it took.

THANK YOU

---

### Post by xingular on 2010-10-12
> **antoinem01 said:**
> Might not be perfect but good enough for me:

sudo su to become root
run nvidia-xconfig (this was in: /usr/lib/nvidia-96/bin/nvidia-xconfig)
go into /etc/X11/xorg.conf - I used vi
modify driver from nvidia to nv - in my case this was on line 94
save file
run startx
when ok - reboot machine - should go straight into your x-windows session

Resolution either 1600X1200 or 1400X1050
Screendept 16

Machine is a Dell Latitiude 840C


Not working for me :( GeForce 3 Ti 200
When I run startx I see this:*


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

*ddxSigGiveUp: Closing log



Reboot, and I still haven't desktop effects.

---

### Post by MonsterTrimble on 2010-10-12
> **spcagigas said:**
> I'm seeing the same error message -- I'm also running the GeForce4MX440 on an older Dell.  I rolled back to 10.04, and the -96 driver loads and runs OK again.  I guess I'll hold off on upgrading back to 10.10 until I hear that the legacy GPU drivers are running OK.

I knew there was a reason I was holding off on Maverick for a while. I ran into the same issue on Maverick beta and although I would really like to get my hands on Lubuntu-core for my Medion 2900 (rebadged Gateway m500) I'm not willing to sacrifice stability and a decent resolution for new hotness. 

I kinda got tired of the upgrade breakages. Can you tell?

---

### Post by Yougo on 2010-10-12
> **xingular said:**
> Not working for me :( GeForce 3 Ti 200
When I run startx I see this:*


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

*ddxSigGiveUp: Closing log



Reboot, and I still haven't desktop effects.

remove /tmp/.X0-lock ...hmm, could work :)
rather, you could rename it and put it back if it didn't do the trick

---

### Post by Slim Odds on 2010-10-12
How long do you guys expect ancient hardware to be supported by **new OS's**?

I have one of these graphics cards in a system at home and that also has an 800MHz Pentium III processor and 768MB of RAM (maxed out). It's still running 8.04.

At some point you have to hang it up and move on.

It's so old that here are the supported Windows OS's:
[INDENT][I]WHQL-certified for Windows XP, Windows
Me, Windows 2000, Windows NT, and
Windows 98[/I]

[/INDENT]Here's what you'll see at the bottom of the data sheet for this device:
[INDENT]Registered trademark NVIDIA® Corporation, 2002. 4 x 4 Evo 2 copyright 2001
[/INDENT]So I'd highly recommend newer hardware or an older OS.

---

### Post by CampbellBoyd on 2010-10-12
> **antoinem01 said:**
> Might not be perfect but good enough for me:

sudo su to become root
run nvidia-xconfig (this was in: /usr/lib/nvidia-96/bin/nvidia-xconfig)
go into /etc/X11/xorg.conf - I used vi
modify driver from nvidia to nv - in my case this was on line 94
save file
run startx
when ok - reboot machine - should go straight into your x-windows session

Resolution either 1600X1200 or 1400X1050
Screendept 16

Machine is a Dell Latitiude 840C

Worked for me! Thanks so much - I was getting near to thinking about going back to Windows [pause to bang head off desk] but now I can wait for the driver update and use my PC.

---

### Post by dreamCatalyst on 2010-10-12
I successfully downgraded X to the version in Lucid (1.7). 
Works like a charm for me. No problems with 3D or resolutions.
Besides X everything is just like a **new os** :P

If anyone wants to know how...post a request in this thread, I'll see what I can do to reproduce the steps.

---

### Post by Slim Odds on 2010-10-12
> **CampbellBoyd said:**
> Worked for me! Thanks so much - I was getting near to thinking about going back to Windows [pause to bang head off desk] but now I can wait for the driver update and use my PC.

That's because 'nv' is a generic open source NVidia driver that supports 2D.

So if you don't need 3D, that should work just fine.

---

### Post by xingular on 2010-10-12
> **dreamCatalyst said:**
> I successfully downgraded X to the version in Lucid (1.7). 
Works like a charm for me. No problems with 3D or resolutions.
Besides X everything is just like a **new os** :P

If anyone wants to know how...post a request in this thread, I'll see what I can do to reproduce the steps.

Please... Request here. I'm very noob... 

I don't have any resolution problem. I need 3D only. For desktop effects, Google Earth... With "nv" would have 2d only. 

GeForce 3 Ti works with nvidia-96?

---

### Post by dreamCatalyst on 2010-10-12
> **xingular said:**
> Please... Request here. I'm very noob... 

Disclaimer: this is what I did, it worked for me, it might not for you. This could break your system.

So here's what I did. First off I used Synaptic to force and lock the versions for all the xserver-xorg packages. Synaptic requires a gui (duh) so a working X with the nv drivers is needed.

step 1) If you have an /etc/X11/xorg.conf file (you shouldn't) back it up now.
step  2) Add the following repositories to /etc/apt/sources.list:
```
deb http://en.archive.ubuntu.com/ubuntu/ lucid main
deb-src http://en.archive.ubuntu.com/ubuntu/ lucid main
```step 3) Update the repositories
```
sudo apt-get update
```step 4) Purge xserver-xorg:
 ```
sudo apt-get purge xserver-xorg
```step 5) This step requires a bit of work. Fire up Synaptic, search for xserver-xorg, sort by name.
For pretty much each xserver-xorg package with the Ubuntu logo you'll want to "Force Version" (Ctrl+E) and select the Lucid version. Then choose "Lock version".
If Synaptic wants to mark other packages choose Cancel each time otherwise you'll simply get an error-message that it can't/won't be able to install.

For completeness here is the list of packages and their versions I locked.
I wanted to do this step with some script-fu but couldn't figure out a good way to lock (pin) the packages. Maybe someone else can make a suggestion.
```

xserver-xorg=1:7.5+5ubuntu1
xserver-xorg-core=2:1.7.6-2ubuntu7
xserver-xorg-input-evdev=1:2.3.2-5ubuntu1
xserver-xorg-input-mouse=1:1.5.0-1
xserver-xorg-input-vmmouse=1:12.6.5-4ubuntu2
xserver-xorg-input-wacom=1:0.10.5-0ubuntu4
xserver-xorg-video-apm=1:1.2.2-1
xserver-xorg-video-ark=1:0.7.2-1
xserver-xorg-video-chips=1:1.2.2-1
xserver-xorg-video-cirrus=1:1.3.2-1ubuntu1
xserver-xorg-video-fbdev=1:0.4.1-1ubuntu1
xserver-xorg-video-geode=2.11.8-4
xserver-xorg-video-i128=1:1.3.3-1
xserver-xorg-video-i740=1:1.3.2-1
xserver-xorg-video-intel=2:2.9.1-3ubuntu5
xserver-xorg-video-mga=1:1.4.11.dfsg-2ubuntu1
xserver-xorg-video-neomagic=1:1.2.4-2
xserver-xorg-video-nv=1:2.1.15-1ubuntu3
xserver-xorg-video-radeon=1:6.13.0-1ubuntu5
xserver-xorg-video-rendition=1:4.2.3-1
xserver-xorg-video-s3=1:0.6.3-1
xserver-xorg-video-s3virge=1:1.10.4-1
xserver-xorg-video-savage=1:2.3.1-1ubuntu1
xserver-xorg-video-siliconmotion=1:1.7.3-1
xserver-xorg-video-sis=1:0.10.2-2
xserver-xorg-video-sisusb=1:0.9.3-1
xserver-xorg-video-tdfx=1:1.4.3-1
xserver-xorg-video-trident=1:1.3.3-1
xserver-xorg-video-tseng=1:1.2.3-1
xserver-xorg-video-v4l=1:0.2.0-4
xserver-xorg-video-vesa=1:2.3.0-1ubuntu1
xserver-xorg-video-vmware=1:10.16.9-1
xserver-xorg-video-voodoo=1:1.2.3-1
```step 6) Reinstall xserver-xorg
```
sudo apt-get install xserver-xorg
```You should now see a list of packages it wants to install. Verify that these are the "older" (Lucid) versions and then go ahead.

step 7) After restarting X you should be done, if the nvidia-driver won't load you might want to try running:
```
sudo nvidia-xconfig
```> **xingular said:**
>  GeForce 3 Ti works with nvidia-96?
Not sure but I think so. Use google for this one ;)

---

### Post by LaughingHorse on 2010-10-12
> **Slim Odds said:**
> How long do you guys expect ancient hardware to be supported by **new OS's**?

Till the hardware dies. Why throw out a perfectly good working piece of hardware?

Wasn't part of the promise of Linux you could run it on old "obsolete hardware?"

The problem I am experiencing is really weird. Now, sometimes when I boot up, everything seems fine. Other times I get a page full of lines of text and a command prompt.

And everything did work perfectly in Lucid.

A suggestion for any developer of Ubuntu "listening" why not add a routine in upgrades that searches the existing hardware and lets the person upgrading know of potential conflicts before they do the upgrade, and possibly ways to get around it for the time being?

---

### Post by cascade9 on 2010-10-12
> **Slim Odds said:**
> How long do you guys expect ancient hardware to be supported by **new OS's**?

I have one of these graphics cards in a system at home and that also has an 800MHz Pentium III processor and 768MB of RAM (maxed out). It's still running 8.04.

At some point you have to hang it up and move on.

It's so old that here are the supported Windows OS's:[INDENT][I]WHQL-certified for Windows XP, Windows
Me, Windows 2000, Windows NT, and
Windows 98[/I]

[/INDENT]Here's what you'll see at the bottom of the data sheet for this device:[INDENT]Registered trademark NVIDIA® Corporation, 2002. 4 x 4 Evo 2 copyright 2001
[/INDENT]So I'd highly recommend newer hardware or an older OS.

A MX440 will run in vista, at least (possibly win7 but I havent tried that). With vista, you HAVE to us the built-in vista driver. BTW, the main reason why there is no offical support for the MX440 is because the MX440 is a DX7 card, vista + win7 need a DX9 cards, but vista with a MX440 worked for me (thats also the reason why the 3Ti and 4Ti card dont have offical vista/win7 drivers, they are only DX8 cards)

10.10 would have no problems supporting the 96.xx drivers right now if it was using xorg 1.8.x, and the 96.xx drivers should get a version that works with xorg 1.9 sooner or later.

---

### Post by Slim Odds on 2010-10-12
> **LaughingHorse said:**
> Till the hardware dies. Why throw out a perfectly good working piece of hardware?

Wasn't part of the promise of Linux you could run it on old "obsolete hardware?"

The problem I am experiencing is really weird. Now, sometimes when I boot up, everything seems fine. Other times I get a page full of lines of text and a command prompt.

And everything did work perfectly in Lucid.

A suggestion for any developer of Ubuntu "listening" why not add a routine in upgrades that searches the existing hardware and lets the person upgrading know of potential conflicts before they do the upgrade, and possibly ways to get around it for the time being?

If you want to run on really old hardware, use really old software.

That "promise" that you speak of can only be taken so far. Should 10.10 also have CGA support?

If you like the way that it worked with Lucid, you should keep using Lucid. It's an LTS and that means that you can use it for a long time.

---

### Post by Slim Odds on 2010-10-12
> **cascade9 said:**
> A MX440 will run in vista, at least (possibly win7 but I havent tried that). With vista, you HAVE to us the built-in vista driver. BTW, the main reason why there is no offical support for the MX440 is because the MX440 is a DX7 card, vista + win7 need a DX9 cards, but vista with a MX440 worked for me (thats also the reason why the 3Ti and 4Ti card dont have offical vista/win7 drivers, they are only DX8 cards)

10.10 would have no problems supporting the 96.xx drivers right now if it was using xorg 1.8.x, and the 96.xx drivers should get a version that works with xorg 1.9 sooner or later.

My point was that even the data sheet shows support only up to Win XP and that by modern standards, this is some pretty ancient hardware.

This idea that every modern linux distro has to support every old piece of hardware gets a little ridiculous at some point.

---

### Post by LaughingHorse on 2010-10-12
> **Slim Odds said:**
> If you want to run on really old hardware, use really old software.

That "promise" that you speak of can only be taken so far. Should 10.10 also have CGA support?

If you like the way that it worked with Lucid, you should keep using Lucid. It's an LTS and that means that you can use it for a long time.

Yeah, I guess you are right. Every time a new release comes out, I'll go buy a new computer just to keep up.

---

### Post by cascade9 on 2010-10-12
> **Slim Odds said:**
> My point was that even the data sheet shows support only up to Win XP and that by modern standards, this is some pretty ancient hardware.

This idea that every modern linux distro has to support every old piece of hardware gets a little ridiculous at some point.

Data sheets can lie ;) 

I can sort of see your point, but lets face it- MX440s, and even older nvidia hardware, works fine in new linux distros. The only 'issue' here is the nVidia proprietary drivers.

---

### Post by Maximus559 on 2010-10-12
> **LaughingHorse said:**
> Yeah, I guess you are right. Every time a new release comes out, I'll go buy a new computer just to keep up.

This. I'm experiencing the same problem with my Geforce4 MX 420, and I have to say I'm pretty disappointed. Couldn't there have been some kind of warning when upgrading, like another poster suggested? This hardware is perfectly adequate for a secondary desktop system. There's no reason why it shouldn't continue to be supported. I guess I'll be going back to 10.04 as soon as I have the time to fool with it. Until then, I'm back on Vista. [facepalm]

---

### Post by tvphil on 2010-10-12
I faced a worse situation after I updated to Meerkat last night, X server wouldn't load at all. After going to recovery mode and switching to the generic driver just so I could see something on my desktop, I found a solution.At the Nouveau wiki [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)

I found after reading through a lot of warnings, if you simply remove whatever Nvidia proprietary driver you are using via Synaptic,then restart, the Nouveau driver that comes pre-installed in Meerkat, takes over after you reboot. So I did and I got my 1400 by 900 full monitor resolution back. The downside, no 3d acceleration (I didn't use it much anyway) and the screen flickers occasionally.The Nouveau driver is also stated in Synaptic as "experimental", so that seems to explain the flickering. I have a 7 year old Gateway running the Geforce 4200ti and it was previously using the NVidia GLX96 driver. I think what I did would probably work for the MX 440 too.

---

### Post by mocoloco on 2010-10-15
> **Slim Odds said:**
> If you want to run on really old hardware, use really old software.

Old software is full of security holes and bugs. The misconception that you must use old software to get the most out of old hardware stems from a proprietary mindset. Eg, if you want to run Windows software on a Pentium II you'll have to use Win98 (setting aside Wine or VM options). The beauty of Linux is you can run new software on old hardware, that's why distros like Puppy are so popular and why there's such an interest in projects like Lubuntu. Especially in less-developed countries where people use "old" stuff in general much longer (computers, cars, appliances, etc).

Anyway, I'm glad to see support is possible. I'll wait for it to come through the repos, for now 2d with the nouveau driver works fine.

---

### Post by cascade9 on 2010-10-17
> **mocoloco said:**
> Old software is full of security holes and bugs. The misconception that you must use old software to get the most out of old hardware stems from a proprietary mindset. Eg, if you want to run Windows software on a Pentium II you'll have to use Win98 (setting aside Wine or VM options). The beauty of Linux is you can run new software on old hardware, that's why distros like Puppy are so popular and why there's such an interest in projects like Lubuntu.

Umm.....apart from Win9X, any version of which would run a Pentium II, Win2K (OK, out of support now) and WinXP will run on a P2 with enough RAM (64MB+). 

A P2 with 512MB is hardly going to be a speed demon with XP, but even a 128MB version would run....slowly, bit it will run. 

Also, IMO, a lot of the reason why lubuntu does get as much intrest as it does is because of xubuntu being far slower and more RAM heavy than it could (should?) be.

---

### Post by Slim Odds on 2010-10-18
> **mocoloco said:**
> Old software is full of security holes and bugs. The misconception that you must use old software to get the most out of old hardware stems from a proprietary mindset. Eg, if you want to run Windows software on a Pentium II you'll have to use Win98 (setting aside Wine or VM options). The beauty of Linux is you can run new software on old hardware, that's why distros like Puppy are so popular and why there's such an interest in projects like Lubuntu. Especially in less-developed countries where people use "old" stuff in general much longer (computers, cars, appliances, etc).

Anyway, I'm glad to see support is possible. I'll wait for it to come through the repos, for now 2d with the nouveau driver works fine.

When I was talking about using "older" software, I wasn't talking about going back to Ubuntu -100. Perhaps using 10.04 might be appropriate since it works with this card and has quite a bit of time left on support.

---

### Post by Leezer on 2010-10-18
Could someone post here again when the nvidia driver has been fixed, so I will know when I can switch back to it?  I am currently using nv as a temporary solution, but it is problematic.  Any video I try to watch (such as youtube) plays as a weird sped-up version.

Also, in order to switch back to the nvidia driver, all I need to do is change "nv" back to "nvidia" in my /etc/X11/xorg.conf file and restart, correct?

---

### Post by owise1 on 2010-10-19
mate - all you should need to do is activate the driver again - system>administration>additional drivers.

---

### Post by Leezer on 2010-10-20
> **owise1 said:**
> mate - all you should need to do is activate the driver again - system>administration>additional drivers.
It says, "This driver is activated but not currently in use."

---

### Post by cascade9 on 2010-10-20
It says that because owise1 is wrong.....for the moment. 

When the 96.xx driver get an version that works with xorg 1.9, then it should work.

---

### Post by owise1 on 2010-10-20
correct cascade9 - I should have been more specific - Leezer should keep an eye out for an update via update manager for nvidia and then enable.  Hopoe that it is not too long a wait.

cheers

---

### Post by cascade9 on 2010-10-21
Hopefully not, but it could take ages.

---

### Post by John Harrington on 2010-10-22
The hardware accelerated nouveau driver works pretty well for me on my GeForce4 MX card.  (Actually, all I use accelerated 3d for is the foobillard billiard simulation, but that works quite well with the nouveau driver.)  The trick is to get the proper hardware accelerated driver for your card.

According to the nouveau website, for nvidia chips from nv30 and up, you need the driver nouveau_dri.so which is in the maverick universe libgl1-mesa-dri-experimental package. For nvidia chips nv20 and earlier, you need nouveau_vieux_dri.so.

I don't think nouveau-vieux-dri.so is in any maverick package in the official repositories. It seems to have been removed from libgl1-mesa-dri-experimental before the maverick final release. However, you don't need to build it. I got it by adding the xorg-edgers ppa repository: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

nouveau_vieux_dri.so is in the libgl1-mesa-dri package (not the experimental package, which I don't need at all). After adding the repository, reloading (using synaptic), installing all updates, and doing a cold reboot (power completely off and then back on), I had accelerated 3d.

To determine which nvidia chip you've got, go here: [http://nouveau.freedesktop.org/wiki/CodeNames](http://nouveau.freedesktop.org/wiki/CodeNames)
GeForce 4 MX card corresponds to the NV10 chip.

---

### Post by I Am Noob on 2010-10-25
> **John Harrington said:**
> The hardware accelerated nouveau driver works pretty well for me on my GeForce4 MX card.  (Actually, all I use accelerated 3d for is the foobillard billiard simulation, but that works quite well with the nouveau driver.)  The trick is to get the proper hardware accelerated driver for your card.

According to the nouveau website, for nvidia chips from nv30 and up, you need the driver nouveau_dri.so which is in the maverick universe libgl1-mesa-dri-experimental package. For nvidia chips nv20 and earlier, you need nouveau_vieux_dri.so.

I don't think nouveau-vieux-dri.so is in any maverick package in the official repositories. It seems to have been removed from libgl1-mesa-dri-experimental before the maverick final release. However, you don't need to build it. I got it by adding the xorg-edgers ppa repository: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

nouveau_vieux_dri.so is in the libgl1-mesa-dri package (not the experimental package, which I don't need at all). After adding the repository, reloading (using synaptic), installing all updates, and doing a cold reboot (power completely off and then back on), I had accelerated 3d.

To determine which nvidia chip you've got, go here: [http://nouveau.freedesktop.org/wiki/CodeNames](http://nouveau.freedesktop.org/wiki/CodeNames)
GeForce 4 MX card corresponds to the NV10 chip.

Hey John Harrington,

I am a complete Ubuntu 10.10 noob and also run a GeForce4 MX card, GeForce4 MX460 to be precise... this solution sounds perfect for me, i'm currently left frustrated because I just want my card to be recognised so that I can change my desktop resolution from higher than 1024x768 and use the Visual Effects that SHOULD be available in the System/Preferences/Appearance tab!

I've tried various other fixes, which have left my system rather buggered because i'm such a noob ha ha... but tried and tried again I have, but your solution sounds like its just what im wanting!

Is there any chance at all that you'd be able to make another post with step-by-step instruction of how to carry out this process - as if I was a complete idiot!? (which I am) :lol:

It would really make my day, and my Ubuntu 10.10 experience... I have posted my own thread regarding this subject here: [http://ubuntuforums.org/showthread.php?t=1605491](http://ubuntuforums.org/showthread.php?t=1605491)

:mrgreen: I Am Noob

---

### Post by John Harrington on 2010-10-25
Hello noob.  I'm not very technically knowledgeable myself.  Anyway, I don't know why you're getting limited screen resolution.  I don't think that should have anything to do with whether or not you've got the 3-D hardware accelerated driver.  The 3-D dri (direct rendering infrastructure) driver is a nouveau component, but with an ordinary Maverick installation you should have the basic nouveau driver installed and working.  It won't give you accelerated 3-D, but should give you the full range of screen resolutions.

To check whether nouveau is loaded, open a terminal. You can do that by clicking the Applications menu, then Accessories > gnome-terminal (or Terminal or xterm, whichever you've got installed).  Then, at the command prompt, type:  modprobe -l nouveau
That should list all the loaded modules containing the word, "nouveau."  Then hit <enter>.  You should see the output:  kernel/drivers/gpu/drm/nouveau/nouveau.ko
If you just get another command prompt without any intervening output, it means you don't have the nouveau driver loaded.  Let us know if that happens.

Otherwise, if you do have the nouveau driver loaded, you should be able to change the desktop resolution by clicking on the System menu, then Preferences > Monitors
I think the available resolutions are limited by the capabilities of your monitor, so just because your card supports a higher resolution doesn't mean the resolution will be available to be selected.  It may help to click the "Detect Monitors" button.  Mine properly identifies my monitor as a 15-inch AOC, and gives me the option of selecting the maximum resolution, which is 1280 x 1024.

Now, assuming you want to go on and try the hardware accelerated nouveau_vieux_dri driver, let me warn you first that I don't think it will let you enable desktop effects.  Even though I've got the driver working for other 3-D applications, I still get a message saying that I need the nvidia proprietary driver when I try to enable desktop effects.  I think that's probably a bug in the desktop effects application, or maybe it's the intended behavior because the developers wanted to avoid crashes resulting from using an experimental hardware accelerated driver.  Anyway, I don't know how to force an override.

Also, let me warn you that the nouveau_vieux_dri driver was not working perfectly for me when I tested several things a few days ago.  The foobillard billiards simulation works very well except that there's a pattern on the tabletop that shouldn't be there.  Google Earth works well, including the 3-D buildings, except that when the view is moved up towards the horizontal and the horizon is about to come into view, the landscape disappears.  The Celestia space simulation works well except for solar illumination, which doesn't show up; planets appear in shadow on all sides.  The Stellarium sky viewer doesn't work at all, but crashes with a error about nvidia.  So at this stage of development of the driver, it's sort of hit and miss as to what will work.

By the way, the package containing the nouveau-vieux-dri driver gets updated every few days-- at least twice since I installed it five days ago-- so what's broken now may be fixed soon.

Here's a step-by-step run-through of what I did to get the nouveau_vieux_dri driver installed:

First, enable the xorg-edgers personal package archives (ppa) (a repository for packages made available by the xorg-edgers group).  There's a warning that these packages are development versions and could cause problems on your system, but they have worked pretty smoothly for me.  You should read the warnings, particularly the instruction about how to reverse the installation of xorg-edgers packages, on the xorg-edgers page: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

To enable the xorg-edgers ppa, enter the following in a terminal:

sudo add-apt-repository ppa:xorg-edgers/ppa

(The smiley face in the preceding line should be : followed by x, but I don't know how to keep this website from converting those two characters to the smiley.)

Then, update all package information, by entering in terminal:

sudo apt-get update

Then, be sure the libgl1-mesa-dri package is installed:

sudo apt-get install libgl1-mesa-dri

If it is already installed, this command will cause it to be updated to the latest version.  If it asks you whether you want to install a package from an untrusted repository, or whether you want to install additional packages, say yes or y.

Then, make sure all other packages are updated to the latest version.  This may be important to ensure that all the xorg-edgers packages are in consistent versions:

sudo apt-get dist-upgrade

Again, if it asks you whether you want to install additional packages or packages from untrusted repositories, say yes or y.

Finally, shutdown the computer to a complete power off, and then restart.  You should have accelerated 3-D graphics in at least some applications.  If you want to be sure to keep the libgl1-mesa-dri package updated, you can run Update Manager (under the Systems menu > Administration) periodically, or set the update notifier to check for updates automatically by going to the Applications menu > System Tools > Configuration Editor > apps > update-notifier.  Make sure auto_launch is checked, and set auto_launch_interval to the number of days you want it to wait between update checks.

---

### Post by I Am Noob on 2010-10-26
Ok.. firstly I would like so send out a **HUGE** thank you to [[COLOR=#d40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104"):KS [John Harrington]("http://ubuntuforums.org/member.php?u=370025"):KS and [christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302"):KS  for their replies and feedback into resolving the issues I have mention  on this thread and two others... nobody forces you to help out of these  forums and your help with me has been **GREATLY** appreciated... Than you :mrgreen:


**My Original Thread:** [http://ubuntuforums.org/showthread.php?t=1605491](http://ubuntuforums.org/showthread.php?t=1605491) 
**[John Harrington]("http://ubuntuforums.org/member.php?u=370025")'s post is in this thread:** [http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)
**[christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302")'s post/thread can be found here:** [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367)


I have not managed to resolve ALL my issues (will ask you another Question at the end of this reply), but here's what I did:

> **cariboo907 said:**
> Nvidia hasn't created a driver for your  graphics card that is compatible with the latest version of Xorg used in  Maverick. The nouveau drivers work quite well on even newer graphics  cards. To get 3D you need to install libgl1-mesa-dri-experimental, it is  in the repositories.

I took this advice and did install libgl1-mesa-dri-experimental from my  repositories within System>Administration>Synaptic Package Manager  but unfortunately this did not solve my issue, I was still unable to  activate Visual Effects within System>Preferences>Appearance after  double checking with a new reboot of course :sad:

Then I re-read this thread: [http://ubuntuforums.org/showthread.php?t=1590367](http://ubuntuforums.org/showthread.php?t=1590367) from [christian.remboldt]("http://ubuntuforums.org/member.php?u=1162302") and decided that because I had a FRESH install I would not need to make changes to /etc/X11/xorg.conf.
as the Nouveau drivers were already installed by default. However I did take the following advice...

> **christian.remboldt said:**
> you need the 3d driver this file is  not included in any package. /usr/lib/dri/nouveau_vieux_dri.so

...but instead building the file myself (because im SUCH a noob) I took a big leap of faith...

> **christian.remboldt said:**
> If you don't want to build it yourself, here is a link to the one I built yesterday. [http://www.mediafire.com/?bzszrsej376y8q7](http://www.mediafire.com/?bzszrsej376y8q7)

and did the unthincable, as a noob, to download and used someone else' self built file!

I then moved my file  to /usr/lib/dri 

> **christian.remboldt said:**
> "Ctrl+Alt+t" this will open a  terminal window. In the terminal type "cd  /home/<user  name>/Desktop" then hit enter. In place of <user  name> make  sure to put your user name. This will change you current  working  directory to the desktop. Then type "sudo cp  nouveau_vieux_dri.so  /usr/lib/dri" and hit enter. You will be prompted  for your  administrator password. On successfully entering the password  and  pressing enter the file will be copied.

and restarted... Sh'bang, Sh'bong Thongsong! I suddenly had my Ubuntu  10.10 singing and dancing, running all the extra Visual Effects quite  nicely :grin:

[B]NOW... the only problem is that Ubuntu still does not recognise my LG M228WA - BZ monitor!
Its a 22" screen and has always run at much higher resolutions than  1024x768, I do realise that my Nvidia graphics card(s) may have had some  role to play in that but im sure this monitor once told me itself (when  I configured Windows resolution wrong) that its best resolution was  something like 1680 x 1050... so my question is HOW do I get Ubuntu to  recognise the true potential of my monitor?[/B] :confused:

[B]PLEASE HELP ME ONCE MORE...

[/B]:mrgreen:I Am Noob

P.S.

> **cariboo907 said:**
> There is a firewall, iptables installed by default, so all you need is a  frontend to set firewall rules. Ufw is installed by default, it stands  for uncomplicated firewall, it is a command line tool for setting  firewall rules. There is also a graphical tool that has the same  function called Gufw, it is in the repositories. To enable the default  rules with ufw, just open a Applications->Accessories->Terminal  and type:
 
 ```
sudo ufw enable
```If you are running a default installation  without any extra services like, ssh, remote desktop or a web server the  default firewall rules are more than enough. If you have an other  computer on your local network, you can do a port scan against the  system to check it for yourself.
 
 I also took this advice and my firewall is now enabled GUI style, thanks again!

---

### Post by owise1 on 2010-11-03
Hi Guys - AaronP of Nvidia has posted that 96.43.19 is ready to try - see [http://www.nvnews.net/vbulletin/showthread.php?t=155622](http://www.nvnews.net/vbulletin/showthread.php?t=155622)

I could not find it in nvidia's download area but hopefully it will not take too long to find its way out into the repository as an update.

Cheers

owise1

---

### Post by sonnettie on 2010-11-03
[URL="ftp://download.nvidia.com/XFree86/Linux-x86/96.43.19/"]**Newest** drivers** working** on _**Ubuntu 10.10**_ on **geforce4 mx** etc cards ..

ftp://download.nvidia.com/XFree86/Linux-x86/96.43.19/   <<<**x86**

ftp://download.nvidia.com/XFree86/Linux-x86_64/96.43.19/  <<**64bit**[/URL]

---

### Post by fluxlizard on 2010-11-04
Thanks for posting the links- I'm about to check them out and give it a shot.

For the  guy who keeps arguing the arrogant viewpoint that old hardware should be tossed-

Give us a break.

Google up on the pollution and health problems in recyclers caused by software making hardware obsolete so rapidly these days.

How about the coders shouldn't break things that are working when they put out new releases?

We wonder why most hardware manufacturers and software companies don't want to support linux?

Nvidia deserves a hand for putting up with this kind of crap and re-writing their drivers every time some genius decides to "improve" xorg and break the drivers.

I have this card on an old machine that still runs ubuntu 10.10 quite well other than this problem. For web surfing, open office, gimp, anything other than streamed video that uses flash (also bloated thanks to our modern disposable mindset even though flash worked really well on this machine a few years ago) it works great.

---

### Post by Henrikx on 2010-11-04
[[IMG]http://img709.imageshack.us/img709/3181/nvidiaxserversettings00.jpg[/IMG]]("http://img709.imageshack.us/i/nvidiaxserversettings00.jpg/")

:-\"

---

### Post by fluxlizard on 2010-11-04
Henrikx-

Would you be kind enough to give us a brief walkthrough for correct installation?

I've tried to follow instructions online, and am running into a couple of problems- I don't seem to have any sort of xorg.conf file and when I try to install, it complains about nouveau even after writing to not use it and rebooting...

---

### Post by Henrikx on 2010-11-05
@fluxlizard

Conditions :

build-essential
xserver-xorg-dev
linux-headers-generic   
The correct linux-headers can be found via Terminal : ```
uname -r
```
libc6-i386 (only for 32 Bit AMD)
nvidia-settings

Download [96.43.19]("http://www.nvnews.net/vbulletin/showthread.php?t=122606")

Uninstall xserver-org-video-nouveau, but not  libdrm-nouveau (too many dependencies)
 libdrm-nouveau is added to the blacklist 
Open terminal : 

```
echo "blacklist nouveau" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```Reboot

With Strg + Alt + F1 switch to to the first console

```
sudo /etc/init.d/gdm stop
```sudo /etc/init.d/kdm stop  (KDE)

```
cd /96.43.19 
``````
sudo sh NVIDIA-Linux-x86-100.14.09-pkg1.run 
```Follow instructions of the installer

Question of whether you want to download a kernel module = NO

Question "to run nvidia-xconfig" = YES

Finish

Reboot

---

### Post by luk1don on 2010-11-05
Blacklist nouveau is not neccessary.

```
sudo gedit /etc/default/grub
```

add option: nomodeset e.g.

> GRUB_CMDLINE_LINUX="nomodeset"

```
sudo update-grub
```

Reboot

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

```
sudo /etc/init.d/gdm stop
```or
```
sudo /etc/init.d/kdm stop
```

Alt + F1, log in

```
sudo sh NVIDIA-Linux-x86-96.43.19-pkg1.run
```

```
sudo nvidia-xconfig
```

or use Xorg -configure

End

---

### Post by fluxlizard on 2010-11-05
Thanks guys for your help!

I've got it working now thanks to you!

Henrikx- I appreciate the effort put into your instructions, but after following carefully step-by-step on a fresh install for some reason it still complained about nouveau drivers when I tried to run the installer.

luk1don- After trying Henrikx instructions I made another fresh install and your instructions worked perfectly. I think you should post it in the tutorials/how to, maybe as a sticky or something.

Couple of thoughts if you do that- 

The installer complains about something and asks if I want to run it anyway, I said yes. Then at the end of the run the already asks if I want to it to run nvidia-xconfig for me.

I said yes, but ran it at the command line afterwords as per your instructions just in case.

Also, I had to still install nvidia-settings afterwords. Only mentioning because if you repost your instructions as a how to somewhere that would be something most users would want to include.

Thanks again guys for the help and to the OP for starting this thread!

---

### Post by deviljelly on 2010-11-06
Comment #45 above offers the clearest install instructions ..... the problem #46 ran into maybe to do with the file /usr/lib/nvidia/pre-install .... I'm guessing Ubuntu puts it there to stop the NVIDIA*.run script from clobbering an existing nvidia-96 install..... I removed this file before running NVIDIA*.run and everything worked well.

---

### Post by deviljelly on 2010-11-06
however vpdau is broken...... mplayer not working... trying to fix

---

### Post by owise1 on 2010-11-06
Dont forget that every time an upgrade to the kernel happens you will need to re-run the nvidia .RUN script.  I hope that as this appears to be an oversight in 10.10 that this driver is packaged to save us all the hassles.

bye the way I am quite impressed with Nouveau for 2D.

---

### Post by ckomurlu on 2010-11-10
Hi,
   I have an Nvidia Geforce4 MX 440 graphics adapter. I applied luk1don's method and it worked great. I've been using Ubuntu since then whitout any problem, last night this problem occured:
   When I logged on, gnome panels never appear, the desktop icons neither. The right click menu does not work at all. Hotkeys such as Alt+F1 and Alt+F2 work fine. This issue has been discussing in [this thread]("http://ubuntuforums.org/showthread.php?t=1592069"). Why I have carried it into this thread, because I guess it's related to my graphics adapter.
   What I did as a workaround, modifying xorg.conf file and change the line
    Driver         "nvidia"
to
    Driver         "nv"
so that nvidia's original driver gets disabled and nv driver gets activated instead. Well, I got back my panels, my icons and right click menu, and probably other things that I had not realized their disfunction. Do you have any idea to solve the problem on nvidia driver?

Thanks,

---

### Post by owise1 on 2010-11-13
I see that - [Bug 626974] Re: ABI change in xorg 1.9 breaks legacy nvidia-96 drivers in Maverick - is finally getting some traction.  

** Changed in: nvidia-graphics-drivers-96 (Ubuntu Maverick)
* *Importance: Undecided => Medium

** Changed in: nvidia-graphics-drivers-96 (Ubuntu Maverick)
* * * *Status: Confirmed => Triaged

Hopefully the driver will get packaged soon.

If you have not been to the bug report suggest that you do and confirm that it impacts you as well as there are only 117 people reported as impacted - [https://bugs.launchpad.net/bugs/626974](https://bugs.launchpad.net/bugs/626974)

---

### Post by Naoko15 on 2010-11-28
> **luk1don said:**
> Blacklist nouveau is not neccessary.

```
sudo gedit /etc/default/grub
```add option: nomodeset e.g.



```
sudo update-grub
```Reboot

```
sudo apt-get install build-essential linux-headers-$(uname -r)
``````
sudo /etc/init.d/gdm stop
```or
```
sudo /etc/init.d/kdm stop
```Alt + F1, log in

```
sudo sh NVIDIA-Linux-x86-96.43.19-pkg1.run
``````
sudo nvidia-xconfig
```or use Xorg -configure

End

Hi, I've got Geforce Ti4200 and i  had the same problem (no propietary drivers for my graphic card after Maverick Merkaat upgrade). Reading the forum i've found out that the legacy drivers have been already released. I've followed luk1don's instructions to install Nvidia's drivers and it seemed to work ok (installation completed, no problems there). The problem now is that my computer is running on low res mode and in System-Administration-Drivers the Nvidia drivers are not there. Also when i try to install them again it says they are already installed. Any ideas? Any help will be much appreciated

Edit: when i go to System-Preferences-Screen it allows me to use Nvidia X Server Settings, and it lets me change the screen resolution, although when i reboot, the screen goes back to low-res. Also i can't use desktop effects. This is the X Configuration file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder75)  Wed Oct 27 19:21:11 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L192WS"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200 with AGP8X"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1280x1024 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by Naoko15 on 2010-11-29
No one knows? Help please :(

---

### Post by ethern0t on 2010-11-29
After Installing if you have a black screen with sound coming just do this :

goto your xorg.conf add below DEPTH ( on screen) Option "UseDisplayDevice" "DFP-0"

This worked for me after installing the nvidia drivers from nvidia 
Using a laptop with geforce 4 420GO,
Good Luck everyone.

---

### Post by Naoko15 on 2010-11-30
Thank you for you reply but my problem is that after installing Nvidia drivers i have to manually enter the correct resolution for my screen on each reboot, as i get a "can't detect monitor display" warning everytime. 

Also the drivers are not anywhere to be found, even though when i try to reinstall it says they are already installed.

Therefore i can't use desktop effects either. 

Help, please. Thank you!

---

### Post by MonsterTrimble on 2010-12-01
I had the same issue, and installed the repo from here: [http://ubuntuforums.org/archive/index.php/t-1620376.html](http://ubuntuforums.org/archive/index.php/t-1620376.html)

Worked like a charm.

---

### Post by Naoko15 on 2010-12-02
Thank you so much MonsterTrimble!!!! it worked great! :)

---

### Post by MonsterTrimble on 2010-12-06
Good to hear!

---

### Post by Leezer on 2011-01-25
> **owise1 said:**
> correct cascade9 - I should have been more specific - Leezer should keep an eye out for an update via update manager for nvidia and then enable.  Hopoe that it is not too long a wait.

cheers

Update:

A new version of the driver FINALLY came in through the update manager today.  I activated it as per the above instructions and restarted my machine, and it seems to work, except I am still having problems playing videos such as youtube.  They play in fast forward on my machine.  Any idea what the problem is here?

It is really frustrating to wait so long for an update and then discover that it still doesn't work properly.

---

