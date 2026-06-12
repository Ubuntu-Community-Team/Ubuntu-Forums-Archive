---
title: "Configuring Radeon Driver on Karmic with ATI HD4200"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MaindotC on 2009-10-16
Has anyone configured the open-source Radeon driver to work properly with Karmic 9.10 on this integrated video card?  I understand it apparently only has 2D support, but I got a Gigabyte GA-MA785GM-US2H motherboard that has this onboard video and one of the reviews says it ran Karmic like a champ.  Anyone been able to do this w/ this board?  Thanks!

---

### Post by happyhamster on 2009-10-16
I have that same motherboard, and onboard video works fine with the default driver (ATI/Radeon). 2D is fast and snappy when using the stock settings: no configuration needed whatsoever. In fact, when testing Karmic, the only video configuring I did after a fresh install was NOT installing the proprietary fglrx driver :D (I don't use compiz, play 3D games, etc.)

The only real problems I had with the board weren't software related: I tweaked all kinds of BIOS-settings, causing the board to fail booting. It was especially touchy about configuring memory settings (so my advice is to just not tweak those).

edit: I disabled RAID, serial port and firewire, so don't know if those work or not.

---

### Post by MaindotC on 2009-10-16
Yeah I read in another thread that the video has a problem utilizing the sideport memory, and one guy changed it to UMA but I couldn't find that setting in the BIOS.  I totally agree with you that it works "as is" but I was hoping to be able to utilize some of those video effects :(

I'll try removing the proprietary driver so it should default back to the radeon driver, I'm assuming, and try running Counterstrike.  CS, a 3-d game, is the real dealbreaker for me and I'm trying desperately to get it to work.  You're no help :p Thank you for your input though!

---

### Post by monraaf on 2009-10-16
There's experimental open source 3D support for the Radeon HD cards, I believe the HD 4200 is also supported.

To get it, you'll have to use this PPA:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

And you'll need to install the latest 2.6.32 kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It's still experimental, so use at your own risk.

---

### Post by MaindotC on 2009-10-16
Wow thanks a lot!  I'll just load it onto a different partition and if it doesn't work, no loss to me :D  Hmmm...I have a question and I acknowledge that I'm asking this without reading the documentation so if you don't wish to answer this I completely understand.  When I add those ppa's, will they automatically upgrade those packages?  I've always wondered about using a later kernel than is supported by the current Ubuntu distribution but I wasn't sure how all that worked.  In any even thank you so much!

---

### Post by monraaf on 2009-10-16
Only the first really is a ppa. To use it add this:

```

ppa:xorg-edgers/ppa

```

to your software sources and run update manager For the kernel you have to download the debs and install them. Latest is v2.6.32-rc5:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32-rc5/)

In firefox just click on the appropriate linux-image-* and linux-headers-* links (i386 or amd64) and let Firefox open them with GDebi.

---

### Post by MaindotC on 2009-10-16
I added those repos and all and upgraded packages - don't notice any changes.  I don't know precisely what I'm suppsed to do - looking for documentation but I've not yet found anything.

---

### Post by monraaf on 2009-10-16
Can you post the output of

```

uname -r

```

and

```

glxinfo |grep renderer

```

---

### Post by MaindotC on 2009-10-16
Sure thing, I'm familiar w/ these commands:
```

x@x:~$ uname -r
2.6.32-020632rc5-generic
x@x:~$ glxinfo | grep direct
IRQ's not enabled, falling back to busy waits: 2 0
direct rendering: Yes
x@x:~$ glxinfo | grep renderer
IRQ's not enabled, falling back to busy waits: 2 0
OpenGL renderer string: Mesa DRI R600 (RS880 9710) 20090101  TCL
x@x:~$ 

```

Desktop effects work just fine.

---

### Post by monraaf on 2009-10-16
Okay, looks like you got it working :)

---

### Post by MaindotC on 2009-10-16
Hmmm...would it make any difference if I reinstall CS, or even reinstall wine and then cs?

---

### Post by monraaf on 2009-10-16
I don't now about CS, but I have been playing Half Life and even Half Life 2 with these open source drivers :P. Just try it...

---

### Post by MaindotC on 2009-10-17
What version of Wine are you using?

---

### Post by MaindotC on 2009-10-17
I tried version 1.0.10 and it was the same slow choppy 1/2 a FPS, and then I tried 1.2 and I got the same thing.  *frustrated* :( :( :(

---

### Post by monraaf on 2009-10-17
Are you trying to run CS or CS:Source?  If you are trying to run it with Compiz enabled, try disabling Compiz, try lowering resolution and settings.

Try running a native Linux OpenGL game like neverball on your computer, see if that runs well.

---

### Post by MaindotC on 2009-10-17
I'm trying to run CS 1.6.  I tried disable Compiz but I got the same effect :(  Neverball (thanks for reminding me that game is awesome) runs well :)  Changing the resolution - well I don't think that's fair.  It runs excellent on the old machine w/ the no-longer supported x850, so I don't see why I should have to reduce the resolution for this one.  But I did just to appease you...1024x768 and I even changed colour to 16-bit in CS.  Still choppy, like 1/2 FPS :(  I really appreciate your suggestions.  I'm going to bed so maybe we can come up with some ideas tomorrow.

Hey, one thing about the experimental video drivers - after I ran the updates, I had the same result, so I installed xserver-xorg-video-radeonhd.  What packages did you install?  I have no xorg.conf, should I have one?

---

### Post by monraaf on 2009-10-17
I don't have an xorg.conf either, you don't need one with newer versions of Xorg. But radeon and radeonhd are only for 2D so it doesn't matter which one you choose, for 3D the driver is mesa.

If I'm not mistaken CS 1.6 runs on the old Half Life engine and I get excellent frame rates > 40 fps at 1440x900 with Half Life. strange...

---

### Post by MaindotC on 2009-10-17
Maybe I'll have to try the ol' "nice, fresh, clean install."  Are there any particular BIOS settings you suggest?  Also, when I connect the DVI port to my 21'' Samsung Synchmaster the picture is extremely distorted - mostly red, wave-live interference from the left side, but when I connect it to a Dell 18'' monitor it works fine.  I was wondering if I should RMA my board.

---

### Post by MaindotC on 2009-10-17
Ok, I'm starting over.  I'm documenting my steps so I'll edit this as events warrant:

1.  Installed Karmic.
2.  Imported xorg-edgers key
3.  Downloaded:

     linux-headers-2.6.32-020632rc5_2.6.32-020632rc5_all.deb
     linux-headers-2.6.32-020632rc5-generic_2.6.32-020632rc5_amd64.deb
     linux-image-2.6.32-020632rc5-generic_2.6.32-020632rc5_amd64.deb
     linux-source-2.6.32_2.6.32-020632rc5_all.deb
I'm assuming that the "all" packages install the package dependent on my architecture but just in case I downloaded the "all" and the amd64 packages.

4.  Ran "sudo dpkg -i linux-*", all packages seemed to install fine.  I have terminal output saved if it should be needed.

5.  Restart and boot into kernel 2.6.32-020632rc5.

6.  Ran updates via apt.  Output saved for reference.

7.  Updates complete.  Rebooted and checked driver with the following command per one of the maintainers of the xorg-edgers ppa:
```

xk@xk:~$ glxinfo | grep OpenGL
IRQ's not enabled, falling back to busy waits: 2 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: Mesa DRI R600 (RS880 9710) 20090101  TCL
OpenGL version string: 1.4 Mesa 7.7-devel
OpenGL extensions:
xk@xk:~$

```
8.  After checking the forums, up to [post #25](http://ubuntuforums.org/showpost.php?p=8121333&postcount=25) I add the Jaunty Wine repository.  I open Synaptic, mark all upgrades, and select Wine 1.31 to install:
```

Removed the following packages:
libgd2-noxpm

Upgraded the following packages:
evolution-plugins (2.28.0-0ubuntu2) to 2.28.0-0ubuntu4
ibus (1.2.0.20090723-1ubuntu1) to 1.2.0.20090927-2ubuntu1
linux-firmware (1.23) to 1.24
linux-generic (2.6.31.11.22) to 2.6.31.14.27
linux-headers-generic (2.6.31.11.22) to 2.6.31.14.27
linux-image-generic (2.6.31.11.22) to 2.6.31.14.27
openoffice.org-base-core (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-calc (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-core (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-draw (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-gnome (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-gtk (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-impress (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-math (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
openoffice.org-writer (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
python-ibus (1.2.0.20090723-1ubuntu1) to 1.2.0.20090927-2ubuntu1
python-uno (1:3.1.1-2ubuntu3) to 1:3.1.1-4ubuntu1
ubuntu-desktop (1.171) to 1.174

Installed the following packages:
cabextract (1.2-3)
libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1)
libneon27-gnutls (0.28.6-1)
libpst4 (0.6.41-0ubuntu2)
linux-headers-2.6.31-14 (2.6.31-14.48)
linux-headers-2.6.31-14-generic (2.6.31-14.48)
linux-image-2.6.31-14-generic (2.6.31-14.48)
python-rsvg (2.28.0-0ubuntu1)
ttf-liberation (1.05.1.20090721-0ubuntu1)
ttf-mscorefonts-installer (3.0)
winbind (2:3.4.0-3ubuntu5)
wine (1.1.31~winehq0~ubuntu~9.04-0ubuntu1)
wine-gecko (1.0.0-0ubuntu1)

```

I reboot, then install Steam with the command:
```

msiexec /a SteamInstall.msi

```

Installed Steam, installed CS.  Started CS and it works!  FPS is 30 - 40 at 1600x1200, but I can kick it down to 1024x768 and get between 40 - 70 FPS.  It's enough to coax me to move to the new machine and use it till I have enough money to get a better vid card or till ATI releases a better driver for Karmic :)

---

### Post by tormod on 2009-10-17
You don't have to install the linux-source package, it is only useful if you want to compile the kernel yourself which is generally a waste of time.

The kernel headers are also not needed for this purpose, only if you have some third-party drivers that needs to be built for this kernel.

For "the point of no return", there is no problem with the kernels, since you will keep the old 2.6.31 kernel anyway. For the xorg-edgers PPA, it is as simple as running "ppa-purge xorg-edgers" to revert to standard Karmic xorg packages again. For wine and CS, I don't know :)

---

### Post by Wise Ferret on 2009-10-17
As far as I know, the free radeon driver does 3d for the card in question (with the tricks above applied), but is not yet integrated with Gallium 3d and thus does not support OpenGL 2.0. This breaks 3d for wine applications.

---

### Post by legolas_w on 2009-10-17
Hi,

Do I need to follow this procedure if I want to enable my ATI Radeon 3470?
I just want to play starcraft on wine and nothing else in my system needs graphical things.

Thanks

---

### Post by Wise Ferret on 2009-10-17
> **legolas_w said:**
> Hi,

Do I need to follow this procedure if I want to enable my ATI Radeon 3470?
I just want to play starcraft on wine and nothing else in my system needs graphical things.

Thanks

You need to follow this procedure to use linux-native 3d apps like compiz and neverball. The open source driver does not currently support 3d apps on wine.
Does starcraft use 3d? If it does not, there is a chance it will run on wine with the open driver for you. If it does, you can use the proprietary driver, fglrx.

---

### Post by monraaf on 2009-10-17
> **Wise Ferret said:**
> You need to follow this procedure to use linux-native 3d apps like compiz and neverball. The open source driver does not currently support 3d apps on wine.


I don't know where you got that info, but it's not true. Of course the open source driver is far from complete and won't run as many games as the proprietary driver but I have run several games on wine with this open source driver (Half Life, Half Life 2, Deus Ex, Max Payne)

---

### Post by monraaf on 2009-10-17
> **strAlan said:**
> 
I believe the next step would be to install wine and try to run CS.  Can anyone suggest if Wine 1.2 is ideal or if I should try a previous version?  I'm just trying to avoid a "point of no return" and have to re-image all over again :D

Personally I'm using wine from this repository.

```

deb http://wine.budgetdedicated.com/apt jaunty main

```

It's from jaunty but works fine in Karmic. See also:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

If after using that version of wine you still don't have success, I  suggest trying the i386 version of Karmic (that's what I'm running).

---

### Post by MaindotC on 2009-10-17
> **monraaf said:**
> Personally I'm using wine from this repository.

```

deb http://wine.budgetdedicated.com/apt jaunty main

```

It's from jaunty but works fine in Karmic. See also:

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

If after using that version of wine you still don't have success, I  suggest trying the i386 version of Karmic (that's what I'm running).

Karmic has version 1.2 that installs without adding the wine repo.  What version do you use?  I'll try adding the jaunty repo and I assume it will add whatever that latest version is.  You say you are having success so I'll follow your advice.  What type of screen resolution do you use?  As I said before, 1600x1200 on my older machine using the x850 in Hardy runs pretty well, so I don't see why I should accept anything less in Karmic.

I'll try the 32-bit but I can't possibly fathom how that could make a difference.  If I don't have success and it works, well, I guess then it's one for the books.

Tormod has been helping me with xorg-edgers and thank you very much for your correspondence.

---

### Post by MaindotC on 2009-10-17
It works!!!!!!!!!!!!  Thank you all so much for your help!  I added details to my post #19.  It's not as good quality as the machine w/ my x850 but it's good enough that I can use this machine full time now :)  Thank you all so much for your help!!!!!

---

### Post by MaindotC on 2009-10-19
How do you boot into other kernels after all this is done?  For some reason my grub doesn't appear anymore and I'm brought right into the 2.6.32-020632rc5 kernel.  I realize that if I boot into a diff kernel I won't have the 3d support that the 2.6.32-020632rc5 kernel provides w/ the experimental radeon driver but I want to use Virtualbox.  Thanks!

---

### Post by DougieFresh4U on 2009-10-19
Machine is AMD Athlon 64  Dual Core 5200  ATI Radeon HD3200 on board graphics.
Multi-boot.
Added .32 kernel and the ppa.
Excellent job.I have fglrx installed on my other 3 partitions.  Performance is much better on this partition. Compiz and 'Extra' in the Appearance menu are all working great.
Thanks for the work that was done to get this together!!

---

### Post by tormod on 2009-10-19
> **strAlan said:**
> How do you boot into other kernels after all this is done?  For some reason my grub doesn't appear anymore and I'm brought right into the 2.6.32-020632rc5 kernel.
If there's no other OS, grub will be hidden by default. Hold the shift key down to make it appear.

---

### Post by MaindotC on 2009-10-19
Hey, Tormod - yes I know how to enter Grub it's just that when I select previous kernel versions I am unable to login under those versions.  It appears to attempt to log in but then I am brought back to the login screen where I try repeated attempts and can't get in unless I reboot and select the rc5 kernel.  It's not terrible - I remember your site specifically states not to attempt installation of the experimental ATI driver without the possibility of "breaking" the system and I'm perfectly fine with that - I just wondered if it was possible to get back into the other kernels.  I'd like to use WebcamStudio and Virtualbox and they won't work with this kernel.  If there's some way to compile the source code of those respective applications I don't know how to do that.

---

### Post by screaminj3sus on 2009-10-20
Thanks a lot for the info on xorg edgers, got it running with my hd2600 and compiz works great! No more crappy fglrx!

Does anyone know how good video playback with this is on ati? with fglrx and compiz I got tearing in videos no matter what and kit was sooo annoying. if there is anyway I can run non-tearing videos with this open source driver and compiz running I will be very happy, I just don't have any videos to test at this very moment.

Compiz actually seems to be running much smoother with this open source driver than it ever has with fglrx which is nice.

---

### Post by tormod on 2009-10-20
> **strAlan said:**
> It appears to attempt to log in but then I am brought back to the login screen where I try repeated attempts and can't get in unless I reboot and select the rc5 kernel.
That means the Xorg server is crashing, there should be some information in Xorg.0.log or gdm/:0.log.

Anyway, this should normally not happen, even if you are using an older kernel. But it could be a bug, which has been fixed in newer kernels.

---

### Post by tormod on 2009-10-20
> **monraaf said:**
> Only the first really is a ppa. To use it add this:

```

ppa:xorg-edgers/ppa

```

Please don't give such instructions, but rather tell people to actually go to the xorg-edgers PPA web page themselves. It is a big problem that people add PPAs without knowing what they are for. The PPA web page is the only place where we can give centralized information and important notices about the packages.

---

### Post by MaindotC on 2009-10-22
> **tormod said:**
> That means the Xorg server is crashing, there should be some information in Xorg.0.log or gdm/:0.log.

Anyway, this should normally not happen, even if you are using an older kernel. But it could be a bug, which has been fixed in newer kernels.

Hey Tormod!  I can boot into other kernels now.  There were some updates for Karmic that were recently released and they must have fixed whatever issues Xorg was encountering.  Now that I can boot into other kernels I can't use your ATI driver w/ 3D support but I can use the vloopback module which is something needed for WebCamStudio.  Thanks for your help :D

---

### Post by Longinus00 on 2009-10-22
> **screaminj3sus said:**
> Thanks a lot for the info on xorg edgers, got it running with my hd2600 and compiz works great! No more crappy fglrx!

Does anyone know how good video playback with this is on ati? with fglrx and compiz I got tearing in videos no matter what and kit was sooo annoying. if there is anyway I can run non-tearing videos with this open source driver and compiz running I will be very happy, I just don't have any videos to test at this very moment.

Compiz actually seems to be running much smoother with this open source driver than it ever has with fglrx which is nice.

The open source drivers have had tear free videos for many months now (since before jaunty). You'll wonder why you've been fighting with fglrx for all this time.

---

### Post by MaindotC on 2009-10-22
> **Longinus00 said:**
> The open source drivers have had tear free videos for many months now (since before jaunty). You'll wonder why you've been fighting with fglrx for all this time.

Do you think an x850 would run better than an onboard HD4200?

---

### Post by Longinus00 on 2009-10-22
> **strAlan said:**
> Do you think an x850 would run better than an onboard HD4200?

I really have no idea but if you have one lying around it couldn't hurt to try.

---

### Post by BMWDriver on 2009-10-23
You can't expect much out of onboard video, at least nowadays still. Remember the X850 was quite a performer in its prime time; it has its own memory and a fully independent GPU. X850 is a Top Gun from its generation. So it's no surprise that the X850 kicks the heck out of your onboard HD4200 which shares memory with your system. 

What your HD4200 is likely to have is more features, such as DX10.1, access to more recent rendering technology... but as far as performance goes, it seems you're doing as well as it's gonna get. Certainly older games will do ok with it.

I personnaly run an X800XT with 256MB of memory, and I find much interest in your thread because I just can't get 3D acceleration going properly. I really like Compiz because it has some nice functionnality to it. It's eye candy I have to do without for now.

Here's an article from one of my favourite sources on evaluting gaming hardware:
[AMD's 785G with Radeon HD 4200 Graphics: Performance and Features Explored]("http://www.firingsquad.com/hardware/amd_785g_performance/default.asp")

---

### Post by Longinus00 on 2009-10-23
> **BMWDriver said:**
> I personnaly run an X800XT with 256MB of memory, and I find much interest in your thread because I just can't get 3D acceleration going properly.

What kind of issues are you having exactly?

---

### Post by MaindotC on 2009-10-23
> **BMWDriver said:**
> You can't expect much out of onboard video, at least nowadays still. Remember the X850 was quite a performer in its prime time; it has its own memory and a fully independent GPU. X850 is a Top Gun from its generation. So it's no surprise that the X850 kicks the heck out of your onboard HD4200 which shares memory with your system. 

What your HD4200 is likely to have is more features, such as DX10.1, access to more recent rendering technology... but as far as performance goes, it seems you're doing as well as it's gonna get. Certainly older games will do ok with it.

This is an excellent viewpoint - thank you!  I don't know very much about circuitry or understanding of different chipsets so I appreciate you putting this in a little bit easier terms to understand.
> **BMWDriver said:**
> 
I personnaly run an X800XT with 256MB of memory, and I find much interest in your thread because I just can't get 3D acceleration going properly. I really like Compiz because it has some nice functionnality to it. It's eye candy I have to do without for now.


First of all, with the latest updates to Karmic I'm getting better 3D support - about 30 - 50 FPS running apps depending on OpenGL - notably Counterstrike and UrbanTerror.  I don't see how that's possible seeing as how I'm using a kernel that is not yet supported by Karmic so I don't see how they'd push me a package built for that kernel, and I thought the xserver-xorg package came from Tormod's repo not the Karmic repos but ok whatever.

Secondly, I tried using the x850 in Jaunty before and there wasn't really any decent driver for it or I didn't have it configured properly.  If you download the driver (for the x850) from the ATI site and try and install it, it will return an error because it can't be installed on 9.04 and above.  If you look for a later driver, the x850 is in "legacy support" (which means no more support) so you can't get a driver that works with 9.04 and above.  Sure you can use the open-source "radeon" driver that comes with Jaunty but I don't see how you'd get 3D-support running unless you use my instructions for installing the development kernel and experimental ATI drivers from Tormod.  Did you try doing that?

---

### Post by PGHammer on 2009-10-23
> **monraaf said:**
> There's experimental open source 3D support for the Radeon HD cards, I believe the HD 4200 is also supported.

To get it, you'll have to use this PPA:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

And you'll need to install the latest 2.6.32 kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It's still experimental, so use at your own risk.

Very Experimental (this is also in the beta of Fedora 12 as well).

I'm kicking this around in Fedora 12 beta 1 along with the experimental GNOME 3 Shell.  In Fedora, I'm using the open-source radeon subdriver; I'll be switching to the radeonhd subdriver on the next run series.

---

### Post by BMWDriver on 2009-10-23
Compiz won't start, no 3D acceleration except for the screensavers that seem to do just fine. Tried Neverball (1 or 2 fps, ouch!) and Alien Arena (nothing stellar, just software rendering I think).

---

### Post by Longinus00 on 2009-10-23
> **BMWDriver said:**
> Compiz won't start, no 3D acceleration except for the screensavers that seem to do just fine. Tried Neverball (1 or 2 fps, ouch!) and Alien Arena (nothing stellar, just software rendering I think).

This might have to do with you having an all in wonder card. Has the open source driver never worked for you?

---

### Post by BMWDriver on 2009-10-24
It does work just fine with 9.04. Yesterday, I went on AMD's site to see that the All-in-Wonder cards are supported in the latest Catalyst drivers. 

I'm in the middle of a fresh re-install of Karmic with the RC this time, and not Ubuntu Studio like the first time. Like always, first boot has desktop effects working.

This time I might try fglrx if radeon does not work after second reboot.

---

### Post by BMWDriver on 2009-10-24
Ah, now it works with radeon driver. Some issues with Gimp and Compiz (below), but much MUCH better now. Neverball works very nicely too. I can turn on special desktop effects and set them to my liking. Thrid reboot, and all is perfect.

The brush tool lags when Compiz is enabled. I may yet try fglrx later, but I like to go to wiki.cchtml.com to get better installation instructions. The site's down right now.

---

### Post by MaindotC on 2009-10-24
New updates from the xorg-edgers PPA. Better, but still not good enough (counterstrike still too choppy to play).  Thanks Tormod and keep up the good work!  You guys should set up a link to donate :)

---

### Post by Longinus00 on 2009-10-24
> **BMWDriver said:**
> Ah, now it works with radeon driver. Some issues with Gimp and Compiz (below), but much MUCH better now. Neverball works very nicely too. I can turn on special desktop effects and set them to my liking. Thrid reboot, and all is perfect.

The brush tool lags when Compiz is enabled. I may yet try fglrx later, but I like to go to wiki.cchtml.com to get better installation instructions. The site's down right now.

fglrx won't work with your video card I'm sorry to say. I'm glad you got everything working in the end though. You might want to try making a thread devoted to your compiz problem to see if anyone can help you with that.

---

### Post by MaindotC on 2009-10-25
> **Longinus00 said:**
> fglrx won't work with your video card I'm sorry to say. I'm glad you got everything working in the end though. You might want to try making a thread devoted to your compiz problem to see if anyone can help you with that.

fglrx won't work with his card *in Jaunty and above*.  8.10 and below the fglrx driver should work fine if you need to roll back your system.

---

### Post by BMWDriver on 2009-10-25
Doh! I misread the release notes of ATI; only the All-in-Wonder variants of HD2400 and later are supported. Well, it don't matter to me. I just keep effect off for now since I use Gimp a lot. I'll just look out for driver updates and try again then.

---

### Post by 4partee on 2009-10-26
> **strAlan said:**
> Has anyone configured the open-source Radeon driver to work properly with Karmic 9.10 on this integrated video card?  I understand it apparently only has 2D support, but I got a Gigabyte GA-MA785GM-US2H motherboard that has this onboard video and one of the reviews says it ran Karmic like a champ.  Anyone been able to do this w/ this board?  Thanks!

I have three of that mobo.  There is a new ATI driver, version 9.10, at [www.amd.com](www.amd.com) along with a pdf install guide.  

I have installed it on 9.04 both 32 and 64 bit, but have not yet tried it on Karmic.

HTH
John

---

### Post by MaindotC on 2009-10-26
> **4partee said:**
> I have three of that mobo.  There is a new ATI driver, version 9.10, at [www.amd.com](www.amd.com) along with a pdf install guide.  

I have installed it on 9.04 both 32 and 64 bit, but have not yet tried it on Karmic.

HTH
John

Please read the thread before posting as the concern of the ATI proprietary driver has already, CLEARLY, been addressed.

---

