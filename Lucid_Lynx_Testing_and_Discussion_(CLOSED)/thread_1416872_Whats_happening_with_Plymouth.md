---
title: "Whats happening with Plymouth?"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by katie-xx on 2010-02-26
[SIZE=2][COLOR=Blue]Can anyone give an authoritative statement regarding progress with Plymouth?
Its very confusing reading through the Forum to get a feel if things are improving or not.
In my own case I had a slight problem last night with Plymouth not starting and getting dumped to a log in screen ... twice .. before I could get to my desktop.
Tonight after updating, that problem doesnt seem as bad ... Plymouth is taking sometime to load but at least I only get one log in screen :)
All this is very interesting to me because Plymouth was a major obstacle in Fedora and resulted in a great many people going to an alternative Distro. That was all sometime ago and hopefully  we wont see a repeat with Ubuntu.
So ..if anyone can pull all this together Im sure it would help not just me but a whole load of other people too 
Thanks :)

Kate[/COLOR][/SIZE]

---

### Post by cariboo on 2010-02-26
I think it seems to make a difference what graphics adapter you are using. On the computer I'm using at the moment, I have an Nvidia GT210 graphics card, plymouth doesn't get finished, and I get dumped to a screen running through all the different TV tuner cards that are supported in the kernel, then I get to the login screen, where I have to login twice in order to get to the desktop.

On my netbook, plymouth works the way it should, I only have to log in once. my netbook has the Intel 945 graphics chipset.

On my main system at home, with an Nvidia 8400GS graphics card plymouth doesn't finish, but I only have to log in once.

So it looks like a win for Intel, but there are still problems with Nvidia.

---

### Post by ElSlunko on 2010-02-26
Not an authoritative response but I've SEEN the plymouth splash screen a couple of times during shutdown but haven't witnessed it during the booting process. It looks pretty cool IMO but I'm sure it has to do with the alpha state would be responsible for it's constant flux.

---

### Post by katie-xx on 2010-02-26
> **cariboo907 said:**
> 
So it looks like a win for Intel, but there are still problems with Nvidia.
[SIZE=2][COLOR=Blue]
Thanks for that. That seems to stack up with my own observations. My Sony Laptop has a Intel chipset and seems ok. However, this laptop, a Dell Studio, has the ATI Mobility Radeon HD 3400 and seems to be having intermittant problems. Sometimes it will sometimes it wont.
I guess we shall have to wait and see what happens by the time the first beta appears :)
At least no one seems to be getting those horrible "progress bars" which blighted Fedora.

Kate
[/COLOR][/SIZE]

---

### Post by Uncle Spellbinder on 2010-02-26
> **ElSlunko said:**
> ...I've SEEN the plymouth splash screen a couple of times during shutdown but haven't witnessed it during the booting process.

I've not seen Plymouth at all.

---

### Post by Alexandre Putt on 2010-02-26
> **Uncle Spellbinder said:**
> I've not seen Plymouth at all.

Yup, I can't see any effect of its presence.

EDIT: It works after following the suggestions here. Great!

---

### Post by descendent87 on 2010-02-26
working perfect for me on startup and shutdown, card is an ATI HD3200

---

### Post by Uncle Spellbinder on 2010-02-26
All I see is the word "Plymouth" appear every now and then. Video card: nVidia 9800GT

---

### Post by ybytyruzu on 2010-02-26
Here I have a Laptop Acer 3100 with ATI Radeon Xpress 1100, and never note nothing about Plymouth. After grub only the Ubuntu Logo and login, and shutdown don't work

---

### Post by katie-xx on 2010-02-26
> **ybytyruzu said:**
> Here I have a Laptop Acer 3100 with ATI Radeon Xpress 1100, and never note nothing about Plymouth. After grub only the Ubuntu Logo and login, and shutdown don't work

I[SIZE=2][COLOR=Blue] think if you are running 10.04 the Ubuntu logo is Plymouth.
Your shutdown doesnt work? Does it show the Ubuntu logo again and freeze there?

Look at this thread for more info :)

[/COLOR][/SIZE][http://ubuntuforums.org/showthread.php?t=1381109](http://ubuntuforums.org/showthread.php?t=1381109)
[SIZE=2][COLOR=Blue] 
Kate
[/COLOR][/SIZE]

---

### Post by Owen.C93 on 2010-02-26
If it's any help had the same problems as you guys with an upgrade, so I burnt an .iso and did a clean install. As far as I know it works fine now. Not that I know what plymouth looks like.

But yeah if you can do a clean install then I recommend that.

---

### Post by ybytyruzu on 2010-02-26
Hi Katie, ohh...ok...so is ok...I will read that thread, thank!

---

### Post by Jordanwb on 2010-02-26
> **cariboo907 said:**
> I get dumped to a screen running through all the different TV tuner cards that are supported in the kernel

Wait... Huh? :confused:

Plymouth is working acceptably on my Acer Aspire 5515 (Radeon x1200 or similar)

---

### Post by aviramof on 2010-02-27
i have completly removed it a few days ago is it safe to install it again from synaptic?

---

### Post by kansasnoob on 2010-02-27
I only know I can't boot with it installed!

---

### Post by katie-xx on 2010-02-28
[SIZE=2][COLOR=Blue]I think a bump is a good idea here :)
Lets see ..Ive been using on two laptops.
One, the Sony, has Intel Graphics and Plymouth has been ok from beginning.
The other, a Dell, has ATI Graphics and, initially was working no problem, but now, on boot, all I see is a flashing cursor until the log in screen appears. On that basis things seem to have gone backwards. 
On the upside, both machines show Plymouth correctly for shutdown. Having said that it shuts down considerably slower than 9.10 does.

Any other accounts with similar or different kit ?

Kate[/COLOR][/SIZE]

---

### Post by Uncle Spellbinder on 2010-02-28
No Plymouth on startup or shutdown here.

HP Pavilion Elite, nVidia 9800 GT

---

### Post by exploder on 2010-02-28
I have Plymouth showing on shut down only with nvidea graphics. Pretty much just a black screen until gdm appears at start up.

---

### Post by nanog on 2010-02-28
"But yeah if you can do a clean install then I recommend that."

Actually upgrades are the preferred way to test (or run ubuntu). I have N E V E R done a re-install and most of my boxes date back to dapper or even breezy.

---

### Post by exploder on 2010-02-28
>  "But yeah if you can do a clean install then I recommend that."

I did a clean install this afternoon.

Edit: Upgrading leaves a lot of unwanted old config files on the system.

---

### Post by Uncle Spellbinder on 2010-02-28
Same here. Clean install of Alpha 3. Still no Plymouth on startup or shutdown.

---

### Post by dino99 on 2010-03-01
> **exploder said:**
> I did a clean install this afternoon.

Edit: Upgrading leaves a lot of unwanted old config files on the system.

yes that's true, you can clean the room whith bleachbit (very nice, powerfull and dangerous too by the way if not used as it might)

---

### Post by philinux on 2010-03-01
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]
At least no one seems to be getting those horrible "progress bars" which blighted Fedora.

Kate
[/COLOR][/SIZE]

Nvidia 8600gt. 

3 fsck messages then...
Horrible blue/white progress bars at bottom of screen.

Plymouth is uninstalled for now with quiet removed so I can seen whats going on. I'll install it when I see a changelog that might indicate progress.

---

### Post by Elfy on 2010-03-01
> **philinux said:**
> Nvidia 8600gt. 

3 fsck messages then...
Horrible blue/white progress bars at bottom of screen.

Plymouth is uninstalled for now with quiet removed so I can seen whats going on. I'll install it when I see a changelog that might indicate progress.

+1 to the lovely progress bars ...

---

### Post by Owen.C93 on 2010-03-01
Yep flashing cursor for me then blue progress bar and a quick nvidia splash. This is with nvidia 190.5xxx driver. The supplied one give me a plymouth boot screen but I get other problems. 

Also shutdown is much slower than 9.10

---

### Post by recluce on 2010-03-01
> **philinux said:**
> Nvidia 8600gt. 

3 fsck messages then...
Horrible blue/white progress bars at bottom of screen.

Plymouth is uninstalled for now with quiet removed so I can seen whats going on. I'll install it when I see a changelog that might indicate progress.

+2 for the fsck and progress bar. NVidia Quadro NVS140 with nNvidia 195.36.03 drivers. 

Add to this the "Gnome Restart after hitting the '2' key", as reported here:

[http://ubuntuforums.org/showthread.php?t=1417140](http://ubuntuforums.org/showthread.php?t=1417140)

---

### Post by moore.bryan on 2010-03-01
I don't know if this will help any of you, but in Fedora, the "ugly bars" at the bottom of the screen indicate Plymouth is *not* running and/or DRM isn't turned-on in the kernel. There's a definite way to do it with Intel cards, but I'm not sure there's a way with ATI or NVIDIA.

---

### Post by Owen.C93 on 2010-03-01
What advntage does plymouth bring? Should I just uninstall it or will boot be slow?

---

### Post by exploder on 2010-03-01
> What advntage does plymouth bring? Should I just uninstall it or will boot be slow?

I would not remove Plymouth, it defeats the whole purpose of testing.

---

### Post by Owen.C93 on 2010-03-01
> **exploder said:**
> I would not remove Plymouth, it defeats the whole purpose of testing.
Meh your rite. I have got a bug to track still and a couple of others in plymouth.

---

### Post by mc4man on 2010-03-01
Actually have come to find that with nvidia hardware atm plymouth presents no problems and can work. (at least my nvidia hardware

On the same desktop with 2 parallel installs - one using nvidia current, the other using nouveau

With nvidia-current plymouth doesn't work, but also presents no issues - the boot up shows blue bars and is slower by about 30%, though plymouth is not a factor in boot time

With nouveau plymouth works, both at boot and shutdown. What nouveau does do is shutdown and restart the monitor at the start of boot which is a bit strange.

Initally plymouth was just a the ubuntu icon, switching themes does work, though - It's there for so short a time as to seem irrelevant.

I'd think if plymouth is causing issues once at the desktop (at least for nvidia display adapters) then it's hardware specific, not a matter of for all.

Also on a  more recent laptop with nvidia plymouth causes no issues  (8400 Gs

(personally I tend to push the power button to get to the desktop, what happens in the 20 secs or so doesn't really matter nor do I tend to watch

---

### Post by VMC on 2010-03-01
> **forestpiskie said:**
> +1 to the lovely progress bars ...
I don't get any progress bars. I use to when I had Fedora installed.

Plymouth is installed and working but I get just the ubuntu logo on bootup and shutdown.

---

### Post by DoeRayMe on 2010-03-01
> **VMC said:**
> I don't get any progress bars. I use to when I had Fedora installed.

Plymouth is installed and working but I get just the ubuntu logo on bootup and shutdown.

Same here for the shutdown, boot up just shows a blinking cursur at the top, using radeon driver.

---

### Post by mc4man on 2010-03-01
> but I get just the ubuntu logo on bootup and shutdown.
Well you can fool around a bit with this.

After going thru them all I'd think some aren't quite working as intented, a couple seem to hang shutting down and the solar one  now works a bit better ( or at least is shown longer, 4-5 secs

Basically ( corrections if not right certainly welcome

Ex. (solar
to see list
> doug@doug-desktop:~$ sudo plymouth-set-default-theme --list
[sudo] password for doug: 
details
fade-in
glow
script
solar
spinfinity
text
ubuntu-logo
```

sudo plymouth-set-default-theme solar --rebuild-initrd
```

And then reboot

---

### Post by kansasnoob on 2010-03-02
Well I know if Plymouth is installed my boot screen staggers and rips just before it freezes. I recently installed Fedora 12 to test grub2 and it works if you can call a blueish progress bar at the bottom of the screen "working".

Fedora 12 boots slow as molasses. How is this blue progress bar a step forward? I think it's just ugly. If I remove plymouth from Lucid then I can boot OK but I'm back at about a 30 second boot time.

---

### Post by jppr on 2010-03-02
just upgraded to the new xorg and plymouth works well

---

### Post by DoeRayMe on 2010-03-02
> **jppr said:**
> just upgraded to the new xorg and plymouth works well

Seems the same for me, i have solar theme on atm, but theres no point tbh, it boots up so fast, i dont get to see anything good lol

---

### Post by VMC on 2010-03-02
> **mc4man said:**
> Well you can fool around a bit with this.

After going thru them all I'd think some aren't quite working as intented, a couple seem to hang shutting down and the solar one  now works a bit better ( or at least is shown longer, 4-5 secs

Basically ( corrections if not right certainly welcome

Ex. (solar
to see list

```

sudo plymouth-set-default-theme solar --rebuild-initrd
```

And then rebootThanks, I did the above command. While it has quite impressive color theme, it still doesn't bring any progress bars.

---

### Post by philinux on 2010-03-02
> **kansasnoob said:**
> Well I know if Plymouth is installed my boot screen staggers and rips just before it freezes. I recently installed Fedora 12 to test grub2 and it works if you can call a blueish progress bar at the bottom of the screen "working".

Fedora 12 boots slow as molasses. How is this blue progress bar a step forward? I think it's just ugly. If I remove plymouth from Lucid then I can boot OK but I'm back at about a 30 second boot time.

The progress bar is a fall back mechanism. It affects me with nvidia-current installed.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

Should get fixed in time I hope.

---

### Post by VMC on 2010-03-02
> **philinux said:**
> The progress bar is a fall back mechanism. It affects me with nvidia-current installed.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

Should get fixed in time I hope.

This is exactly how I remember Fedora working. If I removed their splash rhrg, then I had the blue progress bar at the bottom of the screen.

---

### Post by Uncle Spellbinder on 2010-03-02
Bunch of updates this morning. kernel, xorg, ubuntu-desktop and such. Still no plymouth, though. On boot I get the blue/white progress bar. On shutdown, I get the following text, not always though...

```
init: plymouth main process killed by TERM signal 
```

---

### Post by mc4man on 2010-03-02
It only works (to the extent it does) with nvidia hardware if you're using the nouveau driver, with nvidia drivers it doesn't - blue bars instead

---

### Post by Uncle Spellbinder on 2010-03-02
I currently am using nVidia current (195). Not tried nouveau, 

...and to be honest, I wasn't sure what nouveau was until I googled it. :oops:

In my hardware drivers, all I have available is nVidia 173 and nVidia Current. How do I use nouveau?


EDIT:

In Synaptic for ***xserver-xorg-video-nouveau***:
```
X.Org X server -- Nouveau display driver (experimental)

This driver for the X.Org X server (see xserver-xorg for a further description)
provides support for NVIDIA Riva, TNT, GeForce, and Quadro cards.

Although the nouveau project aims to provide full 3D support it is not yet
complete, and these packages do not include any 3D support.
Users requiring 3D support should use the non-free "nvidia" driver.

This package is built from the FreeDesktop.org xf86-video-nouveau driver.

Canonical provides critical updates for xserver-xorg-video-nouveau until March 2013.
```

---

### Post by Owen.C93 on 2010-03-02
I don't have the nouveau driver either. I looked in synaptic and it said I had something similar installed.

---

### Post by mc4man on 2010-03-02
Well you can take this with a large grain of salt so to speak - ultimately I've no interest in nouveau atm but...
To switch from nvidia-current to nouveau I disabled /removed the nvidia-current in hardware drivers, the  nvidia/Riva/TNT/Geforce was already green, rebooted into low graphics, then rebooted again into nouveau 

(probably more correct way..?

With nouveau this shows
> doug@doug-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: [COLOR="Blue"]Yes[/COLOR]
server glx vendor string: [COLOR="Blue"]SGI[/COLOR]
server glx version string: 1.4


Atm with  nouveau the positives - 
faster boot
some form of working plymouth
**highly superior to nv**

negatives ( without using a sketchy ppa
no 3d ( only use scroll on desktop here as far as effects
video playback is not as good as with nvidia, though close
nvidia offers better settings options
add. display options thru ccsm

---

### Post by Uncle Spellbinder on 2010-03-02
Thanks for the info. But I'll stick with nVidia myself. 

Hopefully the Plymouth issue can be addressed before Lucid final.

---

### Post by Owen.C93 on 2010-03-02
I get this error? 
```
xserver-xorg-video-nouveau:
 Depends: linux-backports-modules-nouveau-lucid-generic but it is not going to be installed or
     linux-backports-modules-nouveau-lucid-generic-pae but it is not going to be installed

```
Help anyone?

---

### Post by philinux on 2010-03-02
> **Uncle Spellbinder said:**
> On boot I get the blue/white progress bar.

That is plymouth. See post #39

---

### Post by CydeSwype on 2010-03-02
I'm stuck on the blue bars same as everyone else...but now and then they load extremely slow.  The bar eventually fills up with white but then hangs for several minutes (I didn't time it but it's still stuck there as I write this).

Is there any way to see what's going on?  Is it running an fsck or something (don't hear the hard drive cranking).  I just have to reboot (REISUB) and then I'm back where I started.  Any way to see what errors are occurring or do any diagnostics?  I guess I could boot with a live CD and fsck and reboot...but what a pain.

---

### Post by emarkay on 2010-03-02
Ixnay on the Ilimouthplay!

---

### Post by katie-xx on 2010-03-02
> **philinux said:**
> Nvidia 8600gt. 

3 fsck messages then...
Horrible blue/white progress bars at bottom of screen.

Plymouth is uninstalled for now with quiet removed so I can seen whats going on. I'll install it when I see a changelog that might indicate progress.
[SIZE=2]
Looks like I was a Jonah there. Id thought that problem hadnt happened with Ubuntu.
No improvement here with ATI graphics Im afraid but after tonight's downloads Im seriously impressed by the boot time.

Kate[/SIZE]

---

### Post by exploder on 2010-03-02
> No improvement here with ATI graphics Im afraid but after tonight's downloads Im seriously impressed by the boot time.

Boot time is pretty slow here, it takes forever for the desktop to load....

---

### Post by NightwishFan on 2010-03-02
When using Nouveau I see the splash on startup, but not on shutdown. Using the proprietary driver I get a black screen and sometimes my gdm is illegally resized, so I have to push enter and it will reset. When I can actually see it looks nice. I wish the normal frame buffer splash (bar at bottom) would work. When it does the boot is fast.

Edit: Nvidia 6150SE Nforce 430 (Yes its old and integrated)

---

### Post by DoeRayMe on 2010-03-02
This is my bootchart with plymouth enabled

---

### Post by NightwishFan on 2010-03-02
I can not seem to read it.

---

### Post by DoeRayMe on 2010-03-02
> **NightwishFan said:**
> I can not seem to read it.

jus download it and use image viewer and zoom in :P

---

### Post by NightwishFan on 2010-03-02
When I download, it is a tiny image, even when I open in a new tab. :o

---

### Post by DoeRayMe on 2010-03-02
> **NightwishFan said:**
> When I download, it is a tiny image, even when I open in a new tab. :o

Here ya go, i took a screen shot of the most important bits

---

### Post by godhika on 2010-03-02
It doesn't look like ureadhead is working. I have found while ureadahead is collecting new data, plymouth works just fine ( say like a kernel update or something like that) - but at the next boot, when ureadahead kicks in to reduce the boot time, all the well known problems appear. So I think the problem is not solely Plymouth alone, but it s interaction with ureadahead.

---

### Post by k3lt01 on 2010-03-03
> **godhika said:**
> It doesn't look like ureadhead is working. I have found while ureadahead is collecting new data, plymouth works just fine ( say like a kernel update or something like that) - but at the next boot, when ureadahead kicks in to reduce the boot time, all the well known problems appear. So I think the problem is not solely Plymouth alone, but it s interaction with ureadahead.ureadahead is a bottleneck to some systems, I know on my laptop it made the machine grind to a halt during bootup. I have tested this with and without Plymouth and Plymouth made no difference at all.

---

### Post by phenest on 2010-03-03
Hmmm, bit of progress here with nVidia GeForce 7950GTX. No more text messages but a blank screen instead (no progress bars), and then Xorg starts. But I still have that annoying 'Enter bug' where I'm sent back to the login screen. Grrr!

---

### Post by philinux on 2010-03-03
Got progress here.

I'm sticking with the nouveau driver as plymouth works and I only have to login once.

31.84 seconds boot time.

nVidia 8600gt. If I activate nvidia-current I get the plymouth fallack progress bars and have to login twice. So I'll track this bug for now.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

---

### Post by zika on 2010-03-03
What would be the proper way to turn ureadahead off? To edit/rename /etc/init/ureadahead.conf?

---

### Post by jppr on 2010-03-03
just updated new gdm and fix plymouth [https://launchpad.net/ubuntu/lucid/+source/gdm/2.29.6-0ubuntu4](https://launchpad.net/ubuntu/lucid/+source/gdm/2.29.6-0ubuntu4)

---

### Post by Uncle Spellbinder on 2010-03-03
> **jppr said:**
> just updated new gdm and fix plymouth [https://launchpad.net/ubuntu/lucid/+source/gdm/2.29.6-0ubuntu4](https://launchpad.net/ubuntu/lucid/+source/gdm/2.29.6-0ubuntu4)

Installed updates this morning. Among them, gdm. No change in Plymouth here. On boot, blue progress bar then login screen. On shutdown, I still get this...


```
init: plymouth main process (3547) killed by TERM signal
```

The number always changes.

---

### Post by ratcheer on 2010-03-03
I have never been able to boot Lucid, normally. I believe that ureadahead is what is causing my problem, too. I see a quickly disappearing message about it before my system starts making terrible noises.

I still have to boot Lucid by selecting recovery mode in grub, going to a root prompt, and starting gdm. It is slow, but it gets me there.

Tim

---

### Post by zika on 2010-03-03
> **ratcheer said:**
> I have never been able to boot Lucid, normally. I believe that ureadahead is what is causing my problem, too. I see a quickly disappearing message about it before my system starts making terrible noises.

I still have to boot Lucid by selecting recovery mode in grub, going to a root prompt, and starting gdm. It is slow, but it gets me there.

TimYou do not have to go to recovery mode ("**single**" in kernel line), just put "**text**" in kernel line and start gdm once You log-in with **sudo service gdm start && logout**.

---

### Post by jppr on 2010-03-03
I have /dev/sda1 10.04 + kubuntu-desktop and /dev/sdb1 windows 7, i don´t have any problem boot lucid or win7. There is some text with plymouth, but so what? ;) System start, boot and run well and that is all what I care

---

### Post by k3lt01 on 2010-03-03
If you are having difficulty and you believe ureadahead is the problem you are better of simply removing it (and sreadahead as well). There are a few threads on this, use the search function and read up on it if you want to.

---

### Post by zika on 2010-03-03
> **k3lt01 said:**
> If you are having difficulty and you believe ureadahead is the problem you are better of simply removing it (and sreadahead as well). There are a few threads on this, use the search function and read up on it if you want to.Or try 2.6.33 since it doesn't pull ureadahead...

---

### Post by k3lt01 on 2010-03-03
> **zika said:**
> Or try 2.6.33 since it doesn't pull ureadahead... I tried that and it stuffed my system.

---

### Post by katie-xx on 2010-03-03
[SIZE=2]We seem to be running dual threads here ..this one and the usplash one. Its getting hard to keep up :)
Maybe a kind mod would check if they are candidates for a merge?

Kate[/SIZE]

---

### Post by | MM | on 2010-03-03
> **philinux said:**
> nvidia 8600gt. 

3 fsck messages then...
Horrible blue/white progress bars at bottom of screen.


+1

---

### Post by MacUntu on 2010-03-04
Using Launchpad is *so* cool!

> No graphical splash on VGA16fb, plymouth uses fallback **blue ASCII progress bar**

[quote=Steve Langasek]
[...]
This is because plymouth doesn't support graphical output to a 4-bit framebuffer (VGA16). **Known issue**, expected to be resolved for Lucid.

Changed in plymouth (Ubuntu): 
milestone: 	none &#8594; **ubuntu-10.04-beta-1**[/quote]

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

---

### Post by k3lt01 on 2010-03-04
> **phenest said:**
> Hmmm, bit of progress here with nVidia GeForce 7950GTX. No more text messages but a blank screen instead (no progress bars), and then Xorg starts. But I still have that annoying 'Enter bug' where I'm sent back to the login screen. Grrr!

> **philinux said:**
> Got progress here.

I'm sticking with the nouveau driver as plymouth works and I only have to login once.

31.84 seconds boot time.

nVidia 8600gt. If I activate nvidia-current I get the plymouth fallack progress bars and have to login twice. So I'll track this bug for now.
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

I just fixed my double logging in issue. I removed bootchart and pybootchart or whatever it was called and now the issue is fixed.

---

### Post by zika on 2010-03-04
> **k3lt01 said:**
> I tried that and it stuffed my system.Sorry to hear that. It works fine here...

---

### Post by k3lt01 on 2010-03-04
> **zika said:**
> Sorry to hear that. It works fine here...I think there may have been a few other issues at play. I just spent a few hours fixing a huge breakage after a "safe-upgrade". Lucid has been slow for me for over a week, double booting, pathetic internet and a fair few other problems but today it broke badly. After going into recovery and dpkg-ing numerous times I finally got it running.

Note that ureadahead and plymouth cannot be blamed for this breakage but I think bootchart and pybootchartgui were some of the issue. All I know is it seems to be working as it should now.

---

### Post by kansasnoob on 2010-03-04
Well I reinstalled Plymouth this AM and I no longer get the "tearing" followed by freezing, and boot speed is quite fast, about 18 to 19 seconds :)

Still just the blue/white progress bar, and occasionally the first bar will jump upwards with a second bar below it, and sometimes even do the same again so I'll have 3 progress bars by the time I get to gdm. 

The bars that stop and jump upwards always say something like, "exit blah-blah status 4", it goes so quickly it's nearly impossible to read.

---

### Post by k3lt01 on 2010-03-04
@ Kansas, is it possible to do a freeze screen so you can catch the error messages? Not that it seems really important cause it is still working anyway.

---

### Post by VMC on 2010-03-04
> **k3lt01 said:**
> @ Kansas, is it possible to do a freeze screen so you can catch the error messages? Not that it seems really important cause it is still working anyway.

Try Ctrl+s . The key combination of Ctrl+s, Ctrl+q work together.

---

### Post by katie-xx on 2010-03-04
[SIZE=2]News from the ATI front (3400 Mobility) is still poor Im afraid :)
I now have a swish purple screen on shutdown. It looks really nice.
However, I still have the two log ins required problem on boot and all I see is a flashing cursor.

Kate
[/SIZE]

---

### Post by exploder on 2010-03-04
I just switched back to the open source drivers for my nvidea card and Plymouth displays now on shut down and re-start, it's still not showing at start up though. 

For now I guess we will have to wait and see if updates resolve the problems.

---

### Post by michy99 on 2010-03-04
I am running an old Pentium III box with Intel 82815 Chipset Graphics Controller. At boot I get the blue and white progress bars which are interrupted several times with text messages which are covered by the bars before I can read them. Then the monitor goes into stand-by and everything stops. I press the enter key and boot continues with the log-in screen.

I suspect that my hardware is just too old for Plymouth, so I have removed it for now.

---

### Post by kansasnoob on 2010-03-04
Scratching my head????????????

I'm totally unclear on what to do here:

> @ Kansas, is it possible to do a freeze screen so you can catch the error messages? Not that it seems really important cause it is still working anyway.

This confuses me even more:

> Try Ctrl+s . The key combination of Ctrl+s, Ctrl+q work together.

I mean I know what it does, so what am I trying to accomplish?

As I've said Fedora 12 does the same thing, so it seems like my P4/M800 can't get no love ;)

That sucks because I've built a lot of low end puters with boards that have that gpu. Thirty + but at least I'm not getting the X freezes I did with Karmic :D

---

### Post by k3lt01 on 2010-03-04
> **kansasnoob said:**
> Scratching my head????????????

I'm totally unclear on what to do here:

This confuses me even more:

I mean I know what it does, so what am I trying to accomplish?What you would be trying to accomplish is finding what the errors are that are being reported. Considering they flash by to quickly for you to read them you will need somehow to slow it down or stop it long enough to read it. Then if you feel like it you can post the info here and we could go through it and see if it is anything that is of any concern.

All this is posted going by the assumption that you would like to know what it is because you posted about it in the first place.

---

### Post by PRGUY85 on 2010-03-04
> **michy99 said:**
> I am running an old Pentium III box with Intel 82815 Chipset Graphics Controller. At boot I get the blue and white progress bars which are interrupted several times with text messages which are covered by the bars before I can read them. Then the monitor goes into stand-by and everything stops. I press the enter key and boot continues with the log-in screen.

I suspect that my hardware is just too old for Plymouth, so I have removed it for now.

Have same problems on my Dell XPS M1210 using Geforce 7400. Worked on Nouveau default but switched to Nvidia's drivers which I use all the time on Ubutnu and now getting blue progress bars, reminding me of the same problem I had using Fedora.

---

### Post by Digital Hick on 2010-03-04
I have *yet* to see the new startup or shutdown screens.  All I get is Plymouth progress bars across the bottom on startup and nothing on shutdown.  :sad:

Periodically, I will see the bars flashing like crazy and a **[C]** in the middle of the screen while it is booting.  Even after tonights updates, nothing.  I have the new background and theme.  But nothing on startup or shutdown.  It has been like this for weeks.

By the way.  The new theme does not work with open office.  You can not read any of the drop down menus when set to Ambiance.  So that needs fixed.  

The login screen after the first reboot was nearly all white.  You could not read the text or hardly see the white Ubuntu logo.

Also, should there still be a menu button in the upper left corner of the windows, because I do not see one any more?  Nothing there to click on.  No response to the mouse.

Tooltips do not always have rounded edges either.  Minor issue.

It is worth noting that I am running this in VirtualBox 3.1.4.  And I can tell you 3.1.2 did not like Lucid at all.  And I think some of it was Plymouth. :sad:

Have not tried drivers yet, VB addons or otherwise.  I want to see what vanilla looks like before I go changing it.;)

In spite of all this bad news here is the good news.  10.04 is very stable for only being at Alpha 3.  And they have nearly 2 months to polish it since today was the UI freeze. :popcorn:

This opinion may not be shared by many, but if they have to push this back to make it really, **REALLY**, bug free and slick, I can live with a 10.05.  Just a thought.  6.04 became 6.06 after all.  I get the sense that people, beyond the Ubuntu community, are hoping this one really hits it out of the park.  [-o<

---

### Post by theanswriz42 on 2010-03-04
> **Digital Hick said:**
> 

This opinion may not be shared by many, but if they have to push this back to make it really, **REALLY**, bug free and slick, I can live with a 10.05.  Just a thought.  6.04 became 6.06 after all.  I get the sense that people, beyond the Ubuntu community, are hoping this one really hits it out of the park.  [-o<

Your opinion is shared by plenty of people. Stability is worth far more than nifty gadgetry that might only work for 10% of the users.

---

### Post by kansasnoob on 2010-03-04
I've been doing some major repartitioning to test "parted" in Lucid so I've also been restarting a lot to see if the changes hosed anything.

What I've found is that the "ripping and tearing" in Plymouth occurs during a fsck. The same occurs in Fedora 12 so it's purely a Plymouth thing, perhaps somewhat hardware related.

But with a 20 second boot time I could care less if it flips me the bird :D

---

### Post by DoeRayMe on 2010-03-04
> **kansasnoob said:**
> But with a 20 second boot time I could care less if it flips me the bird :D

Thats true, the boot speed is alot faster than previous versions, so your not going to see 'much' of it anyway :)

btw love that saying haha :D

---

### Post by tito_torrisi on 2010-03-05
When I try to use 2.6.33 Kernel, nouveau doesn't work anymore. Is there something I have to do to get nouveau to load (?) again? (resolution is broken, looks like with nv on my 9400M)

---

### Post by travisat on 2010-03-05
I currently believe I have plymouth working using the NVIDIA proprietary drivers.  I had to change some grub stuff to get framebuffer support on boot.  If anybody wants to see if this helps here is what I did:

in /etc/default/grub uncomment GRUB_GFXMODE= and put in your main displays resolution, I used 1440x900 so it looks like GRUB_GFXMODE=1440x900, this is on line 18 for me.

in /etc/grub.d/00_header find the line that says set 

gfxmode=${GRUB_GFXMODE}  

on my computer it is line 103, directly underneath this line add the line

 set gfxpayload=keep

then run sudo update-grub.  I assume it is working as I have the ubuntu logo on boot up and shut down.

**Edit: you still have to login twice

---

### Post by Atermoon on 2010-03-05
> **travisat said:**
> I currently believe I have plymouth working using the NVIDIA proprietary drivers.  I had to change some grub stuff to get framebuffer support on boot.  If anybody wants to see if this helps here is what I did:

in /etc/default/grub uncomment GRUB_GFXMODE= and put in your main displays resolution, I used 1440x900 so it looks like GRUB_GFXMODE=1440x900, this is on line 18 for me.

in /etc/grub.d/00_header find the line that says set 

gfxmode=${GRUB_GFXMODE}  

on my computer it is line 103, directly underneath this line add the line

 set gfxpayload=keep

then run sudo update-grub.  I assume it is working as I have the ubuntu logo on boot up and shut down.

**Edit: you still have to login twice

Thaks, that worked for me with the nvidia-current driver although Plymouth appears about 100 pixels on the left of the screen. My tty's too. I only had to login once though.

Edit: changed the resolution from 1280x1024 to 1024x768. Now the image is centered (fills the screen) and I can read my tty's but when I get to GDM and hit enter X restarts. After that everything's ok.

---

### Post by travisat on 2010-03-05
Well when I first did it I only had to login once, the last time I rebooted I had to login twice.  Earlier in this thread there was an updated gdm.  Hopefully when that gets out to the repo it will fix it.  I think that gdm might be booting to quick and the framebuffer is corrupting the display.  I remember having problems with the framebuffer like this several years ago on a different machine where if the framebuffer was enabled the display manager occasionally had video corruption.  

Also this fix probably cannot be included unless you default to 640x480 or 800x600 for the framebuffer since monitor resolution is not standard.

---

### Post by tito_torrisi on 2010-03-05
> **travisat said:**
> I currently believe I have plymouth working using the NVIDIA proprietary drivers.  I had to change some grub stuff to get framebuffer support on boot.  If anybody wants to see if this helps here is what I did:

in /etc/default/grub uncomment GRUB_GFXMODE= and put in your main displays resolution, I used 1440x900 so it looks like GRUB_GFXMODE=1440x900, this is on line 18 for me.

in /etc/grub.d/00_header find the line that says set 

gfxmode=${GRUB_GFXMODE}  

on my computer it is line 103, directly underneath this line add the line

 set gfxpayload=keep

then run sudo update-grub.  I assume it is working as I have the ubuntu logo on boot up and shut down.

**Edit: you still have to login twice

I don't understand how it should work with nvidia drivers, because they don't support KMS. I thought the correct Plymouth experience needs KMS! Without it you cannot have the correct resolution before starting xserver!

---

### Post by travisat on 2010-03-05
> **tito_torrisi said:**
> I don't understand how it should work with nvidia drivers, because they don't support KMS. I thought the correct Plymouth experience needs KMS! Without it you cannot have the correct resolution before starting xserver!

To be completely honest I have no idea.  I changed that setting because I thought it was just xsplash or usplash and wasn't plymouth, but it seems to be working.  You can have the correct resolution with grub by setting the grub resolution then passing that resolution to the kernel, this used to be done separately with a vga kernel option, but grub2 does it a little different.  There is also a way to pass a different resolution than the grub resolution for monitors that don't have a resolution that grub supports.  It is slightly more complex.

**edit: just found information that plymouth will work with a vesa fb.  Since ubuntu has the kernel and grub set to not display text before the framebuffer kicks in it is almost like you have kms.

---

### Post by rudihawk on 2010-03-05
> **philinux said:**
> Nvidia 8600gt. 

3 fsck messages then...
Horrible blue/white progress bars at bottom of screen.

Plymouth is uninstalled for now with quiet removed so I can seen whats going on. I'll install it when I see a changelog that might indicate progress.

I get the same thing!

---

### Post by moore.bryan on 2010-03-05
> **godhika said:**
> It doesn't look like ureadhead is working. I have found while ureadahead is collecting new data, plymouth works just fine ( say like a kernel update or something like that) - but at the next boot, when ureadahead kicks in to reduce the boot time, all the well known problems appear. So I think the problem is not solely Plymouth alone, but it s interaction with ureadahead.

> **k3lt01 said:**
> ureadahead is a bottleneck to some systems, I know on my laptop it made the machine grind to a halt during bootup. I have tested this with and without Plymouth and Plymouth made no difference at all.
Some people have written in other threads about ureadahead and sreadahead's main development being for solid states drives, which may explain the lag on some "traditional" drives.

---

### Post by shafin on 2010-03-05
My plymouth got fixed with a simple stupid check :D
In early phases of lucid cycle, I was getting problems with boot, so deleted the word 'splash' from my grub entry. After that I completely forgot it and had to check out everything to get plymouth working.

---

### Post by VMC on 2010-03-05
> **shafin said:**
> My plymouth got fixed with a simple stupid check :D
In early phases of lucid cycle, I was getting problems with boot, so deleted the word 'splash' from my grub entry. After that I completely forgot it and had to check out everything to get plymouth working.

I had a bug report that revealed I also removed 'splash'. Apparently though it still should have worked. As far as booting up goes.

Explained here:
[bug#521175_comment#26]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/521175/comments/26")

---

### Post by katie-xx on 2010-03-05
[SIZE=2]Well things are certainly changing. Unfortunately they seem to be getting worst.
Every boot now takes two log in attempts to get to the desktop.
A horrible washed out purple background has appeared at the log in screen and I cant find how to disable it.
Ive tried a vesa frame buffer which worked for some people in Fedora but unfortunately no success.
The boot time is now much longer than ever it was before tonight ...but hey I guess some people like watching a blinking cursor.:)
To be honest this seems to be an even worst mess than was the case in Fedora. I do remain hopeful as we are still at the Alpha stage but I dont think its a good sign that additional themes and art work are being rolled out while this is still such an issue.
Anyone else with good news about Plymouth ..... to lift me from my depression :)

Kate
[/SIZE]

---

### Post by grubdude on 2010-03-05
I think for now it is just Zanax for the depression :-)

---

### Post by sgage on 2010-03-05
katie,

it's just part and parcel of alpha testing ;)

grubdude - best handle ever.

---

### Post by katie-xx on 2010-03-05
> **sgage said:**
> katie,

it's just part and parcel of alpha testing ;)

grubdude - best handle ever.
[SIZE=2]
Yes I know .. its just that I had ever such a bad time with Plymouth in Fedora that Ive probably got it all out of proportion :)
it would just be so brilliant if ubuntu devs could get this working.

Kate
[/SIZE]

---

### Post by grubdude on 2010-03-05
Thanks sgage!;)

---

### Post by teh603 on 2010-03-05
> **DoeRayMe said:**
> Thats true, the boot speed is alot faster than previous versions, so your not going to see 'much' of it anyway :)

btw love that saying haha :DTo be honest, I only get a 20 second boot time with Plymouth removed. With it installed, it takes forEVAR, compared to booting Jaunty in safe graphics mode.

What was so wrong with the old bootsplash anyway?

---

### Post by sgage on 2010-03-05
"it would just be so brilliant if ubuntu devs could get this working."

katie, it WILL be brilliant, because you just know they're going to get it sorted. 

I get frustrated with these things as much as anybody, but then I remember the incredibly ridiculous number of hardware combinations out there, and I think "alpha alpha alpha" and I feel much better. ;)

---

### Post by rtalcott on 2010-03-05
I have an ecs a740gm-m...onboard AMD graphics and it appears (plymouth) to work on boot and shutdown...actually boots quicker than it did previously...the gf8100vm-m3 with nvidia graphics....well..it boots.  I guess I am having limited success.
rt

---

### Post by novafluxx on 2010-03-06
Has Ubuntu decided to ditch Usplash and go with Plymouth? I haven't heard anything about that, can someone point me to that post/mailing list post?

---

### Post by cariboo on 2010-03-06
@novafluxx

Have a look [here]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-boot-experience").

---

### Post by infoseeker on 2010-03-06
I have never seen a hint of graphics of any type whatsoever during bootup, other than that nasty bar across the bottom, but then my login (KDM) works flawlessly.  I presume Kubuntu will eventually get plymouth and KDE to work together at some time or other.   It IS installed, btw.

---

### Post by Atermoon on 2010-03-06
> **infoseeker said:**
> I have never seen a hint of graphics of any type whatsoever during bootup, other than that nasty bar across the bottom, but then my login (KDM) works flawlessly.  I presume Kubuntu will eventually get plymouth and KDE to work together at some time or other.   It IS installed, btw.

What video card do you have?

---

### Post by NightwishFan on 2010-03-06
Working fine on Intel chip of my laptop.

---

### Post by cookiecruncher on 2010-03-06
> **Atermoon said:**
> What video card do you have?

Nvidia 9600GT, Core2Duo E7400, 3GB RAM

Running 195.36.08 driver.
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

---

### Post by Atermoon on 2010-03-06
[http://ubuntuforums.org/showpost.php?p=8919056&postcount=92](http://ubuntuforums.org/showpost.php?p=8919056&postcount=92)

Worked for me.

---

### Post by moore.bryan on 2010-03-06
Has anyone noticed the beautiful new Ubuntu Plymouth start-up pushed-out in the past 24-hours?

---

### Post by NightwishFan on 2010-03-06
I got to see it before I switched over to Debian, it is pretty awesome.

---

### Post by PRGUY85 on 2010-03-06
> **Atermoon said:**
> [http://ubuntuforums.org/showpost.php?p=8919056&postcount=92](http://ubuntuforums.org/showpost.php?p=8919056&postcount=92)

Worked for me.

Worked for me too.

---

### Post by kansasnoob on 2010-03-06
> **PRGUY85 said:**
> Worked for me too.

Ditto! And I use the VIA openchrome driver :)

Looks nice and auto-login is working again. Looks awesome. Just to clarify I removed the **[COLOR="Red"]#[/COLOR]** in "/etc/default/grub" that I've highlighted in red but I left the resolution set at the default (I'll explain why later):

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="60"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX="splash quiet"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**[COLOR="Red"]#[/COLOR]GRUB_GFXMODE=640x480**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

Then in "/etc/grub.d/00_header" I added the line highlighted in red (you'll notice I highlighted another line in bold black, more about that later):

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`
locale_dir=`echo /boot/grub/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d _ -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
**if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi**

cat << EOF
if [ -s \$prefix/grubenv ]; then
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  set saved_entry=\${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z \${boot_once} ]; then
    saved_entry=\${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n \${have_grubenv} ]; then if [ -z \${boot_once} ]; then save_env recordfail; fi; fi
}
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  **[COLOR="Red"]set gfxpayload=keep[/COLOR]**
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

# Gettext variables and module
if [ "x${LANG}" != "xC" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir})
  cat << EOF
set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
set lang=${grub_lang}
insmod gettext
EOF
fi

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

```

Then I just ran "update-grub". The result was sweeeeeeeeet :D Oh I still get the fsck delay w/text for a few seconds but no more ugly blue/white bars!

I left the resolution at the default (640x480) because of that other highlighted line:

> if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi


I'll try to study about that a bit more later.

---

### Post by exploder on 2010-03-06
kansasnoob, have you added this information to the bug report? This is some very good information. :)

---

### Post by kansasnoob on 2010-03-06
> **exploder said:**
> kansasnoob, have you added this information to the bug report? This is some very good information. :)

No. It's not really "my" solution, just something I learned in this thread. I posted a question for Dave over in his Grub2 Basics HowTo about the resolution thing:

[http://ubuntuforums.org/showpost.php?p=8925426&postcount=350](http://ubuntuforums.org/showpost.php?p=8925426&postcount=350)

640x480 results in a very large (but nice) logo. I just know there are a gazillion interdependencies between all of the various Grub2 scripts so I left the resolution at the default until I can study that more.

---

### Post by travisat on 2010-03-06
> **kansasnoob said:**
> No. It's not really "my" solution, just something I learned in this thread. I posted a question for Dave over in his Grub2 Basics HowTo about the resolution thing:

[http://ubuntuforums.org/showpost.php?p=8925426&postcount=350](http://ubuntuforums.org/showpost.php?p=8925426&postcount=350)

640x480 results in a very large (but nice) logo. I just know there are a gazillion interdependencies between all of the various Grub2 scripts so I left the resolution at the default until I can study that more.

On that post you don't have to change that extra bold, if you just chnage the GFX_MODE in /etc/default/grub and update-grub it will change your grub resolution.

---

### Post by Tompalaz on 2010-03-07
Anyone else just gets a blank screen, no plymouth or fallback progress bars?

9400M using nouveau drivers from xorg-edgers.
edit: It shows up if I run 
> plymouthd
plymouth --show-splash

---

### Post by kansasnoob on 2010-03-07
> **travisat said:**
> On that post you don't have to change that extra bold, if you just chnage the GFX_MODE in /etc/default/grub and update-grub it will change your grub resolution.

Cool :)

That also changes the size of the grub menu, so a blind old fart like me is better off with the default 640x480. It's still a pleasant splash and a 19.2 second boot time.

---

### Post by NCLI on 2010-03-07
Regardless of who came up with the solution, please add it to the bug report ;)

---

### Post by kansasnoob on 2010-03-07
> **NCLI said:**
> Regardless of who came up with the solution, please add it to the bug report ;)

I'm still in "thimking mode" :p

I pretty much know now that changing resolution is probably not desirable if someone is happy with their present grub menu size. So it comes down to just removing that one comment in "/etc/default/grub" and adding one line to "/etc/grub.d/00_header", but I'm thinking it would be wise to instruct most users to first back up both of those files.

So I'm reviewing some grub2 notes and I think those would remain executable after renaming so you'd need to remove the executable bit after renaming, eg:

sudo cp /etc/default/grub /etc/default/grub_backup
sudo chmod -x /etc/default/grub_backup

Then if necessary to restore the backup:

sudo rm /etc/default/grub
sudo mv /etc/default/grub_backup /etc/default/grub
sudo chmod +x /etc/default/grub

But as I said I'm still just pondering this, I like to test and retest something before I put it in print :)

---

### Post by gibbylinks on 2010-03-07
Wow I didn't realise those dodgy blue bars were intended to be this. Brilliant. Your solution works a treat, now if I could just sort this soddin' double login bug

:popcorn:

---

### Post by philinux on 2010-03-07
> **infoseeker said:**
> I have never seen a hint of graphics of any type whatsoever during bootup, other than that nasty bar across the bottom, but then my login (KDM) works flawlessly.  I presume Kubuntu will eventually get plymouth and KDE to work together at some time or other.   It IS installed, btw.

The nasty progress bar is Plymouth. It's it's fall back system of ascii progress bar.

I dont do workarounds. If you do how will you know it's fixed through an update?

I've reverted to the nouveau driver for now with Plymouth installed and it works. It fails with nvidia-current.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

---

### Post by kansasnoob on 2010-03-07
OK as far as I can tell "/etc/default/grub" is NOT an executable file but "/etc/grub.d/00_header" IS executable. You can see the difference here:

```
lance@lance-desktop:~$ ls -l /etc/default/grub
**[COLOR="Red"]-rw-r--r-- 1[/COLOR]** root root 802 2010-03-07 06:51 /etc/default/grub
lance@lance-desktop:~$ ls -l /etc/grub.d/00_header
**[COLOR="Red"]-rwxr-xr-x 1[/COLOR]** root root 3957 2010-03-06 09:07 /etc/grub.d/00_header

```

I'd appreciate if someone else would verify that by running these two commands and posting the results:

```
ls -l /etc/default/grub
ls -l /etc/grub.d/00_header
```

Just FYI the reason I want to figure this out is so we can have a CLI rescue plan in case someone improperly edits something or if the changes somehow leaves them unable to boot ;)

Always expect and prepare for the worst, eh?

---

### Post by cookiecruncher on 2010-03-07
> **Atermoon said:**
> [http://ubuntuforums.org/showpost.php?p=8919056&postcount=92](http://ubuntuforums.org/showpost.php?p=8919056&postcount=92)

Worked for me.

Was not a good suggestion for me.  On rebooting ended up with 'out-of-sync' error from my monitor where GRUB was supposed to be (my monitor's default resolution IS 1440x900 btw).  The Debian LXDE live CD I had did not support ext4, so that was useless in an attempt to do repair work.  Fortunately I had a PMAGIC 4.7 CD lying around and using this I managed to edit the '/boot/grub.cfg' file (reverted the 1440x900 line back to 800x600 and hashed out the payload entry), so I am back to black screen where plymouth is meant to be.

---

### Post by VMC on 2010-03-07
> lance@lance-desktop:~$ ls -l /etc/default/grub
-rw-r--r-- 1 root root 802 2010-03-07 06:51 /etc/default/grub
lance@lance-desktop:~$ ls -l /etc/grub.d/00_header
-rwxr-xr-x 1 root root 3957 2010-03-06 09:07 /etc/grub.d/00_header

@kansasnoob, My permissions are exactly like yours.

---

### Post by kansasnoob on 2010-03-07
> **philinux said:**
> The nasty progress bar is Plymouth. It's it's fall back system of ascii progress bar.

I dont do workarounds. If you do how will you know it's fixed through an update?

I've reverted to the nouveau driver for now with Plymouth installed and it works. It fails with nvidia-current.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

It also fails with the openchrome drivers.

I always just revert my workarounds about once a week, or when updates make me curious, to see if things are fixed.

---

### Post by kansasnoob on 2010-03-07
**[COLOR="Red"]Please consider this caution[/COLOR]** from Steve Langasek before proceeding:

> From what I've seen, modifying the grub config as you describe causes
the kernel to use the EFI driver as the default framebuffer instead of
VGA16. This will work for some, may fail entirely for others (i.e.,
those on non-EFI systems), and could result in regressions down the line
due to use of this non-default framebuffer module. 

Kudos to Travisat for the nifty work-around:

[http://ubuntuforums.org/showpost.php?p=8919056&postcount=92](http://ubuntuforums.org/showpost.php?p=8919056&postcount=92)

The only part of that that didn't work for me was changing the resolution (my desktop res is 1440x900 on a 22" widescreen) because it resulted in a very tiny grub menu, so I changed it back to it's native 640x480.

I decided to write this because I wanted to offer a method by which a person could "revert" via CLI if something should go awry and leave a machine unbootable. The **method to revert** should also work in a chroot if need be:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

First we'll create backups of "/etc/default/grub" and "/etc/grub.d/00_header" and make "/etc/grub.d/00_header_backup" non-executable just in case something goes awry and leaves you unbootable (I'll explain how to restore the backups at the very end) by running the three following commands:

```
sudo cp /etc/default/grub /etc/default/grub_backup
```

```
sudo cp /etc/grub.d/00_header /etc/grub.d/00_header_backup
```

```
sudo chmod -x /etc/grub.d/00_header_backup
```

You can verify your backups by running "ls /etc/default" and "ls /etc/grub.d".

```
**ls /etc/default**
acpid            cacerts        grub~          jackd       rsync
acpi-support     console-setup  **[COLOR="Red"]grub_backup[/COLOR]**    kdm.d       rsyslog
alsa             cron           grub.ucf-dist  kerneloops  saned
apport           cups           grub.ucf-old   locale      speech-dispatcher
bootlogd         dbus           halt           ntpdate     tmpfs
brltty           devpts         hddtemp        pulseaudio  ufw
brltty.dpkg-old  **[COLOR="Red"]grub[/COLOR]**           irqbalance     rcS         useradd

```
```
**ls /etc/grub.d**
**[COLOR="Red"]00_header[/COLOR]**         05_debian_theme  20_memtest86+  40_custom
**[COLOR="Red"]00_header_backup[/COLOR]**  10_linux         30_os-prober   README
```

**[COLOR="Red"]You should[/COLOR]** also verify that "/etc/grub.d/00_header" is executable, but that "/etc/grub.d/00_header_backup" is **NOT** executable by running:

```
ls -l /etc/grub.d/00_header
```

```
ls -l /etc/grub.d/00_header_backup
```

The difference is obvious:

```
lance@lance-desktop:~$ ls -l /etc/grub.d/00_header
**[COLOR="Red"]-rwxr-xr-x[/COLOR]** 1 root root 3957 2010-03-06 09:07 /etc/grub.d/00_header
lance@lance-desktop:~$ ls -l /etc/grub.d/00_header_backup
**[COLOR="Red"]-rw-r--r--[/COLOR]** 1 root root 3957 2010-03-07 10:03 /etc/grub.d/00_header_backup
```

Now we'll edit "/etc/default/grub" and "/etc/grub.d/00_header" using gedit and then "update-grub":

```
gksu gedit /etc/default/grub
```

Now **remove the comment "#"** that I've highlighted in red here **[COLOR="Red"](You must "uncomment" only that line!)[/COLOR]**:

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="60"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX="splash quiet"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**[COLOR="Red"]#[/COLOR]GRUB_GFXMODE=640x480**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

```

Be sure to click on Save, then File > Quit, and next:

```
gksu gedit /etc/grub.d/00_header
```

And **add the line** I've highlighted in red here **[COLOR="Red"](NOTE: it must be in the proper location!)[/COLOR]**:

```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`
locale_dir=`echo /boot/grub/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d _ -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  set saved_entry=\${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z \${boot_once} ]; then
    saved_entry=\${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n \${have_grubenv} ]; then if [ -z \${boot_once} ]; then save_env recordfail; fi; fi
}
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
  set gfxmode=${GRUB_GFXMODE}
  **[COLOR="Red"]set gfxpayload=keep[/COLOR]**
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

# Gettext variables and module
if [ "x${LANG}" != "xC" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir})
  cat << EOF
set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
set lang=${grub_lang}
insmod gettext
EOF
fi

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

```

Again be sure to click on Save, then File > Quit, and now we'll apply the changes:

```
sudo update-grub
```

**[COLOR="Red"]Wait for it to say done[/COLOR]**, then reboot and hopefully enjoy Plymouth.

*******************************************************************
*******************************************************************
*******************************************************************

**[COLOR="Red"]Only if things went wrong[/COLOR]** and you need to restore the backups via CLI:

```
sudo rm /etc/default/grub

```
```
sudo mv /etc/default/grub_backup /etc/default/grub
```

```
sudo rm /etc/grub.d/00_header
```

```
sudo mv /etc/grub.d/00_header_backup /etc/grub.d/00_header
```

```
sudo chmod +x /etc/grub.d/00_header
```

**[COLOR="Red"]I'd recommend[/COLOR]** checking to be sure "/etc/grub.d/00_header" is executable as shown previously:

```
ls -l /etc/grub.d/00_header
```

Then be sure to "update-grub":

```
sudo update-grub
```

Again be sure to **[COLOR="Red"]wait for it to say done[/COLOR]**.

---

### Post by NightwishFan on 2010-03-07
Great post! =D>

---

### Post by tad1073 on 2010-03-07
@kansasnoob, I have my desktop res set to 1680x1050 and my my grub menu set to 1024x768 which is a perfect size for me, it is readable and looks nice. And I am using the default wallpaper for 10.04 as a background, reminds me of mike & ike candies :lolflag:[]("http://ubuntuforums.org/member.php?u=554595")

---

### Post by kansasnoob on 2010-03-07
> **NightwishFan said:**
> Great post! =D>

Thanks. I try to remember what it was like for me 2 years ago when I had to ask, "where's the terminal" :lolflag:

Quite often we take for granted that people know what we know and even here in the testing forum we need to remember we all have different levels of understanding and expertise with certain "parts & pieces" of the OS.

I also always try to include a way to easily revert any changes if said changes leave someone unable to boot. All that said I was also having this problem with Fedora 12 and found this:

[http://www.my-guides.net/en/content/view/125/26/1/12/#plymouth](http://www.my-guides.net/en/content/view/125/26/1/12/#plymouth)

Look at the **Graphical Boot Problem** section. It worked for me :)

My point in mentioning that is that Fedora 12 came out in November and since it effects both Nvidia and openchrome it may take quite a while to work out the wrinkles - I'm cool with that ;)

---

### Post by kansasnoob on 2010-03-07
> **tad1073 said:**
> @kansasnoob, I have my desktop res set to 1680x1050 and my my grub menu set to 1024x768 which is a perfect size for me, it is readable and looks nice. And I am using the default wallpaper for 10.04 as a background, reminds me of mike & ike candies :lolflag:[]("http://ubuntuforums.org/member.php?u=554595")

I'm sure it depends on both the GPU and monitor, even with this 22" wide-screen it's a comfortable fit, the Plymouth boot is really attractive. 

I am a bit curious what the "refresh rate" is during boot, I've always wondered how to see that, I'd hate to think that it's above 61Hz. I've never smelled anything burning :P

I can't get over the boot speed, it's like WHOOSH! The last I clocked was 18.1 seconds from the time I hit the enter key after selecting my OS of choice. It then takes about 5 seconds longer for the Desktop to become responsive.

In comparison Fedora 12 takes just over one minute, Hardy is about the same, Jaunty is decent at about 42 to 43 seconds.

---

### Post by sparker256 on 2010-03-07
> **tad1073 said:**
> @kansasnoob, I have my desktop res set to 1680x1050 and my my grub menu set to 1024x768 which is a perfect size for me, it is readable and looks nice. And I am using the default wallpaper for 10.04 as a background, reminds me of mike & ike candies :lolflag:[]("http://ubuntuforums.org/member.php?u=554595")

Thank you all. I also have my desktop set to 1680x1050 and set my grub menu and grub image to 1024x768. I am now getting to see what plymouth is supposed to look like not the ugly blue and white bar. I had to get my monitor res check to not pop up and all is good now. I have a delay after I have selected my os before I see plymouth. Not sure if that is correct or not but I do not have quiet turned on at this time.

Bill

---

### Post by katie-xx on 2010-03-07
Im afraid this doesnt do the trick on my ATI kit.
My Sony running on Intel chip has been ok from day 1 but ATI ...no go sorry.

Is it important? Some people have asked does a splash screen matter. IMHO its very important for the obvious reason its the first thing anyone sees. I would also imagine not many people will be pleased at having to log in twice each time.

On that basis, I would argue in an Alpha release it just isnt sensible to be doing work arounds as the problem will never get fixed. That would be a great pity.


Kate

---

### Post by philinux on 2010-03-07
> **katie-xx said:**
> 
Some people have asked does a splash screen matter. IMHO its very important for the obvious reason its the first thing anyone sees. 

I would argue in an Alpha release it just isnt sensible to be doing work arounds.


Kate
+1 
and

+1

---

### Post by MacUntu on 2010-03-07
> **katie-xx said:**
> as the problem will never get fixed

It will, target is Beta 1 (see bug report).

---

### Post by Uncle Spellbinder on 2010-03-07
> **katie-xx said:**
> ...I would argue in an Alpha release it just isnt sensible to be doing work arounds as the problem will never get fixed. That would be a great pity.
So perfectly said.

With the exception of installing apps and such, Lucid remains as it was upon initial install, meaning free of any work-arounds at all. Otherwise, how could I report a bug if I've used a work-around? Or how would I know if a bug has been fixed if I've employed a work-around?

Work-arounds in testing builds never made sense to me.

---

### Post by kansasnoob on 2010-03-07
> **katie-xx said:**
> Im afraid this doesnt do the trick on my ATI kit.
My Sony running on Intel chip has been ok from day 1 but ATI ...no go sorry.

Is it important? Some people have asked does a splash screen matter. IMHO its very important for the obvious reason its the first thing anyone sees. I would also imagine not many people will be pleased at having to log in twice each time.

On that basis, I would argue in an Alpha release it just isnt sensible to be doing work arounds as the problem will never get fixed. That would be a great pity.


Kate

I included a simple method to "revert" in my instructions just for that reason ............. I guess actually two reasons:

#1: It didn't work.

#2: You want to be able to revert quickly (and it's always easier if you have a cut-n-paste guide).

If I'm curious about the progress instead of "rm"ing the altered files I just "mv" them with a different name. Like if I've already used "_backup" I'll use "_old", or in this particular case I'd use "_altered".

In this case it requires a couple more commands due to the executable thing but it's still easy to do :)

---

### Post by sgosnell on 2010-03-07
I had to do a workaround.  The installer refused to put GRUB on my SDHC.  It crashed every time I tried, and would only put it on the internal SSD.  I let it, knowing I couldn't boot without having the card installed, then I reinstalled GRUB to the SSD.  It wasn't pretty, and it was a workaround, but it was the only way I could install it.  The previous install worked OK, and I don't know what changed, but something was wrong.

---

### Post by katie-xx on 2010-03-07
I understand exactly what you are saying but I think you are wrong. :) 
No offence meant ..I mean in the context of an Alpha release you are not right. 
Hope that reads polite because its not meant to be rude.
Sometimes its difficult on a text based forum to appear polite. :)

Besides, even if I agreed with you Im afraid work arounds of this sort havent done it for me with ATI graphics. I also have to tell you there are hoards of people who could never get Plymouth working in Fedora.
 I visIted those very unfriendly forums yesterday and people who cant get Plymouth working are still getting told to clear off to another distro and occasionally being offered a ticket to Ubuntu.
If only they knew Ubuntu has gone there too!!

No one should have to come up with a work around for a splash screen for God's sake. This is the first thing people see and if it doesnt work ... for everyone ... its a major problem for the whole release. 

Lets face it .... who in their right mind is going to change to an operating system which cant even get a splash up and running ... this is serious stuff folks.

So no work arounds ..please ... but plenty of reports :)

Kate

---

### Post by kansasnoob on 2010-03-07
I don't really disagree with you, and just noticed this from Steve Langasek in my email:

> From what I've seen, modifying the grub config as you describe causes
the kernel to use the EFI driver as the default framebuffer instead of
VGA16.  This will work for some, may fail entirely for others (i.e.,
those on non-EFI systems), and could result in regressions down the line
due to use of this non-default framebuffer module.

So it was nice seeing what the new splash looks like, but it's a bad idea all around.

---

### Post by ranch hand on 2010-03-07
> **katie-xx said:**
> Im afraid this doesnt do the trick on my ATI kit.
My Sony running on Intel chip has been ok from day 1 but ATI ...no go sorry.

Is it important? Some people have asked does a splash screen matter. IMHO its very important for the obvious reason its the first thing anyone sees. I would also imagine not many people will be pleased at having to log in twice each time.

On that basis, I would argue in an Alpha release it just isnt sensible to be doing work arounds as the problem will never get fixed. That would be a great pity.


Kate
I do use workarounds on my main install that I use all the time as my production OS.

I also use them on one other, my primary back up OS.  The second backup and the other 4 installs do not get workarounds.

This is one of the reasons that I have so many installs of Lounge Lizard (10.04).  I have plenty of room so it works for me.  If I had no room for at least 2 installs I do not think I would do testing at all.

You really do need to leave one as it is shipped to really test what the devs are doing in relation to your hardware.

---

### Post by travisat on 2010-03-08
To all those saying to not do a workaround in an alpha that is correct, and since it is an alpha you probably should not be doing anything that you don't understand.  In all likelihood 10.04 will break once or even multiple times before its release.

As to those that are worried about updates breaking things, if you have an edited file the update-script is supposed to check for changes and prompt you on what to do.  This is why I always update my system using aptitude or apt-get and not the update-manager.  Lastly if you see a grub update, cancel the update, revert the files you changed to the original, and recommence the update.  

On using the workaround, its nice to know its possible to make it work, even if its not the correct method to do so.

---

### Post by uBeer on 2010-03-08
> **travisat said:**
> As to those that are worried about updates breaking things, if you have an edited file the update-script is supposed to check for changes and prompt you on what to do.  This is why I always update my system using aptitude or apt-get and not the update-manager.

The update-manager presents a screen whether you want to see the changes, merge them or replace with the maintainers file and all the options that are there on the command line, so there is no need to use aptitude or apt-get just for that.

---

### Post by katie-xx on 2010-03-08
Wow! Big change tonight.
I get the usual blinking cursor for about 20 seconds then I get a whole screen full of "Could not write Bytes .. Broken Pipe"  Obviously gone through a loop to fill the screen.
However,  if I then press enter Im taken to the log in and only have to log in once

Kate

---

### Post by tad1073 on 2010-03-08
I am still not seeing the new plymouth theme, all I get is the blue and white fedora bars at the bottom of the screen.

---

### Post by amano on 2010-03-08
@katie-xx:
Well it's getting next to a functional state then. If Plymouth doesn't show up for every configuration around, we will be able to deal with that. But just if the boot is fast and otherwise fine...

@tad:
At least it works. I don't know if everybody will be able to see the theme in Lucid. Let's wait and hope. At least the boot is much faster now...

---

### Post by kansasnoob on 2010-03-08
I noticed something ending in "broken pipe" after the kernel update but my old eyes couldn't catch anymore than that :) I do think the boot was just a bit slower but I didn't actually time it.

I feel fairly confident that they will get this LTS just right. Of course there may be "corner issues" effecting certain hardware but, to me, it seems like they're really going for superb stability on this one.

---

### Post by katie-xx on 2010-03-08
No its not getting near to a functional state ..not on my machine anyhow and the boot time has increased not decreased.

Kate

---

### Post by Owen.C93 on 2010-03-08
> **katie-xx said:**
> No its not getting near to a functional state ..not on my machine anyhow and the boot time has increased not decreased.

Kate
Same, it was fine at first but it's gone downhill for me. I think a clean install is in order. With the new .16 kernel xorg isn't even included or needed. And thus I think alot of my drivers are messed up.

My plan is to wait for nvidia to fix overheating problems and then burn a new disk and re-install.

---

### Post by katie-xx on 2010-03-08
> **Owen.C93 said:**
> 
My plan is to wait for nvidia to fix overheating problems and then burn a new disk and re-install.

Sounds like a plan to me. Fresh install.

Kate

---

### Post by sgage on 2010-03-08
That's my plan - fresh install. But I'm going to wait until the beta drops, so I can download a (hopefully) coherent set of bits.

---

### Post by VMC on 2010-03-08
> **tad1073 said:**
> I am still not seeing the new plymouth theme, all I get is the blue and white fedora bars at the bottom of the screen.

I read in another post, that the blue & white bars is a fall-back when plymouth splash doesn't work correctly.

---

### Post by ranch hand on 2010-03-08
It is in the "text" theme in your /lib/plymouth/themes directory.  I am not suggesting deleting the bugger if it bothers you.  You would have to run;
```

sudo update-initramfs -u

```
after you deleted the directory.

---

### Post by ratcheer on 2010-03-08
GUI Plymouth splash worked for me for the first time ever, today. It was a fresh install of the 3/8/10 alternate CD with no changes applied.

Tim

---

### Post by RJARRRPCGP on 2010-03-08
> **katie-xx said:**
> No its not getting near to a functional state ..not on my machine anyhow and the boot time has increased not decreased.

Kate

Nvidia=That's probably your problem. The Nvidia binary blob init routine hangs the boot! At least with my GeForce 9500 GT. :(

---

### Post by ronacc on 2010-03-08
> **RJARRRPCGP said:**
> Nvidia=That's probably your problem. The Nvidia binary blob init routine hangs the boot! At least with my GeForce 9500 GT. :(

It may be nvidia that is the problem but since a significant % of ubuntu users have nvidia cards , if plymouth is not working for them , thats a problem .I have a 7600gs in my test box and plymouth as yet has done nothing but put a couple of blue squares bottom left on my monitor during boot . It dosen't mater what driver or how it is installed same result , Nvidia propriatary whether installed via term  straight from nvidia , by hardware drivers  , nouveau , nv foobar all .

---

### Post by katie-xx on 2010-03-09
> **RJARRRPCGP said:**
> Nvidia=That's probably your problem. The Nvidia binary blob init routine hangs the boot! At least with my GeForce 9500 GT. :(
 
Nope ..... as mentioned several times in this thread ...ATI :)

---

### Post by kansasnoob on 2010-03-09
> **katie-xx said:**
> Nope ..... as mentioned several times in this thread ...ATI :)

And mine is VIA P4/M800, so this effects a lot of hardware. We can only hope that they make the milestone of Beta 1.

---

### Post by phenest on 2010-03-09
> **ronacc said:**
> It may be nvidia that is the problem but since a significant % of ubuntu users have nvidia cards

Can you back that up? Seriously, if you can, we should present something to Canocical to express how widespread the problem is, and whether usplash should be re-instated until Plymouth can be proved usable.

---

### Post by philinux on 2010-03-09
Plymouth works here with the nouveau driver, however.

Removing plymouth, on my rig, results in an almost instant shutdown instead of >12 seconds with it.

Boot up remained the same.

---

### Post by phenest on 2010-03-09
I haven't tried lately, but although it worked here with nouveau, I had a blank screen. Besides, nouveau is no good for playing games. Plymouth needs to work with the binary too (or vice versa).

---

### Post by Stason on 2010-03-09
Need some advice here please. Having no knowledge of what plymouth is and given the symptoms like flickering lines at boot I may conclude I shall never learn it - should I just remove it? is it best done via synaptic?

---

### Post by tad1073 on 2010-03-09
@Stason: open a terminal and put in:

```
sudo aptitude remove --purge plymouth
```

---

### Post by mc4man on 2010-03-09
> .I have a 7600gs in my test box....
One of my testers  has a 7600gs dual booting lucid - one on nouveau, the other nvidia-current (195.36.08 

Both work well and as expected - plymouth works with nouveau, doesn't with nvidia-current

Overall nouveau works well, a huge improvement from nv though still not as good as nvidia ( and no issues here with the nvidia driver, generally in the 42 - 52 C range.

So if it's a hardware issue it lies elsewhere

---

### Post by sgage on 2010-03-09
So when is plymouth expected to work with nvidia?

---

### Post by teh603 on 2010-03-09
> **phenest said:**
> Can you back that up? Seriously, if you can, we should present something to Canocical to express how widespread the problem is, and whether usplash should be re-instated until Plymouth can be proved usable.

Honestly, look at the number of threads which have people complaining about Plymouth. Now look at the number of bugs people have actually filed about it. There's maybe five, and only one of them is even high priority. My guess is that the people who have the issue (like me) don't know how to file a bug report about a specific process, or can't describe the symptoms properly enough to get it to be accepted.

It doesn't seem to work with the i3 chipsets, either.

Maybe one of us oughtta file a bug demanding that Plymouth get removed, link it to the forum for everyone to see, and see how many votes it gets?

---

### Post by NightwishFan on 2010-03-09
You could always remove it and install usplash. I believe the best bet is to mark a bug as affecting you or post one if your issue is new.

---

### Post by teh603 on 2010-03-09
> **NightwishFan said:**
> You could always remove it and install usplash. I believe the best bet is to mark a bug as affecting you or post one if your issue is new.Can you post a howto on that? The best I can do is fire up Synaptic, flag Plymouth for removal, and then click Apply. Which doesn't stop the system from generating a ton of errors because it can't find Plymouth, and I can't uninstall libPlymouth because its aparrently required by everything including the kernel...

---

### Post by NightwishFan on 2010-03-09
I doubt that will be the case come release time.

---

### Post by tad1073 on 2010-03-09
> **mc4man said:**
> and no issues here with the nvidia driver, generally in the 42 - 52 C range.

So if it's a hardware issue it lies elsewhere

I have an after market fan on my gpu that has a 3pin to molex connector so I am able to bypass the fan controller that is on the card.

---

### Post by Uncle Spellbinder on 2010-03-10
> **sgage said:**
> So when is plymouth expected to work with nvidia?
Hopefully before final release, or there will be lots of unhappy LTS users.

---

### Post by yoasif on 2010-03-10
I wasn't able to find a page that showed what "should work" for plymouth, so I will just ask here.

After grub loads, we should see plymouth and no other text messages until gdm loads, kinda like usplash, right? because right now, I am seeing other messages -- not the prettiest boot experience at all.

---

### Post by ndefontenay on 2010-03-10
> **katie-xx said:**
> [SIZE=2][COLOR=Blue]
Thanks for that. That seems to stack up with my own observations. My Sony Laptop has a Intel chipset and seems ok. However, this laptop, a Dell Studio, has the ATI Mobility Radeon HD 3400 and seems to be having intermittant problems. Sometimes it will sometimes it wont.
I guess we shall have to wait and see what happens by the time the first beta appears :)
At least no one seems to be getting those horrible "progress bars" which blighted Fedora.

Kate
[/COLOR][/SIZE]

Dell Studio as well. Same problem. I have to press enter in order to log in.

---

### Post by ranch hand on 2010-03-10
For the last few days plymouth has worked about 90% of the time on all 7 variations of 10.04 that I am running on this box.

Beats me.

Card in sig.

---

### Post by VMC on 2010-03-10
> **yoasif said:**
> I wasn't able to find a page that showed what "should work" for plymouth, so I will just ask here.

After grub loads, we should see plymouth and no other text messages until gdm loads, kinda like usplash, right? because right now, I am seeing other messages -- not the prettiest boot experience at all.

Is the "quiet" command line parameter on?
From a terminal run this 'grep linux /boot/grub/grub.cfg/'

Look for the *linux* line of the UUID you want to boot.
 Make sure it has "quiet" near the end. If not that's why your getting more text messages than you want.

---

### Post by kansasnoob on 2010-03-10
> **NightwishFan said:**
> You could always remove it and install usplash. I believe the best bet is to mark a bug as affecting you or post one if your issue is new.

As far as, "install usplash": just how would you do that without removing gdm?????????????

How about we be patient just a bit ;) If you look at reply #1 here:

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

> milestone:  	 none &#8594; ubuntu-10.04-beta-1 

Actually that would be a good place to add any actual knowledge anyone has regarding this. It's not just a Nvidia thing - the OP, Kate, has ATI - I have VIA, and even Steve Langasek says, "because plymouth doesn't support graphical output to a 4-bit framebuffer".

I trust him!!!!!!!!!!!!

---

### Post by NightwishFan on 2010-03-10
I advise patience as well, since the release is probably set up to be developer friendly and not for user stability right now.

Please note I do not track Lucid, I run Debian Unstable now, so I have no idea how everything is going. I might install in virtual machine to help out though.

---

### Post by teh603 on 2010-03-10
For those of us who are still having problems with Plymouth, here's a bug to look at.

[https://bugs.launchpad.net/ubuntu/+bug/535671](https://bugs.launchpad.net/ubuntu/+bug/535671)

Not sure if this is what they're looking for, but it will hopefully get something better than "low" priority if enough people vote for it.

---

### Post by ronacc on 2010-03-10
added my me too to your bug

---

### Post by cyberkilla on 2010-03-10
I don't know if this has been pointed out again recently, but I still see a handful of console messages between Plymouth transitions.

For instance, on boot I see a few fsck messages, plus a warning about a usb webcam driver that doesn't work properly.

On shutdown, I see Plymouth, then for a couple of seconds, I see messages about TERM signals and being "disconnected from system bus". Not sure what the cause of this is, but I'd imagine that Plymouth is supposed to be the last thing a user sees before the screen switches off.

If the boot is to be graphical, I'm all for hiding console messages. In particular, any messages which don't culminate in my computer failing to boot.:D

PS. The problem is still flicker-free (Nouveau)

---

### Post by kansasnoob on 2010-03-10
> **teh603 said:**
> For those of us who are still having problems with Plymouth, here's a bug to look at.

[https://bugs.launchpad.net/ubuntu/+bug/535671](https://bugs.launchpad.net/ubuntu/+bug/535671)

Not sure if this is what they're looking for, but it will hopefully get something better than "low" priority if enough people vote for it.

As it says in reply to your "bug" report, that's a suggestion for Brainstorm, but the milestone for fixing this is Beta 1. I take that to mean it will be assigned and hopefully fixed during the Beta 1 cycle.

OTOH if you'd like to work on a way to replace Plymouth with Usplash and still have GDM I'm sure some might like that.

---

### Post by teh603 on 2010-03-10
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/519641](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/519641)

Filed it on Brainstorm, then I tried booting from the current LiveCD snapshot. Which failed miserably thanks to the "broken pipe" mentioned in the above bug.

---

### Post by katie-xx on 2010-03-10
Now we seem to be cooking on gas. Its a big improvement tonight.
Still not perfect: There is a significant delay between 2 different blinking cursors and the appearance of the splash screen but its there at last with ATI kit.

Plymouth first came to my attention with Fedora10. It never worked properly and didnt get any better through Fedora 11 and 12. Not for me anyhow. Anyone asking questions risked being told to sling their hook and, on one occasion, I was asked if I wanted a ticket to Ubuntu.

Now its still not perfect but is working better than I have seen before. 
Nice one :)

Edit: ....... Damn it. I spoke too soon. After 4 restarts when Plymouth ran as above ,,it is now back to square 1 .... no splash screen, two log ins required and in addition ..I have to press enter to get away from blank screen.
Worst of all I havent done anything by way of downloads or configuration between successful and unsuccessful boot.
Anyone else ?

Kate

---

### Post by NightwishFan on 2010-03-10
Fedora 10 splash is fantastic. I might try to get plymouth and that splash on Debian somehow.

---

### Post by katie-xx on 2010-03-10
> **NightwishFan said:**
> Fedora 10 splash is fantastic. I might try to get plymouth and that splash on Debian somehow.
Fedora 10 splash is fantastic for a very small subset of the hardware out there.

---

### Post by teh603 on 2010-03-10
> **katie-xx said:**
> Now we seem to be cooking on gas. Its a big improvement tonight.
Still not perfect: There is a significant delay between 2 different blinking cursors and the appearance of the splash screen but its there at last with ATI kit.

Plymouth first came to my attention with Fedora10. It never worked properly and didnt get any better through Fedora 11 and 12. Not for me anyhow. Anyone asking questions risked being told to sling their hook and, on one occasion, I was asked if I wanted a ticket to Ubuntu.

Now its still not perfect but is working better than I have seen before. 
Nice one :)

Edit: ....... Damn it. I spoke too soon. After 4 restarts when Plymouth ran as above ,,it is now back to square 1 .... no splash screen, two log ins required and in addition ..I have to press enter to get away from blank screen.
Worst of all I havent done anything by way of downloads or configuration between successful and unsuccessful boot.
Anyone else ?

Kate
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/519641](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/519641)

Take a look at the last comment here.

Now, hopefully the developers will deal with the fact that the bootsplash for the LiveCD image is hopelessly borked when they do these changes...

---

### Post by NightwishFan on 2010-03-10
I agree. Though for my Nvidia card. (Proprietary Driver) I just had to add a parameter to grub like vga=0x31a or something.

---

### Post by katie-xx on 2010-03-10
> **NightwishFan said:**
> I agree. Though for my Nvidia card. (Proprietary Driver) I just had to add a parameter to grub like vga=0x31a or something.

I think I posted a link to that earlier in the thread. Generally it required result of vbetest.
Wasnt successful for everyone though even across identical hardware.

---

### Post by katie-xx on 2010-03-11
Two crash reports tonight. 

*"PlymouthD has closed unexpectedly."*

I have a little difficulty understanding why such a well known buggy component has been sucked into Ubuntu. However, its probably too late now and I guess we are going to end up with a distro that cant put up a splash for the majority of the common hardware out there. (Think Pads are us :))

Kate

Edit: Kernel freeze is today yes?

---

### Post by kansasnoob on 2010-03-11
> **NightwishFan said:**
> Fedora 10 splash is fantastic. I might try to get plymouth and that splash on Debian somehow.

I'm still using usplash on Squeeze.

I haven't tried Sid in quite a while.

---

### Post by NightwishFan on 2010-03-11
Plymouth packages are in experimental, but I decided to wait until they hit Sid.

---

### Post by Owen.C93 on 2010-03-11
I was under the impression that alot of the issues are with graphics card drivers. Not really plymouth.

---

### Post by ronacc on 2010-03-11
if  plymouth does not work with common graphics cards from major manufacture's they are not the problem , plymouth is .

---

### Post by VMC on 2010-03-11
> **katie-xx said:**
> Two crash reports tonight. 

*"PlymouthD has closed unexpectedly."*



I'm experiencing this also. There's a [**_bug#537262 report_**]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/537262") on it. Go there and join the fun. 

I get that Plymouth crash on almost every boot. the weird thing is the bug is for Plymouth not closing. Apparently you don't get the crash report until next re-boot.

Edit:Actually from the bug report, they think .. this isn't a bug in Plymouth - it's a bug in the script that's telling you it's a bug. ..

Something to do with "/etc/init.d/sendsigs" script.

---

### Post by Muflon on 2010-03-12
> **VMC said:**
> I'm experiencing this also. There's a [**_bug#537262 report_**]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/537262") on it. Go there and join the fun. 

I get that Plymouth crash on almost every boot. the weird thing is the bug is for Plymouth not closing. Apparently you don't get the crash report until next re-boot.

Edit:Actually from the bug report, they think .. this isn't a bug in Plymouth - it's a bug in the script that's telling you it's a bug. ..

Something to do with "/etc/init.d/sendsigs" script.

You have to smile :)

Muflon

---

### Post by tekstr1der on 2010-03-12
Major plymouth update landed. Should be in repos soon...

```
plymouth (0.8.0~-13) lucid; urgency=low

  [ Steve Langasek ]
  * Don't attach /proc/cmdline to apport reports, this is already in the
    standard info that gets collected...

  [ Alberto Milone ]
  * ubuntu_logo theme:
    - New logo from Otto Greenslade.
    - Switch off dots starting from the ones on the left instead of
      switching them off all at once.

  [ Scott James Remnant ]
  * Move the Ubuntu logo up as discussed with Otto, this makes the mouse
    cursor appear between the logo and dots and solves the optical illusion
    of the logo being too low.  LP: #535014.
  * Don't include message about disk checks, which can come from mountall.
  * Drop the rc script splash functions, we don't want the SysV-rc compat
    stuff messing around with the splash screen - this can be entirely
    managed by Upstart now.  LP: #528787, #537262.

  * Plymouth Fix Mega Patch:
    - This hasn't yet been broken up into enough bits to send upstream, and
      doesn't *quite* address all the issues yet, but it's a major step.

    - Rewrite the VT handling, rather than abusing /dev/tty0 keep all VT
      operations on the actual VT (tty7), this avoids issues where we set
      the graphics mode of the wrong VT or put the wrong VT into VT_PROCESS
      mode.  LP: #520460, #522598, #526321, #533135
    - Don't attempt VT switch when using non-VT consoles.
    - Make VT mandatory for renderer plugins, so we fallback gracefully to
      text when the console is not a VT.  LP: #516825, #527083.
    - Restore VT when finished displaying the splash unless plymouth quit
      is called with --retain-splash.  LP: #506297.
    - Activate VT from text and details plugins, rather than haphardly in
      the main code, this means the textual boot is also on VT7.
      LP: #518352, #520122.
    - Add a --has-active-vt command that can let gdm inquire whether it
      should reuse Plymouth's VT; fixes the issue where Plymouth has no
      visible splash screen and X ends up on VT1.  LP: #519641, #533572.

    - Don't open terminal device in X11, fixes the issue where X will crash
      when debugging plugins using the X11 renderer.
    - Add --tty option to plymouthd for debugging when X is running and
      thus using an alternate VT.

    - Improve deactivate command so that the terminal is no longer watched
      for keyboard input, session is closed, etc.  LP: #528787, #531650.
    - Ignore mode changes while deactivated, otherwise we can end up
      resetting the VT back into text mode while X is starting up.
      LP: #523788, #502509.

    - Fix races with simultaneous quit and deactivate commands, or multiples
      of those commands.
    - Ignore --show-splash, --hide-splash, etc. commands while deactivated.
    - Add reactivate command for testing purposes.

    - Don't scan out drm buffer contents to fbcon when not called with
      quit --retain-splash.  LP: #527180.

    - Avoid resetting the terminal to unbuffered mode on every write, this
      results in setting X's VT into raw mode and results in the X server
      crashing on key presses.  LP: #532047, #534861, #519460, #520593,
      #522974, #525393

  * I'm aware that if you see the TEXT plugin, it's possible for Enter to
    still crash the X server for some people.  I will be opening a new bug
    for this, and would appreciate details from people affected.

  * If you have issues with Enter crashing the X server, and you see a
    GRAPHICAL plugin, check that gdm is up to date - if it is, please
    file new bugs.

  * I'm also aware of an issue where after boot, rather than seeing an X
    server, you see the ordinary "login:" getty screen.  Pressing Alt+F7
    should take you to X.  I will be opening a new bug for this, and would
    appreciate details from people affected.

  * Don't send fsck progress updates to the boot-duration file.
  * Make all the dots orange just before starting the X server.

  * Cute text-version of the splash screen.
    - Added basic support for fsck notification.
    - Added support for showing keys information on separate lines.


```

---

### Post by DoeRayMe on 2010-03-12
> **tekstr1der said:**
> Major plymouth update landed. Should be in repos soon...

```
plymouth (0.8.0~-13) lucid; urgency=low

  [ Steve Langasek ]
  * Don't attach /proc/cmdline to apport reports, this is already in the
    standard info that gets collected...

  [ Alberto Milone ]
  * ubuntu_logo theme:
    - New logo from Otto Greenslade.
    - Switch off dots starting from the ones on the left instead of
      switching them off all at once.

  [ Scott James Remnant ]
  * Move the Ubuntu logo up as discussed with Otto, this makes the mouse
    cursor appear between the logo and dots and solves the optical illusion
    of the logo being too low.  LP: #535014.
  * Don't include message about disk checks, which can come from mountall.
  * Drop the rc script splash functions, we don't want the SysV-rc compat
    stuff messing around with the splash screen - this can be entirely
    managed by Upstart now.  LP: #528787, #537262.

  * Plymouth Fix Mega Patch:
    - This hasn't yet been broken up into enough bits to send upstream, and
      doesn't *quite* address all the issues yet, but it's a major step.

    - Rewrite the VT handling, rather than abusing /dev/tty0 keep all VT
      operations on the actual VT (tty7), this avoids issues where we set
      the graphics mode of the wrong VT or put the wrong VT into VT_PROCESS
      mode.  LP: #520460, #522598, #526321, #533135
    - Don't attempt VT switch when using non-VT consoles.
    - Make VT mandatory for renderer plugins, so we fallback gracefully to
      text when the console is not a VT.  LP: #516825, #527083.
    - Restore VT when finished displaying the splash unless plymouth quit
      is called with --retain-splash.  LP: #506297.
    - Activate VT from text and details plugins, rather than haphardly in
      the main code, this means the textual boot is also on VT7.
      LP: #518352, #520122.
    - Add a --has-active-vt command that can let gdm inquire whether it
      should reuse Plymouth's VT; fixes the issue where Plymouth has no
      visible splash screen and X ends up on VT1.  LP: #519641, #533572.

    - Don't open terminal device in X11, fixes the issue where X will crash
      when debugging plugins using the X11 renderer.
    - Add --tty option to plymouthd for debugging when X is running and
      thus using an alternate VT.

    - Improve deactivate command so that the terminal is no longer watched
      for keyboard input, session is closed, etc.  LP: #528787, #531650.
    - Ignore mode changes while deactivated, otherwise we can end up
      resetting the VT back into text mode while X is starting up.
      LP: #523788, #502509.

    - Fix races with simultaneous quit and deactivate commands, or multiples
      of those commands.
    - Ignore --show-splash, --hide-splash, etc. commands while deactivated.
    - Add reactivate command for testing purposes.

    - Don't scan out drm buffer contents to fbcon when not called with
      quit --retain-splash.  LP: #527180.

    - Avoid resetting the terminal to unbuffered mode on every write, this
      results in setting X's VT into raw mode and results in the X server
      crashing on key presses.  LP: #532047, #534861, #519460, #520593,
      #522974, #525393

  * I'm aware that if you see the TEXT plugin, it's possible for Enter to
    still crash the X server for some people.  I will be opening a new bug
    for this, and would appreciate details from people affected.

  * If you have issues with Enter crashing the X server, and you see a
    GRAPHICAL plugin, check that gdm is up to date - if it is, please
    file new bugs.

  * I'm also aware of an issue where after boot, rather than seeing an X
    server, you see the ordinary "login:" getty screen.  Pressing Alt+F7
    should take you to X.  I will be opening a new bug for this, and would
    appreciate details from people affected.

  * Don't send fsck progress updates to the boot-duration file.
  * Make all the dots orange just before starting the X server.

  * Cute text-version of the splash screen.
    - Added basic support for fsck notification.
    - Added support for showing keys information on separate lines.


```

tbh i'm quite excited by these changes, looking forward to testing them :)

---

### Post by sgage on 2010-03-12
I was pretty excited, too, when I saw plymouth updates in Synaptic. Applied them and... system won't boot at all. Oh well.

---

### Post by koso on 2010-03-12
Same problem here, even without enabled plymouth => its probably problem with mountall :((

---

### Post by sgage on 2010-03-12
I'm thinking about taking a break from Lucid until the beta bits are released next week. I don't mind testing through a bit of roughness, but a fella has got to be able to boot to do any testing!  ;-)

---

### Post by katie-xx on 2010-03-12
Yipee! Isnt Alpha fun :)
I cant boot at all after updating Plymouth so its gotta be a fresh install after a decent period of time.
Maybe some kind person will be able to give the heads up once its safe to install :)


Kate

---

### Post by k3lt01 on 2010-03-12
My system is working perfectly, I like the new look at boot and its seems to be slightly faster on my little laptop.

---

### Post by seeker5528 on 2010-03-12
> **ronacc said:**
> if  plymouth does not work with common graphics cards from major manufacture's they are not the problem , plymouth is .

If plymouth doesn't work with a card, that is not a problem. 

If failure to work with a card results in failure to boot, that's a problem. 

Later, Seeker

---

### Post by katie-xx on 2010-03-12
Restored for now :)
I was going to wait for Beta and then do a clean install but couldnt be patient enough so booted from Crunchbang  disc.

Fingers crossed but Ive had Plymouth screen up three times now without any problems ..so its time for me to eat my hat maybe???

Kate

Edit:  Spoke too soon again it seems. :)
          Thrown into tty and had to do a Ctrl + Alt + F7 to get to GUI login.
Guess what ....I can now replicate this problem every time ...... ah well ..Alpha is fun :)
Anyone else??

---

### Post by ranch hand on 2010-03-12
If you can chroot in and do another update/upgrade it should clear the failure to boot problem.  Needed an update of ureadahead to work.

---

### Post by VMC on 2010-03-12
> **katie-xx said:**
> Restored for now :)
I was going to wait for Beta and then do a clean install but couldnt be patient enough so booted from Crunchbang  disc.

Fingers crossed but Ive had Plymouth screen up three times now without any problems ..so its time for me to eat my hat maybe???

Kate

Edit:  Spoke too soon again it seems. :)
          Thrown into tty and had to do a Ctrl + Alt + F7 to get to GUI login.
Guess what ....I can now replicate this problem every time ...... ah well ..Alpha is fun :)
Anyone else??

I think you have the same bug I have. Here's the [**_bug report_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214").

---

### Post by tekstr1der on 2010-03-12
Good find. Thanks.

---

### Post by ElSlunko on 2010-03-12
> **ranch hand said:**
> If you can chroot in and do another update/upgrade it should clear the failure to boot problem.  Needed an update of ureadahead to work.

I did this from the live cd instead of the symbolic link. Worked fine.

---

### Post by morryis on 2010-03-13
The new text based boot splash with nvidia driver looks ugly and primitive

---

### Post by MacUntu on 2010-03-13
Not primitive - oldskool! :>

---

### Post by plun on 2010-03-13
> **MacUntu said:**
> Not primitive - oldskool! :>

Yeeah... "the new school" is to introduce crappy software within an LTS...:D

Magic....;)

---

### Post by teh603 on 2010-03-13
> **VMC said:**
> I think you have the same bug I have. Here's the [**_bug report_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214").

Yaaaaay someone was able to report it. I tried installing the -14  build of Plymouth, and had to completely reinstall everything because of this. Good to see its already confirmed and assigned.

---

### Post by tad1073 on 2010-03-13
Plymouth is finally working for me but it looks horrid and I also get the ureadahead proccess terminated error.

---

### Post by plun on 2010-03-13
> **tad1073 said:**
> Plymouth is finally working for me but it looks horrid and I also get the ureadahead proccess terminated error.

Well, my desktop is broken and forced to use low resolution mode....

If the bug is Jockey, Plymouth, or other package is unknown ????
(I am not going to file a bug against this mess)

If I was Mr Langasek i directly order a "cleanup" and a Nouveu removal.
(also Plymouth seems to be totally crap)

---

### Post by tad1073 on 2010-03-13
I myself kind of like the verbose output during the boot process...

---

### Post by plun on 2010-03-13
> **tad1073 said:**
> I myself kind of like the verbose output during the boot process...

No.....  I like eye-candy....

And it looks like **** with no Plymouth !

So Mr Langasek must do something !!!! It soon beta -time !

---

### Post by personman_ on 2010-03-13
Plymouth is working fine for my stock kernels now, but my custom compile 2.6.33 just hangs at the boot splash screen.

Wasn't doing this before this recent batch of updates.

Tried rebuilding the initramfs, removing and reinstalling the kernel package, etc.

Only way I can boot my custom kernel now is to remove "splash" from the kernel options. :/

-Andy

---

### Post by ratcheer on 2010-03-13
> **ranch hand said:**
> If you can chroot in and do another update/upgrade it should clear the failure to boot problem.  Needed an update of ureadahead to work.

I had been saying that I thought ureadahead was the problem (or, at least, it was involved in the problem), but everyone else said, "Nooooo, there are no bugs in ureadahead."

Tim

---

### Post by Half-Left on 2010-03-13
What's the real problem here?. Fedora had it working fine ages ago, apart from having to enter vga= to get the nice animating image, so I don't understand why Canonical are having so many issues with it.

If it's still not showing properly by the RC and then fine, start moaning, don't delete it now just because the alpha has issues. I hope it turns out to be a smooth process, without the cursor flashing after grub.

---

### Post by ratcheer on 2010-03-13
I just applied all updates to Lucid and it still will not boot, normally. I noticed that many of the updates were for plymouth and X11. It gives the purple plymouth screen for a few seconds, then my disk starts the repeated clicking/grinding sound, then the screen goes black. Hitting or holding the Enter key has no effect.

Rebooting to grub recovery mode, root prompt, start gdm still works fine.

Tim

---

### Post by jppr on 2010-03-13
i did fresh install, boot and plymouth works well

---

### Post by meborc on 2010-03-13
Re-installed today using daily-live

Boot works, I see Ubuntu logo and the "dots", very beautiful. After rebooting I still see the nice logo, but instead of GDM, I see command line. I have to do a manual ALT+F7 to get to GDM. Bug report here - [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214)

After Gnome has loaded, I get an error message that plymouthd has stopper unexpectedly. 

To me as a user, the only nuisance is to remember switching to tty7 to log in :)

Next I'll try to install the proprietary nvidia drivers and see what happens then.

---

### Post by k3lt01 on 2010-03-13
> **ratcheer said:**
> I had been saying that I thought ureadahead was the problem (or, at least, it was involved in the problem), but everyone else said, "Nooooo, there are no bugs in ureadahead."

TimDo a search on the forums, you will see a few threads where ureadahead has been identified as a problem. Both Ranch Hand and myself have mentioned it in this thread a few times.

---

### Post by ElSlunko on 2010-03-13
I've been doing the updates & I don't see a logo. I see the purple background & the dots but the words "Ubuntu 10.04" isn't a logo to me, just some Monospace text.

---

### Post by meborc on 2010-03-13
> **ElSlunko said:**
> I've been doing the updates & I don't see a logo. I see the purple background & the dots but the words "Ubuntu 10.04" isn't a logo to me, just some Monospace text.

that's what i get also with the **nvidia proprietary** drivers...

---

### Post by katie-xx on 2010-03-14
> **Half-Left said:**
> What's the real problem here?. Fedora had it working fine ages ago, apart from having to enter vga= to get the nice animating image, so I don't understand why Canonical are having so many issues with it.
If it's still not showing properly by the RC and then fine, start moaning, don't delete it now just because the alpha has issues. I hope it turns out to be a smooth process, without the cursor flashing after grub.

To be absolutely accurate about this: Fedora had it working fine ages ago for a minority of its user base. Most people were left with one or more problems. with Plymouth.
Canonical are having exactly the same issues as Fedora. A significant proportion of the user base do not have hardware which Plymouth expects to find.
It seems to me that Canonical are trying a little harder to improve matters as there have been a significant number of changes made. Unfortunately these havent done the trick as yet but we are still on an Alpha release.
I will still eat my woolly ski hat if Ubuntu get this working properly tho :)

Kate

---

### Post by teh603 on 2010-03-14
Be glad you get anything at all. I get dumped to a text login if I install it.

By the way, my idea on Brainstorm to remove Plymouth got flagged as "this isn't an idea." Which is bull, because it clearly IS an idea. Same as my filing it on Launchpad resulted in "this is an idea, not a bug." I'm starting to think someone high enough up to make executive decisions is forcing Plymouth down our throats whether we like it or know how to fully remove it or not.

Which sucks, because I really don't want to go back to Win7.

---

### Post by Madspyman on 2010-03-14
> **teh603 said:**
> Be glad you get anything at all. I get dumped to a text login if I install it.

By the way, my idea on Brainstorm to remove Plymouth got flagged as "this isn't an idea." Which is bull, because it clearly IS an idea. Same as my filing it on Launchpad resulted in "this is an idea, not a bug." I'm starting to think someone high enough up to make executive decisions is forcing Plymouth down our throats whether we like it or know how to fully remove it or not.

Which sucks, because I really don't want to go back to Win7.

I removed Plymouth and haven't had a boot problem in Lucid since, I'm not a fan of the purple splash screen anyway.

---

### Post by teh603 on 2010-03-14
> **Madspyman said:**
> I removed Plymouth and haven't had a boot problem in Lucid since, I'm not a fan of the purple splash screen anyway.How did you get rid of the "Plymouth main process (number) ended with status 2" error messages?

---

### Post by Matticus on 2010-03-14
I was just posting to say I kept getting kicked to a text base login after updating. But now it works after a few boots.

At first I liked the white logo on black background (was very glad to see the back of brown), then when I reboot after update I loved the black background (guess it wasn't supposed to be there) with the new font and dots. Then I got text based a bunch of times. Then finally I was presented with a purple background and dots my initial thought was cool until all these crazy light flares etc. To me it seems a little bit too OS X inspired.

Edit: tty again. Alpha's are fun, now if I can get my wireless to connect again, change the order of the buttons and make my battery icon appear again, then I can start getting some serious tinkering done.

---

### Post by ranch hand on 2010-03-14
> **teh603 said:**
> How did you get rid of the "Plymouth main process (number) ended with status 2" error messages?
```

sudo apt-get purge

```and then
```

gksudo nautilus

```and delete the /lib/plymouth directory if it is still there.

EDIT
I have done that on one of my installs that just will not boot with plymouth at all.

I will probably reinstall ureadahead and install plymouth again when I am feeling lucky.

---

### Post by autocrosser on 2010-03-14
To get Plymouth working with the Nvidia drivers I used the info from post #92--- I found that if you just edit after line #103 in /etc/grub.d/00_header with a new line that reads: ```
set gfxpayload=keep
``` Both of my systems using nvidia cards will work "mostly" normal with Plymouth---My main system that is a Quad i7 works with it just like it should & my wife's system that is a single-core 1.8 spits 3 or 4 lines out & then Plymouth starts...So, all-in-all, I have found that this "works" at least for me......

Note: line #103 reads:```
 gfxmode=${GRUB_GFXMODE}
```

---

### Post by FrancoNero on 2010-03-14
alt and f7 actually gets you out of the text login screen to the graphical login in exactly under one second.

my plymouth starting and shutting down has no logo, but it's noticable plymouth....

what i find weird is that my nouveau is completely gone. i'd love to try nouveau to see if it works smoother

---

### Post by ndefontenay on 2010-03-14
These days I still have to press enter twice before being logged in. 

I don't have the log in screen anymore however so I guess it's a progress. I do hope we won't be left on the side when lucid hits april 29th deadline ><

---

### Post by teh603 on 2010-03-14
> **ranch hand said:**
> ```

sudo apt-get purge

```and then
```

gksudo nautilus

```and delete the /lib/plymouth directory if it is still there.

EDIT
I have done that on one of my installs that just will not boot with plymouth at all.

I will probably reinstall ureadahead and install plymouth again when I am feeling lucky.Is there a way to do the apt-get parts in Synaptic? I'm still not too comfortable using apt thru the console.

---

### Post by k3lt01 on 2010-03-14
> **teh603 said:**
> Is there a way to do the apt-get parts in Synaptic? I'm still not too comfortable using apt thru the console.Yes, mark the item you want to remove "For Complete Removal"

---

### Post by VMC on 2010-03-16
Scott James Remnant has a [PPA]("https://launchpad.net/~scott/+archive/ppa") for plymouth and wants us that have the [textual]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214") login error to try it and see if it fixes this issue. 
That bug is the error whereby your left in a VT login state, and pushing Alt+F7 brings up your desktop.

---

### Post by robert shearer on 2010-03-16
> **VMC said:**
> Scott James Remnant has a [PPA]("https://launchpad.net/~scott/+archive/ppa") for plymouth and wants us that have the [textual]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538214") login error to try it and see if it fixes this issue. 
That bug is the error whereby your left in a VT login state, and pushing Alt+F7 brings up your desktop.

Thanks for that. Fixed it for me.

---

### Post by VMC on 2010-03-16
> **robert shearer said:**
> Thanks for that. Fixed it for me.

It fix for several others. I can't get past 404's:

Inputting:
```
$ sudo add-apt-repository ppa:scott/ppa
```
that worked.

Adding to sources.list:
```
deb http://ppa.launchpad.net/scott/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/scott/ppa/ubuntu lucid main
```

then,
```
sudo aptitude -q update && sudo aptitude -q safe-upgrade

```
gave me these errors:
```
Err http://ppa.launchpad.net lucid/main Packages
  404 Not Found
Err http://ppa.launchpad.net lucid/main Packages
  404 Not Found
```

changing mirrors didn't help. Weird. 

At any rate, the new plymouth should be in repositories tomorrow.

---

### Post by robert shearer on 2010-03-16
I think the sources.list is for pre 9.10 and the 
```
 sudo add-apt-repository ppa:scott/ppa
```
works for  Lucid as you've found.

---

### Post by VMC on 2010-03-16
> **robert shearer said:**
> I think the sources.list is for pre 9.10 and the 
```
 sudo add-apt-repository ppa:scott/ppa
```
works for  Lucid as you've found.

Yea, at first I realized I installed the wrong key, but installing the correct key didn't work. I think something must of happened in between. I have a backup partition that I used the correct PPA in the beginning and it worked without PPA 404 errors.

So a politely copied that partitions "/etc/apt" folders over to the one that didn't work. That worked. But now left with what happened. A stupid mistake, thinking it wouldn't work. I should have renamed the old folders so I could compare and find the culprit.

At any rate Plymouth now works, I just don't get a booting ubuntu logo, and I do get a reboot ubuntu logo. Not sure it that even matters.

---

### Post by teh603 on 2010-03-16
I get a blank screen instead of the splash (or a flashing cursor) more often than not, but then again when it gives me a blank screen it boots really quick.

At least its not crashing, dumping me to an ugly login screen, or dropping me in odd text login screens anymore.

---

### Post by VMC on 2010-03-17
It would be nice to get that ubuntu logo on boot up. More professional, but I will settle on plymouth working - even in the dark :)

---

### Post by robert shearer on 2010-03-17
> **VMC said:**
> It would be nice to get that ubuntu logo on boot up. More professional, but I will settle on plymouth working - even in the dark :)

Like a tree falling in a forest with no one to hear it fall.....

---

### Post by katie-xx on 2010-03-17
> **VMC said:**
>  
At any rate Plymouth now works, **I just don't get a booting ubuntu logo**, and I do get a reboot ubuntu logo. Not sure it that even matters.
 
Actually, thats Plymouth not working :)

---

### Post by VMC on 2010-03-17
> **katie-xx said:**
> Actually, thats Plymouth not working :)
No, that's splash not working.

---

### Post by ratcheer on 2010-03-17
My plymouth and several related components were updated, this morning. plymouth worked better, for me, yesterday. Why do they always do this stuff?

Tim

---

### Post by MacUntu on 2010-03-17
> **ratcheer said:**
> Why do they always do this stuff?

Visual stuff obviously is less important for beta-1 than being able to boot. ;-)

---

### Post by teh603 on 2010-03-17
> **MacUntu said:**
> Visual stuff obviously is less important for beta-1 than being able to boot. ;-)Unless said visual stuff is interfering with the boot process, like plymouth has from time to time.

---

### Post by ratcheer on 2010-03-17
> **MacUntu said:**
> Visual stuff obviously is less important for beta-1 than being able to boot. ;-)

Well, exactly. My system booted better with yesterday's plymouth than today's. It is back to doing all that disk grinding crap, again. And since plymouth is what changed, I blame it on the plymouth changes. 

Tim

---

### Post by ratcheer on 2010-03-17
> **teh603 said:**
> Unless said visual stuff is interfering with the boot process, like plymouth has from time to time.

Bingo!

Tim

---

### Post by katie-xx on 2010-03-17
> **VMC said:**
> No, that's splash not working.

Its Plymouth not working. Trust me.
Plymouth consists of two binaries.
One of these is Plymouthd, and this is designed to log the session and show the splash.
The other, Plymouth, is essentially a control interface for Plymouthd.
Your problem, as I said, is Plymouth not working properly.

Google is your friend :)   [https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience](https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience)

Kate

---

### Post by ranch hand on 2010-03-17
> **katie-xx said:**
> Its Plymouth not working. Trust me.
Plymouth consists of two binaries.
One of these is Plymouthd, and this is designed to log the session and show the splash.
The other, Plymouth, is essentially a control interface for Plymouthd.
Your problem, as I said, is Plymouth not working properly.

Kate
+1

But Fedora uses it so it has to be great.

---

### Post by katie-xx on 2010-03-17
Hiya
This might be of interest:

[http://cgit.freedesktop.org/plymouth/tree/README](http://cgit.freedesktop.org/plymouth/tree/README)

Kate

---

### Post by prodigy_ on 2010-03-17
Yeah, it was an awesome idea to jump to Plymouth in an LTS release. Along with other important innovations like changing the default buttons placement. After all, we don't want to make things too easy for the newcomers, do we?
/sarcasm off

Desktop Linux distros still have serious, glaring, showstopper issues like video tearing in movie players and sound not working on every second laptop. And often there are no actual, universal solutions for these issues at all. I wonder when the Ubuntu team (and other development teams for that matter) will start paying attention to real problems instead of breaking things that have been working fine for years.

---

### Post by Digital Hick on 2010-03-17
> **katie-xx said:**
> Hiya
This might be of interest:

[http://cgit.freedesktop.org/plymouth/tree/README](http://cgit.freedesktop.org/plymouth/tree/README)

Kate

Very interesting...from the web page you pointed to...

> 
It is designed to work on systems with DRM modesetting drivers.  The
idea is that early on in the boot process the native mode for the
computer is set, plymouth uses that mode, and that mode stays throughout
the entire boot process up to and after X starts.  Ideally, the goal is
to get rid of all flicker during startup.


Well it largely worked that way for me this morning, no command-line scrolling text or much flicker.  But how long will it last.  It seems little tweaks here and there that installing some software may cause or even updates can cause console text to start showing up again.

> 
For systems that don't have DRM mode settings drivers, plymouth falls
back to text mode.


Is that the bars?  The bars vs. scrolling text?  I don't know which is worse.

> 
In either text or graphics mode, the boot messages are completely
occluded.  After the root file system is mounted read-write, the
messages are dumped to /var/log/boot.log.  Also, the user can see the
messages at any time during boot up by hitting the escape key.


Found that little trick by accident.  But if you are hung up you might be able to hit ESC and find the offending bit.  It is good that the process is being recording for viewing in case of errors.

> 
plymouth supports various "splash" plugins which are analagous to
screensavers, but happen at boot time.  Currently there are three
graphical splash plugins: solar, fade-in, and spinfinity.  There are
also three non-graphical plugins which are for text mode and the
detailed view.


So they are animated then?  That would be interesting, no functional value, but interesting.;)

> 
Plymouth isn't done yet.  It's still under active development [B]and isn't
ready for distros to use as-is[/B].  That should change in the near future
though.


Everything in Linux and OSS is under active development.

But wait a minute here!  This is supposed to be a LTS release and they are using something critical to starting the system, that could stop it from booting right, that can not be used as-is?  That does not inspire a lot of confidence in me.:frown:

I know from working with Fedora periodically I get bars more than logos.

---

### Post by ranch hand on 2010-03-17
I am beginning to think that plymouth is a plot to not give you bars but to drive you into them.  Probably supported by the beer industry.

---

### Post by katie-xx on 2010-03-17
> **ranch hand said:**
> I am beginning to think that plymouth is a plot to not give you bars but to drive you into them.  Probably supported by the beer industry.

I like that :)

I would guess about half the user base might be able to receive a good Plymouth experience in the fullness of time. ....This is based on my non productive experience with the Fedora thing.
I do have to say though ... there seems to have been more effort made by Ubuntu developers than was ever the case in the other distro if all the updates are anything to go by.
Hope Springs Eternal ? :)


Kate

---

### Post by tekstr1der on 2010-03-17
> **ranch hand said:**
> ...Probably supported by the beer industry.

Haha ranch hand made a funny. Good one. 

Just for ships 'n giggles today at work, I installed today's daily CD (essentially the beta) on a quad-core with an Intel SSD. We have that stuff to play with at work, yay. Anyhow, Plymouth flashes by in about 1-2 seconds. Barely noticeable, and I was really looking for it. On today's modern hardware, this seems like a tremendous wasted of resources (human) time and effort to incorporate this into Ubuntu.

This LTS is shaping up nicely, it's stable, and tomorrow I'll be installing it on my new ThinkPad X201s. I would really prefer to see all that developer time and effort go toward squashing existing regression bugs to get this release as smooth as butta'. But, if I'm not contributing patches, I really have no say in the matter. It will certainly be the best release thus far.

---

### Post by Owen.C93 on 2010-03-17
Latest updates simply made the splash stay frozen for longer.

---

### Post by robert shearer on 2010-03-17
> **katie-xx said:**
> ....Hope Springs Eternal ? :)

Well I wish she would stop 'cause all that jumping up and down is giving me a headache. :)

---

### Post by teh603 on 2010-03-17
> **ranch hand said:**
> I am beginning to think that plymouth is a plot to not give you bars but to drive you into them.  Probably supported by the beer industry.Shame the only beer-type drink I've been able to stand is a Seagram's Black Cherry Fizz. Ain't been made since '03, as far as I can tell.

To be honest, LTSes aren't so much about stability as they are simply being supported longer for people who don't want to upgrade for every point release.

---

### Post by prodigy_ on 2010-03-17
> **teh603 said:**
> To be honest, LTSes aren't so much about stability
And this makes no sense. They should be all about stability/reliability. Bleeding edge isn't suitable for everything because some people actually want to use Linux for their servers and workstations.

---

### Post by Queue29 on 2010-03-17
> **prodigy_ said:**
> And this makes no sense. They should be all about stability/reliability. Bleeding edge isn't suitable for everything because some people actually want to use Linux for their servers and workstations.

So many things about Lucid make no sense. From the cheesy lens glare backdrop to the inclusion of useless, unstable software, Ubuntu 10.04 LTS will go down in linux-desktop history as a prime example of why linux can't get above 1% market share. 

Between MS, Apple, and Canonical, two of those companies don't ship with unstable software. Two of those companies don't change interface designs for no reason. Two of those companies don't expect the user to be able to use a command line. And two of those companies actually hire paid graphics/interface designers who know what the hell they are doing.

Ubuntu 10.4 LTS is supposed to be a stable, usable distribution **from the get-go.** It's pointless if it isn't deemed "stable" until the end of its lifespan. Let Fedora and the non LTS releases get the shiny, new, unstable stuff and try it out on people. Why the Ubuntu community doesn't understand the concept of producing a stable distro is just beyond me I guess.

---

### Post by cariboo on 2010-03-17
Where do people get the idea that an LTS release means stable? LTS stands for **L**ong **T**erm **S**upport.

---

### Post by ranch hand on 2010-03-17
> **Queue29 said:**
> So many things about Lucid make no sense. From the cheesy lens glare backdrop to the inclusion of useless, unstable software, Ubuntu 10.04 LTS will go down in linux-desktop history as a prime example of why linux can't get above 1% market share. 

Between MS, Apple, and Canonical, two of those companies don't ship with unstable software. Two of those companies don't change interface designs for no reason. Two of those companies don't expect the user to be able to use a command line. And two of those companies actually hire paid graphics/interface designers who know what the hell they are doing.

Ubuntu 10.4 LTS is supposed to be a stable, usable distribution **from the get-go.** It's pointless if it isn't deemed "stable" until the end of its lifespan. Let Fedora and the non LTS releases get the shiny, new, unstable stuff and try it out on people. Why the Ubuntu community doesn't understand the concept of producing a stable distro is just beyond me I guess.
I would, if I were you, seriously consider an OS from one of those 2 companies.

Myself, I switched from one of those two so that I could, for one thing, have a good, functional CLI.

---

### Post by VMC on 2010-03-17
> **Queue29 said:**
> So many things about Lucid make no sense. From the cheesy lens glare backdrop to the inclusion of useless, unstable software, Ubuntu 10.04 LTS will go down in linux-desktop history as a prime example of why linux can't get above 1% market share. 

Between MS, Apple, and Canonical, two of those companies don't ship with unstable software.....

Apparently you never ran Windows ME or Windows Vista, or ever saw a BSOD or ever had a virus...

---

### Post by kansasnoob on 2010-03-17
Well it's looking good now :guitar:

Not perfect but compared to Fedora 12 you can see the *buntu devs are really gaining. Hat tip to them all :D

BTW this thread is about Plymouth, not other controversial issues.

---

### Post by ranch hand on 2010-03-18
> **kansasnoob said:**
> Well it's looking good now :guitar:

Not perfect but compared to Fedora 12 you can see the *buntu devs are really gaining. Hat tip to them all :D

BTW this thread is about Plymouth, not other controversial issues.
Good God man what are you trying to do, be a voice of reason?

---

### Post by lidex on 2010-03-18
I had issues with plymouth previously so uninstalled it - or at least what I could uninstall. As I always get an error message on boot thought I'd reinstall and try the fix over at web upd8: [http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html]("http://www.webupd8.org/2010/03/how-to-get-plymouth-working-with-nvidia.html") so I wouldn't have to see it anymore. I am still shocked it actually worked and continues to do so. It's been a couple of days and the only real issue is that "bug in the script that's telling you it's a bug": [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262")

---

### Post by k3lt01 on 2010-03-18
Well after nearly a week mine is still working :popcorn:. It never worked until last friday night-saturday morning but its has worked since then. I just hope others get to see the improvements I have seen now. I am impressed that something, from I have read about and what people like katie-xx have said, has come so far in such a short time with the efforts the Ubuntu devs have put into it.

---

### Post by prodigy_ on 2010-03-18
> **cariboo907 said:**
> Where do people get the idea that an LTS release means stable? LTS stands for **L**ong **T**erm **S**upport.
And that's the problem.

---

### Post by Queue29 on 2010-03-18
> **cariboo907 said:**
> Where do people get the idea that an LTS release means stable? LTS stands for **L**ong **T**erm **S**upport.

Okay, so where do I find Ubuntu Stable & Supported edition?

---

### Post by ikt on 2010-03-18
> **cariboo907 said:**
> Where do people get the idea that an LTS release means stable? LTS stands for **L**ong **T**erm **S**upport.

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

More Tested: We will shorten the development window and extend the Beta cycle to allow for more testing and bug fixing

We will focus on hardening functionality of existing features, versus introducing new ones1, except for in the areas of Online Services and Desktop Experience2.

Instead of doing an automatic full package import from Debian unstable, we will do it from Debian testing1. The benefit we gain from not introducing new bugs and/or regressions outweighs the new features and/or fixes we often get from unstable.

All of these things point to a more stable release.

---

### Post by philinux on 2010-03-18
Latest boot experience. nVidia-current installed as that is what I will be using.

After grub..

Flashing cursor in upper top left for a few seconds.

3 identical fsck messages.

Plymouth arrives for [COLOR="Red"]**<1 second**[/COLOR] then a ureadahead error flashes very quickly.

GDM login to Desktop.

29 seconds boot according to bootchart.

---

### Post by teh603 on 2010-03-18
> **ikt said:**
> We will focus on hardening functionality of existing features, versus introducing new ones1, except for in the areas of Online Services and Desktop Experience2.

Lessee... Gwibber is an online service (and easily removed in Synaptic). Plymouth, the new themes, and moving the buttons are all desktop experience-related changes.

And for the record, Lucid even in its alpha state works better than Karmic ever did.

---

### Post by dino99 on 2010-03-18
> **philinux said:**
> Latest boot experience. nVidia-current installed as that is what I will be using.

After grub..

Flashing cursor in upper top left for a few seconds.

3 identical fsck messages.

Plymouth arrives for [COLOR="Red"]**<1 second**[/COLOR] then a ureadahead error flashes very quickly.

GDM login to Desktop.

29 seconds boot according to bootchart.

i've too some hard time when fsck/ureadahead/plymouth are running, ureadahead always ended with status 4

---

### Post by philinux on 2010-03-18
> **dino99 said:**
> i've too some hard time when fsck/ureadahead/plymouth are running, ureadahead always ended with status 4

Yeah thats it. By the way the boot experience I described never changes. Been like that for quite a while.

---

### Post by theozzlives on 2010-03-18
All I see is what looks like xsplash, but it's a gay purple.

---

### Post by philinux on 2010-03-18
> **theozzlives said:**
> All I see is what looks like xsplash, but it's a gay purple.

This is the default plymouth theme although it only on screen for <1 sec at boot and about 5 seconds on shutdown.

[http://www.omgubuntu.co.uk/2010/03/new-ubuntu-plymouth-theme-lands-in.html](http://www.omgubuntu.co.uk/2010/03/new-ubuntu-plymouth-theme-lands-in.html)

---

### Post by zika on 2010-03-18
> **philinux said:**
> This is the default plymouth theme although it only on screen for <1 sec at boot and about 5 seconds on shutdown.

[http://www.omgubuntu.co.uk/2010/03/new-ubuntu-plymouth-theme-lands-in.html](http://www.omgubuntu.co.uk/2010/03/new-ubuntu-plymouth-theme-lands-in.html)Maybe longer if shutdown doesn't work, as it doesn't in my case ...

---

### Post by Merk42 on 2010-03-18
> **Queue29 said:**
> Okay, so where do I find Ubuntu Stable & Supported edition?

ubuntu.com for either 9.10 or 8.04

Lucid is currently alpha (though today beta), so comparing it with RTM versions of other OSs is quite unfair.

---

### Post by ratcheer on 2010-03-18
I just tried the GRUB_GFXMODE and gfxpayload thing. On my system, plymouth works better without it. Actually booting is no better one way or the other - it is just bad.

Tim

---

### Post by MonsterTrimble on 2010-03-18
> **philinux said:**
> Latest boot experience. nVidia-current installed as that is what I will be using.

After grub..

Flashing cursor in upper top left for a few seconds.

3 identical fsck messages.

Plymouth arrives for [COLOR="Red"]**<1 second**[/COLOR] then a ureadahead error flashes very quickly.

GDM login to Desktop.

29 seconds boot according to bootchart.

My laptop would start up, get to the log-in screen then all control of the keyboard would stop along with prolonged flashes of white on the screen. I removed Plymouth (and with it the Lubuntu-desktop package) and it's worked flawlessly since except for an error stating that Plymouth is not installed. 

YMMV. I'm running a Toshina Satellite 1400 with Lubuntu Lucid Alpha 3.

---

### Post by Owen.C93 on 2010-03-18
For those who want the boot splash to last throughout boot (but may add a second or two) you can try installing "cryptsetup" from synaptic.

[The bug is here ]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/535108")which is where I got the workaround from.

BTW how do I make a bootchart?

---

### Post by cariboo on 2010-03-18
Install bootchart from the repositories, the app automagically creates the chart and stores it in /var/log/bootchart.

---

### Post by lidex on 2010-03-18
> **ratcheer said:**
> I just tried the GRUB_GFXMODE and gfxpayload thing. On my system, plymouth works better without it. Actually booting is no better one way or the other - it is just bad.

Tim
It worked surprisingly well for me. nvidia 8800 gts, nvidia current driver, ureadahead uninstalled. The only nouveau package installed is libdrm-nouveau1.

---

### Post by keypox on 2010-03-18
17 secs much better than 9.10.... pretty impressed on this laptop with 5400 hd.

---

### Post by Didius Falco on 2010-03-18
Plymouth itself is working well, though I haven't booted more than 4 times since it updated last -2 updates yesterday...

It isn't running the fsck check as often as it should, though. It's actually only checked it one time since plymouth was installed, and that time it quit at 71%.

---

### Post by ndefontenay on 2010-03-18
Got some plymouth related updates yesterday evening.
Still, no luck. Black lit screen, cursor on the left jumps to the top and finally I get in the GUI.

There is some improvement when getting in the GUI since the whole GUI shows at once rather than just skype only for 3-5 seconds then the rest.

---

### Post by cyberkilla on 2010-03-19
It's still showing console output before boot and at shutdown for me.

The progress bar on plymouth is a waste of time, because it doesn't denote any kind of progress. X starts before it reaches 100% at boot, and it barely gets 2 dots coloured in at shutdown.

---

### Post by amauk on 2010-03-19
> **cyberkilla said:**
> The progress bar on plymouth is a waste of time, because it doesn't denote any kind of progress. X starts before it reaches 100% at boot, and it barely gets 2 dots coloured in at shutdown.
That's the difference between running things in series (old Sys-V init system) and running them in parallel (upstart)

---

### Post by vishalrao on 2010-03-19
i would like to customise it a bit to remove the progressbar (dots) and get that circular logo spinning... that would be nice... (code ideas from the ubuntu sunrise plymouth theme)...

---

### Post by katie-xx on 2010-03-19
High hopes that a fresh install might clear out some of the dead wood from all the Plymouth changes but not to be Im afraid.
Im still getting the crash report ..which interestingly takes me to a PlymouthD not shut down report !!.
Something not quite right there I think :) 
Also the boot experience still falls some significant way short of what we used to have in Ubuntu and what we might reasonably expect from a distro aimed at the desktop.
I believe that is now a valid criticism as we have moved to beta and the boot process should be fully functional at this stage.
I do wonder exactly how deeply embedded Plymouth is into this distro as it shaping up to be a real shambles.
Better out than in IMHO.
Hopefully by tomorrow a Developer with super insight will appear and prove me wrong :)
Would anyone out there care to give me a betting price on that happening tho?

Kate

---

### Post by Muflon on 2010-03-19
> **katie-xx said:**
> Also the boot experience still falls some significant way short of what we used to have in Ubuntu and what we might reasonably expect from a distro aimed at the desktop.
I believe that is now a valid criticism as we have moved to beta and the boot process should be fully functional at this stage.

It would be nice if there were no issues remaining in the Beta but it generally doesn't happen that way.  A release is generally at its best just before the next one comes out :D

Muflon

---

### Post by katie-xx on 2010-03-19
> **Muflon said:**
> It would be nice if there were no issues remaining in the Beta but it generally doesn't happen that way.  A release is generally at its best just before the next one comes out :D
Muflon

Thanks for that I might bring it up at our next Whiteboard meeting :) 

Please take a little time to read through all the posts in this thread and you might get a feel for what the issues are.

Plymouth is shaping up to be a shambles or even worst a reputation destroyer. Im saying this because Ive seen it all before on other distros. In particular, Fedora either has a nice boot experience with pretty graphics, or the other 50% of its userbase has to put up with with horrible progress bars or hung boots or silly black screens like so many of us are seeing here. Plymouth drove a lot of people away from Fedora ..I know this for a fact as several of my friends at uni (at the time) gave up on it.

I have made several posts here which have credited the developers for trying .. there have been numerous updates .. in contrast to Fedora where the community preferred telling people to clear off if they didnt like the Plymouth disaster.

Now please give _me_ some credit ....Im sure that my colleagues and I would be looking for other jobs if we had a product in Beta which couldnt show a company splash. Im also sure the Ubuntu developers are switched on people and if it was a reasonably difficult task ..it would now be functioning properly.

Plymouth is shaping up to be a disaster and is likely to damage the reputation of Ubuntu big style if, like Fedora, it cant be put right for the majority of users.

Kate

---

### Post by Owen.C93 on 2010-03-19
A few things need to sorted out. But things that draw people away like the boot experience, well the bugs are hidden from view and marked as low :L

Still if you want the boot animation to work throughout (but still have plymouth crash) then open terminal and type:
```

echo FRAMEBUFFER=y | sudo tee  /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u



```It's usable.

Edit: Thanks to: [Scott  James Remnant , ]("https://launchpad.net/%7Escott")[Nicolò  Chieffo]("https://launchpad.net/%7Eyelo3") and plymouth dev [Steve  Langasek]("https://launchpad.net/%7Evorlon")for the workaround.

---

### Post by katie-xx on 2010-03-19
> **Owen.C93 said:**
> 
[/CODE]It's usable.

Edit: Thanks to: [Scott  James Remnant , ]("https://launchpad.net/%7Escott")[Nicolò  Chieffo]("https://launchpad.net/%7Eyelo3") and plymouth dev [Steve  Langasek]("https://launchpad.net/%7Evorlon")for the workaround.

No  .... its useable for some people. Not only that ..but I can just imagne going to my boss and saying ..hey I can work around that ..provided our client doesnt mind it crashing afterwards .... wise up  :)
Trust me! Been there ..got the T shirt seen it all b4 with this ... well I was going to say rubbish ..Im afraid Plymouth doesnt crack it as competent  ..sorry guys


Kate

---

### Post by Trespasser on 2010-03-19
I'll bet the Devs get it all sorted out pretty soon. I have faith in them and I'm sure so do a lot of other people.

---

### Post by katie-xx on 2010-03-19
> **Trespasser said:**
> I'll bet the Devs get it all sorted out pretty soon. I have faith in them and I'm sure so do a lot of other people.

Well how gai young man :) 
I hope your faith is justified. As for me ... I think its not to late to change direction with this one :)

---

### Post by bobcollard on 2010-03-19
Waited for first Beta in Xubuntu 10.04.  Tried Alpha 2 and got crash report, now the same thing, very disappoinitng, a day late and another crash.  What is PlymouthD?  Cannot find it in Synaptic to get rid of it.

---

### Post by keybuk on 2010-03-19
> **k3lt01 said:**
> Do a search on the forums, you will see a few threads where ureadahead has been identified as a problem. Both Ranch Hand and myself have mentioned it in this thread a few times.

Hi.

I'm the author of ureadahead.  And *I'm* not aware of it being a problem for anybody!

The only "issue" I know if is that you sometimes get an "exit with status 4" message on the console, which is a complete red herring - and will be hidden before we release Lucid.  (It means that ureadahead is actually working correctly, and isn't wasting time on one of the entries in your fstab)

Have you actually filed a bug with bootcharts with and without ureadahead?  Please do!  Also include the "ureadahead --dump" output.

Thanks

---

### Post by keybuk on 2010-03-19
> **prodigy_ said:**
> Desktop Linux distros still have serious, glaring, showstopper issues like video tearing in movie players and sound not working on every second laptop. And often there are no actual, universal solutions for these issues at all. I wonder when the Ubuntu team (and other development teams for that matter) will start paying attention to real problems instead of breaking things that have been working fine for years.

To fix issues like video tearing in movie players, you would expect to see major changes to the operating system architecture concerned with graphics drivers.

For example, rather than having graphics drivers in a userspace process, you might expect to see them because true kernel drivers in their own right.  This would lead to the possibility for all sorts of future improvements, up to syncing every screen update on a screen blank (the cause of tearing).

Unfortunately if you move graphics drivers up the stack, then other pieces might need to be changed.  For example you might not be able to use raw SVGA to draw a splash screen anymore, because it would interfere with these new graphics drivers and the architecture that will one day fix major problems like the ones you describe.

You might switch the splash screen code entirely so that it uses the new graphics drivers as well.

Sometimes we're not just breaking things for fun <g>

---

### Post by katie-xx on 2010-03-19
> **VMC said:**
> A voice for reason. My thinking is, this forum is for resolving issues and to help solve problems, and the "cafe" forums is for trash talking and other non issues.
This testing release forum is full of FUD.

Arent you the guy who was telling me the Plymouth problem wasnt Plymouth ? :)

If you think this problem is trash fair enough. I dont think it is trash ..I think it is a very important component of the distro.

I think I pointed out to you the two binaries involved here but you declined to respond. 

Ubuntu has a problem with plymouth.; So does Fedora and so does one of the netbook distros ..cant recall out of my head this moment :)

The answer is to discuss, post bugs ..there are plenty for Plymouth ,, and perhaps lobby for this particular component to be removed.

Now ... we are very lucky that the ureadahead author has deigned to visit us ... I would like to hear a little more about ureadahead ..perhaps he could be persuaded to visit us again and give an overview of his procedure?


Be happy


Kate

---

### Post by keybuk on 2010-03-19
> **vishalrao said:**
> i would like to customise it a bit to remove the progressbar (dots) and get that circular logo spinning... that would be nice... (code ideas from the ubuntu sunrise plymouth theme)...

Should be pretty easy; if you actually take a look at /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script it's just a scripting language drawing it -- you can doing pretty much anything with it

(I have dancing monkeys)

---

### Post by keybuk on 2010-03-19
> **katie-xx said:**
> Also the boot experience still falls some significant way short of what we used to have in Ubuntu and what we might reasonably expect from a distro aimed at the desktop.
I believe that is now a valid criticism as we have moved to beta and the boot process should be fully functional at this stage.
I do wonder exactly how deeply embedded Plymouth is into this distro as it shaping up to be a real shambles.
Better out than in IMHO.
Hopefully by tomorrow a Developer with super insight will appear and prove me wrong :)


Hello.

What experience problems are you having with Plymouth at the moment?  The last batch of updates running up to the ones that held up the Beta a bit should have fixed all of the "problems" (ie. things actually caused crashes and boot hangs and the like)

Obviously things are't quite shiny and sparkly yet, but it sounds like it's a surprise to you that it's deliberate.

You still see the odd console message (and that irritating one about ureadahead, and those fsck ones) because we've deliberately chosen not to disable them just yet.  After all, one of them might turn out to be important and a photo from a Beta 1 tester might reveal a clue to a bug.

And if you see the text version, you're seeing it because we're deliberately making you test it!  That's our ultimate fallback screen for people with graphics hardware we just don't have up to date drivers for.  It's no good if your ultimate fallback is your least tested code path -- as it turned out, it was a good idea that we did, since the text-based plugin caused a lot of the login crash problems that we've since fixed.

We have made a deliberate decision this release to prioritise working suspend/resume over a photo-quality splash screen, so when we do "turn on" the graphical splash for you, it won't be quite as pretty as those on other cards -- but we think most people prefer it if suspend worked.

There's a simple switch if you prefer a pretty splash to working suspend/resume; edit the /etc/default/grub file and add "video=vesafb" (or those vga=* arguments) to the default command-line.

---

### Post by katie-xx on 2010-03-19
> **keybuk said:**
> Hello.
What experience problems are you having with Plymouth at the moment?  The last batch of updates running up to the ones that held up the Beta a bit should have fixed all of the "problems" (ie. things actually caused crashes and boot hangs and the like)


Hi
A sensible poster and respect due.
im sorry but the issues are not fixed for ATI. My intel kit is fabulous but not the ATI kit.
its difficult to report a genuine bug ..mostly because when a crash report emerges we are transported to a bug report which basically denies the bug we want to report exists :) ....hey not unusual for debugging.
If I could make one sensible suggestion re: Plymouth ..I think if a structured test sheet was issued such as we use at work ...what u did ..expctd result etc ... I think it would help.
Just my humble opinion of course 

Kate

---

### Post by Half-Left on 2010-03-19
> **bobcollard said:**
> Yeah, it bugs ME.  Every startup I get a CRASH icon and I check it out and it say you have ore recently had an application crash.  Here I am wondering  "What Now?"  and it is this same old thing.  Fix Apport then, whatever.  My graphics drivers are built into the mother board, Mobile 4 or something like that, nothing special, just a computer that works with Xubuntu 9.04 and now it seems broken.  I didn't break it.  I still have a version of 9.04 running, just a different distro.  I know this is Beta but they said these things would be fixed in the extra day they took to release the Beta.  Sorry, trying not to vent.

It's still a beta and all things are not fixed. Get used to crashes while testing and while you're at it, expect things to explode.

---

### Post by keybuk on 2010-03-19
> **katie-xx said:**
> Hi
A sensible poster and respect due.
im sorry but the issues are not fixed for ATI. My intel kit is fabulous but not the ATI kit.
its difficult to report a genuine bug ..mostly because when a crash report emerges we are transported to a bug report which basically denies the bug we want to report exists :) ....hey not unusual for debugging.


Why not record a video of what you see, I'll take a look and help you file bug(s) for the problems you see - or point you at any existing bugs you might want to watch.

---

### Post by SaintStewart on 2010-03-19
> **katie-xx said:**
> Hi
A sensible poster and respect due.
im sorry but the issues are not fixed for ATI. My intel kit is fabulous but not the ATI kit.
its difficult to report a genuine bug ..mostly because when a crash report emerges we are transported to a bug report which basically denies the bug we want to report exists :) ....hey not unusual for debugging.
If I could make one sensible suggestion re: Plymouth ..I think if a structured test sheet was issued such as we use at work ...what u did ..expctd result etc ... I think it would help.
Just my humble opinion of course 

Kate



I gotta side with Katie on this one.  I posted a week or so back about Plymouth problems.  I came back for the beta, and....its STILL garbage.  Im using an Aspire AS1410.  Its a Celeron 1.3GHz, 4GB RAM, Intel GMA4500MHD. 

With the Beta, I can at least finally INSTALL the stupid thing, but I still have to CTRL-ALT-F2 to CLI then wait for it to load, hit CTRL-ALT-F7 to get to login screen when its done loading, type in my password, then C-A-F2 again, wait for it to load more, then C-A-F7 when its finally done.  Even after all that, the screen flashes and blinks all the time and the mouse cursor freezes and is jerky.  Oh and on top of all that, I have to manually connect to my home wifi every time I relog in.  

Im not sure whats going on (I know you'll tell me its something IM doing wrong, but this worked fine with 9.10), but you guys need to get it fixed fast.  You're about to (if not already) start bleeding users.

---

### Post by bobcollard on 2010-03-19
> **Half-Left said:**
> It's still a beta and all things are not fixed. Get used to crashes while testing and while you're at it, expect things to explode.
Did you read my reply at all?  I know what a beta is, I have a backup system and I keep earlier kernels in grub too.  Not a newby here.

---

### Post by Half-Left on 2010-03-19
> **katie-xx said:**
> Hi
A sensible poster and respect due.
im sorry but the issues are not fixed for ATI. My intel kit is fabulous but not the ATI kit.
its difficult to report a genuine bug ..mostly because when a crash report emerges we are transported to a bug report which basically denies the bug we want to report exists :) ....hey not unusual for debugging.
If I could make one sensible suggestion re: Plymouth ..I think if a structured test sheet was issued such as we use at work ...what u did ..expctd result etc ... I think it would help.
Just my humble opinion of course 

Kate

Drivers are actually part of the problem yes. You have to remember that the FOSS people are not going to be held down by the proprietary people.

Just take KMS. It was design to be opensource driver friendly of course but not proprietary friendly. The NVIDIA binary doesn't work with KMS at all. Can you guess why that is?

Binary blobs cause issues that cannot be fixed by Canonical.

---

### Post by Owen.C93 on 2010-03-19
> **SaintStewart said:**
> I gotta side with Katie on this one.  I posted a week or so back about Plymouth problems.  I came back for the beta, and....its STILL garbage. 

Posted on the forums or a bug on launchpad? Unless you filed a bug don't expect it to be fixed....or quickly at least.

I don't know why you are having trouble but make sure you are using the Nouveau drivers and a fully updated plymouth.

---

### Post by Half-Left on 2010-03-19
> **bobcollard said:**
> Did you read my reply at all?  I know what a beta is, I have a backup system and I keep earlier kernels in grub too.  Not a newby here.

Then if you don't like testing and having such issues, don't use it. Alphas  and betas are for testing, not ranting about common issues like things not working and crashing.

---

### Post by SaintStewart on 2010-03-19
> **Owen.C93 said:**
> Posted on the forums or a bug on launchpad?

Both.

---

### Post by keybuk on 2010-03-19
> **katie-xx said:**
> Not you of course !!!!
Wow def not u
I said Ill pm u and I will ..... the general replies Ive had 2nite are abuse sorry 

wow ....def not u


Kate

Ah ok ;-)  I got confused as you were replying to me.

Us developers don't get into the forums much, so not entirely sure how things work here

---

### Post by Half-Left on 2010-03-19
> **bobcollard said:**
> When someone puts it into writing that it is fixed, you have a right to rant when it's still broken.  Common issues?  There is nothing common about something they knew was broken and still put it out.  9.10 was a perfect example, let the users hack it out in the forums.  Then fix it in the updates.  This is supposed to be a long term edition.  It's been through 3 Alphas, the "Common issues" should be fixed.

It's still testing, things can be re-broken so as I said, if you don't like things being broken, stick to the stable releases. Anyway, as long as they fix issues quick after release, it's not a problem. Microsoft and Apple do it all the time so nobody is perfect.

---

### Post by Half-Left on 2010-03-19
> **katie-xx said:**
> OmG ... u have not understood a word Ive posted have u?

U must be American ....please tell me u arent British.


Kate

Well, what? 35 pages of ranting achieved what exactly?

---

### Post by keybuk on 2010-03-19
> **Half-Left said:**
> Drivers are actually part of the problem yes. You have to remember that the FOSS people are not going to be held down by the proprietary people.

Just take KMS. It was design to be opensource driver friendly of course but not proprietary friendly. The NVIDIA binary doesn't work with KMS at all. Can you guess why that is?

Binary blobs cause issues that cannot be fixed by Canonical.

Well, to be entirely fair to nVidia here, the kernel developers have deliberately implemented the "Kernel Mode Setting" subsystem in a way that makes it illegal for nVidia to make their binary driver support KMS.

It's pressure for nVidia to actually open source their driver, at least I suspect that's how they see it.

---

### Post by SaintStewart on 2010-03-19
> **Half-Left said:**
> Well, what? 35 pages of ranting achieved what exactly?

Troll is troll.  If youre not here to be a part of the solution, then how are you any better?  Your hate spew all over the place isn't helping either.  Keep it up.  You make the other Trolls happy.

---

### Post by ronacc on 2010-03-19
I can attest to the fact that the plymouthd crash message is not cured .Did my evening update at 2000 hrs east coast US , rebooted and got the message as usual . My sys is Nvidia . I really don't expect plymouth to work with Nvidia and don't care either since I don't get my kicks staring drooling and mumbling ooo shiny for the few seconds it takes my box to boot.

---

### Post by bobcollard on 2010-03-19
> **Half-Left said:**
> Well, what? 35 pages of ranting achieved what exactly?
Plymouth is still broken, nice point.  That's not British humor.  You must be American.

---

### Post by keybuk on 2010-03-19
> **teh603 said:**
> Honestly, I wouldn't be surprised if Plymouth gets canned for the next version. Its been that huge of a headache.

Why?  There's been some fun bugs, but nothing like the recurring nightmare that was the SVGA code in usplash.  We honestly don't want to go back to *that*.

---

### Post by Half-Left on 2010-03-19
> **keybuk said:**
> Well, to be entirely fair to nVidia here, the kernel developers have deliberately implemented the "Kernel Mode Setting" subsystem in a way that makes it illegal for nVidia to make their binary driver support KMS.

It's pressure for nVidia to actually open source their driver, at least I suspect that's how they see it.

Yes. I think it's unfair to do that because from what I've heard, NVIDIA cannot opensource their driver because of third party code and licenses. 

FOSS tend to walk a fine line when dealing with this sort of issue, and stepping into the Grey areas without thinking.

---

### Post by keybuk on 2010-03-19
> **Half-Left said:**
> Yes. I think it's unfair to do that because from what I've heard, NVIDIA cannot opensource their driver because of third party code and licenses.

Oh, that's almost certainly ******** on their part ;-)  Nobody believes that, not even people *at* NVIDIA.

They won't open source their driver because it shows the worrying number problems their hardware has that the driver covers up.  Allegedly ;)

---

### Post by VMC on 2010-03-19
> **keybuk said:**
> Why?  There's been some fun bugs, but nothing like the recurring nightmare that was the SVGA code in usplash.  We honestly don't want to go back to *that*.

Plymouth is working for me 90% of the time. Occasionally I don't see a splash.

The topic came also regarding the "fsck" that is always coming up just before the splash. Is that part of plymouth or mountall asking for fsck. I'm not talking about the fsck that checks when you reach the 35 boot limit.

Also, on one of the bug reports it was suggested to install cryptest(I think that's what its called). I installed cryptest and plymouth works perfectly. The trade-off is that it adds 4-5 seconds to boot.

---

### Post by NightwishFan on 2010-03-19
I watched a few interviews of Mark, and I have found myself convinced. I will put my faith in Canonical/Ubuntu. Plymouth is mostly non-working here, but when I get a disk check it looks epic. ;)

---

### Post by ronacc on 2010-03-19
> **keybuk said:**
> Well, to be entirely fair to nVidia here, the kernel developers have deliberately implemented the "Kernel Mode Setting" subsystem in a way that makes it illegal for nVidia to make their binary driver support KMS.

It's pressure for nVidia to actually open source their driver, at least I suspect that's how they see it.

If they are using plymouth as a whip to beat Nvidia with they will only suceed in alienating the large percentage of users who have Nvidia cards and also spitting in the face of a company that has supported Linux by providing drivers for their cards for a long time , I am thankful that Nvidia puts up with the disgraceful way their efforts are treated by some in the linux community and hope they continue to do so .

---

### Post by keybuk on 2010-03-19
> **VMC said:**
> Plymouth is working for me 90% of the time. Occasionally I don't see a splash.

The topic came also regarding the "fsck" that is always coming up just before the splash. Is that part of plymouth or mountall asking for fsck. I'm not talking about the fsck that checks when you reach the 35 boot limit.

Also, on one of the bug reports it was suggested to install cryptest(I think that's what its called). I installed cryptest and plymouth works perfectly. The trade-off is that it adds 4-5 seconds to boot.

Well, the message appearing is just because I haven't hidden it yet; that'll be hidden before we release.

Getting Plymouth visible a bit quicker is a priority, because right now it's actually - as you point out - quite a way through the boot sequence.  This is because the graphics drivers take a while to load.

Installing cryptsetup reorders the boot such that the graphics drivers are loaded very early, so you see the splash much longer, but the side-effect of this is as you point out, a 4-5 second increase in boot time.

I'm working on that problem.

---

### Post by Half-Left on 2010-03-19
> **keybuk said:**
> Oh, that's almost certainly ******** on their part ;-)  Nobody believes that, not even people *at* NVIDIA.

They won't open source their driver because it shows the worrying number problems their hardware has that the driver covers up.  Allegedly ;)

hehe. but still, FOSS do like that Grey area and tend to believe they're right while standing in it.

---

### Post by FishRCynic on 2010-03-19
used to always use (and currently) a nvidia card for compatibility reasons lol - figures

---

### Post by teh603 on 2010-03-19
> **ronacc said:**
> If they are using plymouth as a whip to beat Nvidia with they will only suceed in alienating the large percentage of users who have Nvidia cards and also spitting in the face of a company that has supported Linux by providing drivers for their cards for a long time , I am thankful that Nvidia puts up with the disgraceful way their efforts are treated by some in the linux community and hope they continue to do so .

+1

I don't agree with smacking nVidia like that either. There's so little corporate support for Linux compared to other OSes (mainly windoze), and we don't need to do something which will probably end up hurting us. Replacing the bootsplash with something else that doesn't specifically conflict with nVidia would be a much better decision.

Besides, from what I read Nouveau is even worse than the nVidia drivers.

---

### Post by VMC on 2010-03-19
> **keybuk said:**
> Well, the message appearing is just because I haven't hidden it yet; that'll be hidden before we release.

Getting Plymouth visible a bit quicker is a priority, because right now it's actually - as you point out - quite a way through the boot sequence.  This is because the graphics drivers take a while to load.

Installing cryptsetup reorders the boot such that the graphics drivers are loaded very early, so you see the splash much longer, but the side-effect of this is as you point out, a 4-5 second increase in boot time.

I'm working on that problem.Great news, and thanks for sharing your views. Its nice to here from the devs in this critical time of development.

 I have an Intel i865, and although not as powerful as nVidia, ATI, or other Intels, I haven't had the major issues plaguing the others...nor the wonderful 3-D effects effects the others have.

---

### Post by FishRCynic on 2010-03-19
[http://ubuntuforums.org/showthread.php?t=1434053](http://ubuntuforums.org/showthread.php?t=1434053)

its not "broke" it's just beta testing

---

### Post by Half-Left on 2010-03-19
> **teh603 said:**
> +1

I don't agree with smacking nVidia like that either. There's so little corporate support for Linux compared to other OSes (mainly windoze), and we don't need to do something which will probably end up hurting us. Replacing the bootsplash with something else that doesn't specifically conflict with nVidia would be a much better decision.

Besides, from what I read Nouveau is even worse than the nVidia drivers.

Well, why would the kernel devs make it even more binary friendly? They make the interface with the proprietary binaries which taints the kernel.

Nouveau is actually better than the NVIDIA binary in 2D speed and has such features as KMS. In the end both drivers want access to the hardware and they cannot share it.

---

### Post by ronacc on 2010-03-19
> **Half-Left said:**
> Well, why would the kernel devs make it even more binary friendly? They make the interface with the proprietary binaries which taints the kernel.

Nouveau is actually better than the NVIDIA binary in 2D speed and has such features as KMS. In the end both drivers want access to the hardware and they cannot share it.

It all depends on what their goal is , is it to improve the linux experience for users or is it to push some Idealogical agenda .

---

### Post by keybuk on 2010-03-19
> **ronacc said:**
> It all depends on what their goal is , is it to improve the linux experience for users or is it to push some Idealogical agenda .

It's actually the former.

We don't have the source code for the nVidia drivers; so there is absolutely nothing we do about all the bugs with them, and nothing we can do about all the other bugs they cause.

To improve the Linux experience for users, we need the source code to those drivers; since we don't have it, the Linux community has had to resort to writing its own (nouveau).

While they may not be as good *yet*, we can actually fix bugs in them, triage problems, etc.  So the experience will be better!

---

### Post by ibuclaw on 2010-03-19
I'm currently using the Xorg Edgers PPA, and report no big issues with them (if we ignore ACPI for a moment here).

They can be added via: [NOPARSE]add-apt-repository ppa:xorg-edgers/ppa[/NOPARSE]
Though if someone will want to clarify whether or not it is still necessary to use the PPA, then let me know. :)

> **Owen.C93 said:**
> Jesus Christ.

Anyway It's 1:20am in the UK so I think we should take a break and come back to it tomorrow. See you then :)

/me hits the sack.

---

### Post by teh603 on 2010-03-19
> **keybuk said:**
> It's actually the former.

We don't have the source code for the nVidia drivers; so there is absolutely nothing we do about all the bugs with them, and nothing we can do about all the other bugs they cause.

To improve the Linux experience for users, we need the source code to those drivers; since we don't have it, the Linux community has had to resort to writing its own (nouveau).

While they may not be as good *yet*, we can actually fix bugs in them, triage problems, etc.  So the experience will be better!Can you list some of those bugs? I haven't seen any, but that doesn't mean they don't exist. Just means I'm not a programmer and don't usually go under the hood unless its an easy fix like the SierraWireless Mercury cell modem fix in Intrepid.

---

### Post by cyberkilla on 2010-03-19
Well, I look forward to /not/ seeing the console output in between Plymouth appearances.

Fingers crossed that the new GDM and Plymouth will gain more substantial theming tools at some point down the line; something sorely missed since we lost usplash and the old GDM.

---

### Post by keybuk on 2010-03-19
> **cyberkilla said:**
> Well, I look forward to /not/ seeing the console output in between Plymouth appearances.

Fingers crossed that the new GDM and Plymouth will gain more substantial theming tools at some point down the line; something sorely missed since we lost usplash and the old GDM.

I find that last point a bit baffling; in order to theme usplash, you had to create a shared library with appropriate bits in random places, hardly "easy".

Theming Plymouth is a dream in comparison, take a look at /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script

It's a doddle to write whatever you like in that language, just drop it in a directory under /lib/plymouth/themes with the appropriate *.plymouth file as well (see the one alongside ubuntu-logo for an example).

I'm honestly looking forwards to seeing what the artistic members of our community do with it!

---

### Post by cyberkilla on 2010-03-19
> **keybuk said:**
> I'm honestly looking forwards to seeing what the artistic members of our community do with it!

Yes, I agree, I shouldn't have referenced usplash so directly in my previous message.

The updated GDM and other aspects of Ubuntu have (indirectly and in the case of GDM, inevitably) reduced its customisability. Whilst it is technically possible to change some things, the graphical tools haven't really caught up, AFAIK.

Strange design decisions have impeded customisation too; for instance, NotifyOSD, which you can't even recolour. Of all computer users, the demographic Ubuntu targets is the most likely to want to customise the look of their computer. This is somewhat off-topic, however.

---

### Post by VMC on 2010-03-19
> **keybuk said:**
> ...
Theming Plymouth is a dream in comparison, take a look at /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script

It's a doddle to write whatever you like in that language, just drop it in a directory under /lib/plymouth/themes with the appropriate *.plymouth file as well (see the one alongside ubuntu-logo for an example).

I'm honestly looking forwards to seeing what the artistic members of our community do with it!

...and I was impressed with solar:
```
sudo plymouth-set-default-theme solar --rebuild-initrd

```
Now that I think about it, when I used the above solar rebuild, plymouth never failed.


I'm probably more limited with my video card than anything else.

Edit: I re-installed solar and rebooted several times and not once did plymouth fail. So why does it fail at times, using the default Ubuntu logo and those red dots?

---

### Post by SaintStewart on 2010-03-19
If it helps any, every time I finally get to my desktop after reboot, I get a crash of "plymouthd".

---

### Post by VMC on 2010-03-19
> **SaintStewart said:**
> If it helps any, every time I finally get to my desktop after reboot, I get a crash of "plymouthd".

You might be suffering from this [**_bug_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262").

---

### Post by k3lt01 on 2010-03-19
> **keybuk said:**
> Hi.

I'm the author of ureadahead.  And *I'm* not aware of it being a problem for anybody!

The only "issue" I know if is that you sometimes get an "exit with status 4" message on the console, which is a complete red herring - and will be hidden before we release Lucid.  (It means that ureadahead is actually working correctly, and isn't wasting time on one of the entries in your fstab)

Have you actually filed a bug with bootcharts with and without ureadahead?  Please do!  Also include the "ureadahead --dump" output.

Thanks

Here's some links for you to take a squiz at.

[http://ubuntuforums.org/showthread.php?t=1419477&highlight=ureadahead](http://ubuntuforums.org/showthread.php?t=1419477&highlight=ureadahead)

[http://ubuntuforums.org/showthread.php?t=1352578&highlight=ureadahead](http://ubuntuforums.org/showthread.php?t=1352578&highlight=ureadahead)

[http://ubuntuforums.org/showthread.php?t=1376994&highlight=ureadahead](http://ubuntuforums.org/showthread.php?t=1376994&highlight=ureadahead)

[http://ubuntuforums.org/showthread.php?t=1404962&highlight=ureadahead](http://ubuntuforums.org/showthread.php?t=1404962&highlight=ureadahead)

[http://ubuntuforums.org/showthread.php?t=1401801&highlight=ureadahead](http://ubuntuforums.org/showthread.php?t=1401801&highlight=ureadahead)

[http://ubuntuforums.org/showthread.php?t=1379275&highlight=ureadahead](http://ubuntuforums.org/showthread.php?t=1379275&highlight=ureadahead)

If you have any other questions on ureadahead feel free to get back to me, maybe in a thread related to it specifically. I know its a useful thing but it just causes a huge bottleneck on my little old laptop.

---

### Post by FrancoNero on 2010-03-19
so what's going on with plymouth? beta is here and all i see is a purple screen that sais ubuntu and some dots (all text), same with shutdown, only there it gives excerpts from a terminal screen saying there was a kill signal and it will shutdown.

i thought there was supposed to be a nic elogo and all that?

btw: I think the system boots so fast, who needs a boot splash? just make it a little faster and skill the whole thing.....

---

### Post by ranch hand on 2010-03-20
> **keybuk said:**
> Hello.

What experience problems are you having with Plymouth at the moment?  The last batch of updates running up to the ones that held up the Beta a bit should have fixed all of the "problems" (ie. things actually caused crashes and boot hangs and the like)

Obviously things are't quite shiny and sparkly yet, but it sounds like it's a surprise to you that it's deliberate.

You still see the odd console message (and that irritating one about ureadahead, and those fsck ones) because we've deliberately chosen not to disable them just yet.  After all, one of them might turn out to be important and a photo from a Beta 1 tester might reveal a clue to a bug.

And if you see the text version, you're seeing it because we're deliberately making you test it!  That's our ultimate fallback screen for people with graphics hardware we just don't have up to date drivers for.  It's no good if your ultimate fallback is your least tested code path -- as it turned out, it was a good idea that we did, since the text-based plugin caused a lot of the login crash problems that we've since fixed.

We have made a deliberate decision this release to prioritise working suspend/resume over a photo-quality splash screen, so when we do "turn on" the graphical splash for you, it won't be quite as pretty as those on other cards -- but we think most people prefer it if suspend worked.

There's a simple switch if you prefer a pretty splash to working suspend/resume; edit the /etc/default/grub file and add "video=vesafb" (or those vga=* arguments) to the default command-line.
I have no idea a what problem katie-xx is having with plymouth but I can tell you that purging ureadahead and reinstalling ureadahead has madi it possible for  me to boot my system as recently as last week.

Removing plymouth improves performance by about 25% on my box.  I have only done this on one of 5 nearly identical installs on this box.  Then I only get a message that plymouth can't be contacted and the boot goes on from there fine and fast.

No one is attacking ureadahead.  Ureadahead is a problem inside the plymouth problem.  Without plymouth ureadahead works fine.

I have never been a Fedora fan.  My experience with Linux is basically from my join date on these forums.  I tried fedora and had a hell of a time booting.  This was cured, on a second install of whatever version that was  by removing plymouth from an install of Ubuntu.  That is why I am still here.  No plymouth.

Now, I like katie-xx, am hoping that the Ubuntu devs can get this right.

Ureadahead is part of the problem in that it does not inter act with plymout his a constructive way.  What a shock.  The kernel does not either.

As far as I can see nothing does and the only reason to use plymouth is that fedora does.  "If all your friends were jumping of a bridge would you?" as my mother used to ask.

We need this crap so that people with less than 15 second attention span can have stimulation.  Great let us ruin an Ubuntu version so a few people can have a pacifier for the duration of the long boot process.

Removing plymouth and leaving uread ahead alone is good for a gain on this bos of about 15 seconds.  No I am not going to show you the bootchart .  That is because it does not work either.  You can doubt this statement.  I will be happy to send screen shots of my file system that will show that the gzip files are there and the pybootchart images are not.  Boot chart does not work on my box any more than (and perhaps less than Plymouth).  If you can not believe, as many can't that 9.04 boots in almost half the time that is fine.

I have been judging time for longer than you have been born (probably). The boot experience in 10.04 is terrible.  9.04 is damn near twice as fast.

With out plymouth 10.04 is very much faster than 9.01.

---

### Post by k3lt01 on 2010-03-20
> **ranch hand said:**
> No one is attacking ureadahead. Correct

> **ranch hand said:**
> Ureadahead is a problem inside the plymouth problem.  Without plymouth ureadahead works fine.Incorrect, Ureadahead has been playing up on me before Plymouth ever got onto my PCs. They both have issues that are most definitely separate from each other. I'll go further and comment more on Plymouth, until I removed bootchart and pybootchart (I think that's its name) Plymouth would NOT work for me at all. After removing them Plymouth started to do things it should have been doing but not doing it properly. Now since updating last weekend Plymouth is finally doing what it should.

In other words Plymouth, like you said, doesn't work well with other programs but Ureadahead isn't the cause of Plymouth's issues and vice versa.

---

### Post by ratcheer on 2010-03-20
> **ranch hand said:**
>  ....

 If you can not believe, as many can't that 9.04 boots in almost half the time that is fine.

I have been judging time for longer than you have been born (probably). The boot experience in 10.04 is terrible.  9.04 is damn near twice as fast.



I am having a very similar experience to ranch hand's. 9.10 boots effortlessly on my system. When I try to do a normal boot of Lucid, I get the purple plymouth screen for a few seconds, then my disk starts clicking and grinding away, then the screen goes black and the disk keeps clicking and grinding. If this disk thrashing last more than about 90 seconds, and it usually does, I hard-reset my computer and do a recovery mode boot and drop to a root prompt. Then, I start gdm and the desktop comes up, almost immediately. Then, everything seems to work, perfectly.

I am not as experienced with Linux problems as many. I have no idea what is causing the disk thrashing or how I would gather any info on it to support a bug report. I don't know if it is plymouth, or ureadahead, or an interaction between them, or something else entirely. But what I do know is that it never happens on Karmic and it always happens on Lucid. The Disk Utility applet shows my drive's status as "Healthy".

Also, I have to run the nVidia proprietary driver because I am testing for the Xorg Proprietary Drivers test team.

Tim

---

### Post by ranch hand on 2010-03-20
> **keybuk said:**
> Why?  There's been some fun bugs, but nothing like the recurring nightmare that was the SVGA code in usplash.  We honestly don't want to go back to *that*.
Usplash was alright compared to plymouth.  Xsplash was a dream.

Check my sig.  I do not use nvidea.

---

### Post by vishalrao on 2010-03-20
thanks @keybuk for taking the time to read the forum. i will try customising the ubuntu-logo plymouth theme to get a spinning COF logo...

i am certainly looking forward to lucid/plymouth/nouveau a lot - not too many complaints from me :D

---

### Post by VMC on 2010-03-20
> **vishalrao said:**
> thanks @keybuk for taking the time to read the forum. i will try customising the ubuntu-logo plymouth theme to get a spinning COF logo...

i am certainly looking forward to lucid/plymouth/nouveau a lot - not too many complaints from me :D

Since I added solar theme, plymouth has **never** failed.

---

### Post by josefcub on 2010-03-20
> **ranch hand said:**
> Usplash was alright compared to plymouth.  Xsplash was a dream.

Sadly, I have to second the above sentiment.  A purple text-mode bootup screen?  Seriously?

I do use nVidia on both my laptop and desktop, and the DOS-esque Plymouth boot screen and logging in did function.  They could save even more boot time by simply dumping a text file to stdout on bootup. :rolleyes:

I think I'd prefer to have Karmic's usplash/xsplash combo instead.  At least it looked nice, if nothing else.  Does anyone think they'll forward-port that interface for those of us who actually end up having to look at their bootup/shutdown screens?

---

### Post by vishalrao on 2010-03-20
> **keybuk said:**
> Should be pretty easy; if you actually take a look at /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.script it's just a scripting language drawing it -- you can doing pretty much anything with it

(I have dancing monkeys)

> **vishalrao said:**
> thanks @keybuk for taking the time to read the forum. i will try customising the ubuntu-logo plymouth theme to get a spinning COF logo...

i am certainly looking forward to lucid/plymouth/nouveau a lot - not too many complaints from me :D

@keybuk, I have it working too with a spinning COF logo! :D I noticed a possible bug where logo.sprite.Set**Y** is called in the third lines where Alberto Milone probably wanted Set**Z** which was causing me a little grief! Will file a quick bug on that. Thats probably why he wrote that draw_logo() function with the comment that "plymouth doesnt seem to draw properly without this" because that function has it set properly :)


> **VMC said:**
> Since I added solar theme, plymouth has **never** failed.

@VMC I wonder if its because of that little typo-bug SetY/SetZ I think I saw? :)

---

### Post by vishalrao on 2010-03-20
edit: ok bug filed at [lpbug]542458[/lpbug] i hope im not wasting precious developer time with these things :lolflag: anyone care to confirm it?

---

### Post by lidex on 2010-03-20
> **VMC said:**
> ...and I was impressed with solar:
```
sudo plymouth-set-default-theme solar --rebuild-initrd

```
Now that I think about it, when I used the above solar rebuild, plymouth never failed.


I'm probably more limited with my video card than anything else.

Edit: I re-installed solar and rebooted several times and not once did plymouth fail. So why does it fail at times, using the default Ubuntu logo and those red dots?

Wow. Thanks for that. Shutdown/Startup now seamless and themed.

---

### Post by vishalrao on 2010-03-20
Ok got a decent plymouth splash with spinning logo as posted in the theming thread: [http://ubuntuforums.org/showpost.php?p=8997516&postcount=97](http://ubuntuforums.org/showpost.php?p=8997516&postcount=97)  - ok i need a life :lolflag:

---

### Post by Owen.C93 on 2010-03-20
lol.

If anyone cares I installed burg which matches plymouth rather nicely.

---

### Post by uRock on 2010-03-20
I think Plymouth is running sweet.

---

### Post by tad1073 on 2010-03-20
> **iRock said:**
> I think Plymouth is running sweet.

It is not running proper for me, I get the solid purple background with the 8 bit font ubuntu w/no logo

---

### Post by vishalrao on 2010-03-21
+1 about the themability part :) look at my uber hacking/artistic skillzzzz yo! [http://www.youtube.com/watch?v=dZuWdMsIed8](http://www.youtube.com/watch?v=dZuWdMsIed8)

---

### Post by k3lt01 on 2010-03-21
A little bit of an update regarding the ureadahead issue keybuk is working on.

Because I have both Karmic and Lucid on my laptop I have done (succeeded with Karmic,tried with Lucid) what Keybuk asked us to do in [this thread]("http://ubuntuforums.org/showthread.php?t=1434502").

I reinstalled everything he asked and in the case of Lucid I have not been able to keep the machine running long enough without it either crashing or rebooting to the log on screen. It seems to me that the rebooting issue is because of bootchart and bootchartpy (sp?) as it seems one of these two is crashing plymouthd badly.

I have asked his advice as to what steps he wants me to take next.

I just wanted to say, I have read alot of comments in various threads about the devs not taking part in the forums, and I can understand why they don't have the time, but to me keybuk has stepped up above and beyond the call of duty. I have never had a negative experience with an Ubuntu dev yet but keybuk has just just shown how much dedication these people have to their chosen vocation.

Keybuk, I'll buy you a drink (of your choosing, tea?) any day ;).

---

### Post by ranch hand on 2010-03-21
pybootchartgui

The thing doesn't work on most of my installs.  Bootchart itself doesn't work on a couple, can't blame pybootchart for not being able to read tgz files that I can't get to open.

---

### Post by k3lt01 on 2010-03-21
> **ranch hand said:**
> pybootchartgui

The thing doesn't work on most of my installs.  Bootchart itself doesn't work on a couple, can't blame pybootchart for not being able to read tgz files that I can't get to open.I don't remember saying anyone else could blame anything, I can however blame at least 1 of the 2 because in the minute moment the machine was running before it kept rebooting an error report was produced point out 1 of them. Which one I don't know cause I can't keep it running long enough to read it properly. Anyway, I gave my account just incase others have a similar thing happening.

---

### Post by Sef on 2010-03-21
Since the thread had gotten badly off-topic, I removed any thread that was not directly related to the title.  Thank you all who have been posting on-topic.

---

### Post by eris23 on 2010-03-21
Currently working with Nvidia binary driver on my machine.

In /etc/default/grub:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"

In /etc/initramfs-tools/conf.d:
FRAMEBUFFER=y

A few ureadahead errors pop up.

I had poorer luck with the Nouveau driver.

---

### Post by ibuclaw on 2010-03-21
> **teh603 said:**
> Can you list some of those bugs? I haven't seen any, but that doesn't mean they don't exist. Just means I'm not a programmer and don't usually go under the hood unless its an easy fix like the SierraWireless Mercury cell modem fix in Intrepid.

See here for our nouveau compatibility list: [https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

Still needs a bit updating, and is not quite official. :)

Regards
Iain

---

### Post by cowlip1 on 2010-03-21
> **eris23 said:**
> 

In /etc/initramfs-tools/conf.d:
FRAMEBUFFER=y


Sorry, where is the file to set this?  On my system, that "conf.d" is a directory, so I can't edit it.

---

### Post by eris23 on 2010-03-21
> **cowlip1 said:**
> Sorry, where is the file to set this?  On my system, that "conf.d" is a directory, so I can't edit it.

Sorry.
/etc/initramfs-tools/conf.d/splash

---

### Post by ronacc on 2010-03-21
still not working on my sys , never has , crashes every boot .

---

### Post by prodigy_ on 2010-03-21
By the way, I've found out that after ```
sudo apt-get remove --purge plymouth
``` startup and especially shutdown times decrease noticeably. This leads to a question - why do we need plymouth in default installation at all? It certainly doesn't do anything even remotely useful **and** it makes user experience worse. Looks counter-productive to me...

---

### Post by emarkay on 2010-03-21
**So what are the facts here?**
It really seems that this Plymouth is both useless *and* flawed.
Will someone please get to the bottom of this before RC time!

---

### Post by cowlip1 on 2010-03-21
I keep these horrible images whenever I boot up or shut down, using the binary nVidia driver.

I'm going to try booting with that Framebuffer option now though.  Hopefully it will do the trick.

---

### Post by VMC on 2010-03-21
> **prodigy_ said:**
> By the way, I've found out that after ```
sudo apt-get remove --purge plymouth
``` startup and especially shutdown times decrease noticeably. This leads to a question - why do we need plymouth in default installation at all? It certainly doesn't do anything even remotely useful **and** it makes user experience worse. Looks counter-productive to me...

I asked myself the same question a couple of alphas ago. There must be a reason other than supplying a splash. There's a lot of packages related to plymouth. I too noticed that it booted faster, but was afraid that some needed programs wasn't being run at startup. BTW, right now using plymouth, it boots the fastest ever.

---

### Post by ranch hand on 2010-03-22
> **VMC said:**
> I asked myself the same question a couple of alphas ago. There must be a reason other than supplying a splash. There's a lot of packages related to plymouth. I too noticed that it booted faster, but was afraid that some needed programs wasn't being run at startup. BTW, right now using plymouth, it boots the fastest ever.
I am glad that it is booting for you finally.

It has been booting for me but it is slow.  Way slower than 9.10 and it is also slower than 9.04.  Right now, if i can believe bootchart that only works on any of my installs occasionally, it is at about 1.04 minutes.  Shut down takes at least as long if not longer.

Seeing that it does boot on all my installs now I will be leaving it on all of them.  When the release comes out it is off of here.

There is not really anything I can find that depends on it to function right.  Mountall will throw an error message if plymouth is removed.  I can live with that quite unbothered.

Without plymouth shut down is just about instantanious and boot is in the mid 30s.

---

### Post by k3lt01 on 2010-03-22
> **ranch hand said:**
> Right now, if i can believe bootchart that only works on any of my installs occasionally, it is at about 1.04 minutes.  Shut down takes at least as long if not longer.I still can't get Lucid booting properly with bootchart installed. I'm going to remove it and see if it is any better with just ureadahead and Plymouth. I have spent most of yesterday and today in Karmic because of it.

---

### Post by ranch hand on 2010-03-22
Bootchart also slows down your boot.  I prefer a clock.  I have a long timeout on grub (100 seconds) so I can easily watch a clock and hit enter at a good time.

I can't see that it is hurting anything but I think it is going to have to go because all it is good for, reliably, is irritating me.

If it is effecting plymouth, plymouth is worse than I thought.

I do hope that you keep us posted on the results of removing it from your system.

---

### Post by Stason on 2010-03-22
:popcorn: Wow! I have updated to beta1 and plymouth is now working! I could see it for the first time! Purple boot screen with some ugly font Ubuntu 10.04. Same on shutdown! :popcorn:


Seriously, is that how it supposed to be looking? How do I get that sunrise stuff instead?

BTW it's nVidia 7300GT on latest drivers.

---

### Post by ranch hand on 2010-03-22
> **Stason said:**
> :popcorn: Wow! I have updated to beta1 and plymouth is now working! I could see it for the first time! Purple boot screen with some ugly font Ubuntu 10.04. Same on shutdown! :popcorn:


Seriously, is that how it supposed to be looking? How do I get that sunrise stuff instead?

BTW it's nVidia 7300GT on latest drivers.
Follow the directions here;

[http://ubuntuforums.org/showthread.php?t=1381109](http://ubuntuforums.org/showthread.php?t=1381109)

---

### Post by cariboo on 2010-03-22
> **Stason said:**
> :popcorn: Wow! I have updated to beta1 and plymouth is now working! I could see it for the first time! Purple boot screen with some ugly font Ubuntu 10.04. Same on shutdown! :popcorn:


Seriously, is that how it supposed to be looking? How do I get that sunrise stuff instead?

BTW it's nVidia 7300GT on latest drivers.

If you are seeing **Ubuntu 10.04** at boot, plymouth is broken for you, try the nouveau driver. Trying one of the other themes won't work.

---

### Post by Stason on 2010-03-22
OK, I should have put <sarcasm> to my previous message. Of course the thing does not work. Using Nouveau would be screwing up the whole system for the sake of the start-up screen - would be too much sacrifice. 

I now get the Bug #537262 reported after booting up. It says it should be fixed by beta2. 

Well, I am going to wait until final and then press the purge button if that thing does not work. After all boot up time is very short these days.

Funny enough, but isn't Plymouth a mouth made of ply[wood]? Brrrr....

---

### Post by k3lt01 on 2010-03-22
Removed bootchart, but not pybootchartgui, and my laptop started with Lucid, BUT, it took more than half an hour to get to a usable stage. After that it booted ok each time and was under 1 minute.

I am about to reinstall bootchart, YES I know I'm an idiot, and remove pybootchartgui to see what happens. Hopefully in about an hour I'll be able to let you know what happens. If not I'll go back to Karmic and post from there.

---

### Post by k3lt01 on 2010-03-22
Well what an interesting little test that was. I did as I said above and everything went bad from there. I had about 15 minutes of Plymouth with NO hard drive activity at all. Reboot, get into Lucid, barely, I figured if I start Firefox it somehow slows the imminent crash. Don't ask me how cause I really don't know or understand it. I posted in the ureadahead thread and my laptop crashed. Restarted, got into synaptic, again barely, and removed bootchart, reboot, ureadahead reprofiled it took approximately 32 minutes. reboot and here I am typing with a nice laptop.

Now, bootchart and its little gui mate cause problems but ureadahead is still way to slow on reprofiling and the machine is pretty unusable until you reboot again. After that it's fine until the next ureadahead reprofile.

All in all I cannot get the info keybuk needs for Lucid, but I did get it for Karmic so I hope it is enough at the moment for him to work with. I hope someone else may be able to give him some more data samples to work with.

---

### Post by keybuk on 2010-03-22
> **cowlip1 said:**
> I keep these horrible images whenever I boot up or shut down, using the binary nVidia driver.

I'm going to try booting with that Framebuffer option now though.  Hopefully it will do the trick.

Known and deliberate ;-)

Boot-time console messages will be hidden before Beta 2

---

### Post by keybuk on 2010-03-22
> **Stason said:**
> :popcorn: Wow! I have updated to beta1 and plymouth is now working! I could see it for the first time! Purple boot screen with some ugly font Ubuntu 10.04. Same on shutdown! :popcorn:


Seriously, is that how it supposed to be looking? How do I get that sunrise stuff instead?

BTW it's nVidia 7300GT on latest drivers.

Yes, if you're using the binary drivers we don't have any way to provide high-color graphics for you during boot while also having a chance of suspend and resume working for you.

We do have a low-color splash solution in the wings for you, but we wanted to stress-test the ultimate fallback text version in Beta 1 instead.

So thanks for the testing! :-)

---

### Post by keybuk on 2010-03-22
> **cariboo907 said:**
> If you are seeing **Ubuntu 10.04** at boot, plymouth is broken for you, try the nouveau driver. Trying one of the other themes won't work.

Sorry but this is incorrect.

If you're seeing **Ubuntu 10.04** at boot, Plymouth is working perfectly for you; since it's Plymouth drawing that and animating the little dots below it.

Please don't spread this myth.

---

### Post by mcooke1 on 2010-03-22
> **keybuk said:**
> Sorry but this is incorrect.

If you're seeing **Ubuntu 10.04** at boot, Plymouth is working perfectly for you; since it's Plymouth drawing that and animating the little dots below it.

Please don't spread this myth.

Thank you for the clarification I saw the earlier post and thought I had a problem but I do not, my boot is as you discribe.

---

### Post by meborc on 2010-03-22
> **keybuk said:**
> Sorry but this is incorrect.

If you're seeing **Ubuntu 10.04** at boot, Plymouth is working perfectly for you; since it's Plymouth drawing that and animating the little dots below it.

Please don't spread this myth.

to me it looks like it is working as good as when it was drawing the nasty blue/white loading bars at the bottom of the screen, it is nowhere near what the boot looks with the nouveau driver

so my question is why to have that intermediate screen? why not just have plymouth when you are using drivers that support it fully and not have it / disable it when you don't

probably I am missing something, but will the boot with nvidia proprietary drivers ever look as nice as it is with nouveau? will it be ready for 10.04?

---

### Post by VMC on 2010-03-22
> **keybuk said:**
> Sorry but this is incorrect.

If you're seeing **Ubuntu 10.04** at boot, Plymouth is working perfectly for you; since it's Plymouth drawing that and animating the little dots below it.

Please don't spread this myth.

That may be a myth, but why did I once get the ***Ubuntu 10.04*** and from then on just ***Ubuntu*** only.

 I just did a fresh install from Mar21st and now only get ***Ubuntu***, and for the first time, it now works every time. It use to be hit and miss whether it would work at all.

 But I do not get ***Ubuntu 10.04***. I only saw that splash one time a while back.

---

### Post by mc4man on 2010-03-22
On a machine with 2 lucid installs and nvidia - 
The install using nouveau gets the ubuntu logo (5 lights
The install using nvidia-current gets the Ubuntu 10.04 (4 lights

Plymouth works fine on both, no issues, haven't yet tried changing the plymouth theme in the nvidia-current install

---

### Post by Uncle Spellbinder on 2010-03-22
On fresh install of Beta 1, I got Plymouth showing just ***Ubuntu***. Looked great with the new branding font. I was thrilled to see it finally working. After enabling restricted driver (nVidia), on reboot, Plymouth is still working. Except now I get ***Ubuntu 10.04*** in ugly block letters.

---

### Post by meborc on 2010-03-22
oh, i forgot to add that i also get plymouthd crash report every time I boot into gnome. i tick the "don't report this version crash blah-blah" but it still keeps reporting it to me on every boot

annoying

---

### Post by Uncle Spellbinder on 2010-03-22
> **meborc said:**
> oh, i forgot to add that i also get plymouthd crash report every time I boot into gnome. i tick the "don't report this version crash blah-blah" but it still keeps reporting it to me on every boot.
Same here. Been doing that since Alpha 3 in my case.

---

### Post by ChrisGaeth on 2010-03-22
I get the nice looking boot screen but my "Ubuntu" is off to the left.  On shutdown I have just a purple bar at the bottom.

---

### Post by cariboo on 2010-03-22
> **keybuk said:**
> Sorry but this is incorrect.

If you're seeing **Ubuntu 10.04** at boot, Plymouth is working perfectly for you; since it's Plymouth drawing that and animating the little dots below it.

Please don't spread this myth.

How come I get the proper Ubuntu logo on my netbook then?

---

### Post by uRock on 2010-03-22
> **cariboo907 said:**
> How come I get the proper Ubuntu logo on my netbook then?

Same here. Works perfectly on mine, too.

---

### Post by philinux on 2010-03-22
> **meborc said:**
> oh, i forgot to add that i also get plymouthd crash report every time I boot into gnome. i tick the "don't report this version crash blah-blah" but it still keeps reporting it to me on every boot

annoying

The devs are trying to fix this.

---

### Post by tad1073 on 2010-03-22
plymouth is still not working as it should with the latest nvidia drivers...

---

### Post by keybuk on 2010-03-22
> **tad1073 said:**
> plymouth is still not working as it should with the latest nvidia drivers...

Can you expand on this?

Assuming you are using the nVidia binary driver, Plymouth *should* work fine, displaying "Ubuntu 10.04" written in a standard VGA font on a Purple background.

---

### Post by mc4man on 2010-03-22
> Assuming you are using the nVidia binary driver, Plymouth *should* work fine, displaying "Ubuntu 10.04" written in a standard VGA font on a Purple background.

I think there is some expectation (or hope) that nvidia-current will have the same scheme as nouveau (and ability to change to the other avail. ones.

Whether or not it will (or can) I don't know - it was just recently nvidia-current didn't work at all..

( and the ship/install default will be nouveau which does work fine - at least on most hardware atm

---

### Post by ronacc on 2010-03-22
> **keybuk said:**
> Can you expand on this?

Assuming you are using the nVidia binary driver, Plymouth *should* work fine, displaying "Ubuntu 10.04" written in a standard VGA font on a Purple background.

using the driver that Nvidia shows as the current for my card (195.36.15 ) all I get during boot is a black screen with occasional blue and green squares flashing at random places and times on the screen until the login screen comes up . Strangely I DO get the purple screen with ubuntu 10.04 ( and a message about ureadahead not completing ) on SHUTDOWN . note! also get the plymouthd crash message when logged in .

---

### Post by NightwishFan on 2010-03-22
Currently my plymouth works, however it starts so late in the boot process. I am using the solar theme now even though I like the ubuntu one.

---

### Post by tad1073 on 2010-03-22
> **keybuk said:**
> Can you expand on this?

Assuming you are using the nVidia binary driver, Plymouth *should* work fine, displaying "Ubuntu 10.04" written in a standard VGA font on a Purple background.

the plymouth theme that is used with the nouveau driver is different from the one used with the nvidia driver, constancy is the the key here, it is no show stopper but the plymouth theme that is used with the nvidia driver is god awful.

---

### Post by cyberkilla on 2010-03-22
It's a shame the default theme is bright purple. If it was black, it would be much more theme agnostic. ATM, if you have a different GDM theme, or use KDM, it is a jarring jump from purple to air blue.

I honestly think they would be better served by putting the Plymouth boot logo on a black background.

---

### Post by ranch hand on 2010-03-22
At least is not digestive tract brown.  Black would be better (was).

---

### Post by tad1073 on 2010-03-22
I think it would be in the best interest if the ubuntu plymouth developers would brainstorm with fedora plymouth developers

---

### Post by ranch hand on 2010-03-22
I think the best idea is to drop it like the dog it is.

---

### Post by ronacc on 2010-03-22
I doubt there is much hope of that .We will just have to learn how to work around it like so many other things they've done lately .

---

### Post by Stason on 2010-03-22
> **keybuk said:**
> Yes, if you're using the binary drivers we don't have any way to provide high-color graphics for you during boot while also having a chance of suspend and resume working for you.

We do have a low-color splash solution in the wings for you, but we wanted to stress-test the ultimate fallback text version in Beta 1 instead.

So thanks for the testing! :-)

OK! I did not know it was important. A few comments then. Around every third reboot I cannot boot at all due to some filesystem mounting error. This does not happen on cold start only on reboots. When boot is successful sometimes I get some flicker even with the text version.

---

### Post by teh603 on 2010-03-22
> **ronacc said:**
> I doubt there is much hope of that .We will just have to learn how to work around it like so many other things they've done lately .I noticed that every try to get Plymouth removed gets soundly stomped down. I wish I knew what's really going on here.

---

### Post by ranch hand on 2010-03-22
Well, it is a bit late to be doing that in this cycle.  I think we are stuck with it for the next 3 years.  What a drag.

Maybe they will drop it after 10.04 and backport something better.

---

### Post by ronacc on 2010-03-22
actually with lucid my box is booting so quick that a boot splash would be kind of a waste even if it did work .

---

### Post by keybuk on 2010-03-22
> **mc4man said:**
> I think there is some expectation (or hope) that nvidia-current will have the same scheme as nouveau (and ability to change to the other avail. ones.

Whether or not it will (or can) I don't know - it was just recently nvidia-current didn't work at all..

Unfortunately the driver provided by nvidia doesn't provide any mechanism for us to draw to it in anything other than VGA or VESA standard modes.

VESA has its own problem that it tends to break suspend and resume, so good old 16-color VGA it is.

(You can enable vesa easily enough by adding video=vesafb or vga=... to your kernel command-line)

---

### Post by keybuk on 2010-03-22
> **teh603 said:**
> I noticed that every try to get Plymouth removed gets soundly stomped down. I wish I knew what's really going on here.

Because you haven't suggested anything to replace it with.

usplash doesn't work correctly with in-kernel graphics drivers, and doesn't provide the mechanism to queue questions or password requests.

---

### Post by keybuk on 2010-03-22
> **tad1073 said:**
> I think it would be in the best interest if the ubuntu plymouth developers would brainstorm with fedora plymouth developers

I talk to them just about every day.

---

### Post by mc4man on 2010-03-22
> Unfortunately the driver provided by nvidia doesn't provide any mechanism for us to draw to it in anything other than VGA or VESA standard modes.


Personally that's fine by me, I just thought possibly several posters were 'confused' by the 2 different ubuntu logo screens,  - what's available w/ nouveau and what is used w/ nvidia-current.

 Here nvidia-current is without any issue, nouveau has some minor stuff but not in terms of plymouth (as far as what's seen during the boot up

---

### Post by rtalcott on 2010-03-22
fwiw working fine on 4 machines...2 nvidia-current and two ati...
rt

---

### Post by tad1073 on 2010-03-22
> **ranch hand said:**
> I think the best idea is to drop it like the dog it is.

+1

> **ronacc said:**
> actually with lucid my box is booting so quick that a boot splash would be kind of a waste even if it did work .

same here, I remove "quiet" from the kernel option to see the output, now If I could just get the resolution to 1024x768 I would be happy

> **keybuk said:**
> I talk to them just about every day.

funny thing is, if I use vga=795 w/nvida drivers under fedora 12 I get the correct plymouth theme

if vga=795 is not added, I get the blue and white progress bar at the bottom the screen

---

### Post by ranch hand on 2010-03-22
If I remove plymouth from this install it will boot in less than 40  seconds.  I decided to reinstall it.  After 5 reboots this is what I get.  The desktop name is shortened from Horny Horse which, as everyone should know is what 8.04 is called.  This is an 8.04.4 to 10.04 upgrade.

---

### Post by ranch hand on 2010-03-22
> **keybuk said:**
> Because you haven't suggested anything to replace it with.

usplash doesn't work correctly with in-kernel graphics drivers, and doesn't provide the mechanism to queue questions or password requests.
From my post above you may get the idea why I don't think it needs replaced.  All I removed was plymouth, no purge.  Worked great the only problem was mountall, of coarse, could not connect with plymouth.

I assumed that it was a congratual message like "Hey now your computer will boot in less than a day".

You mention usplash in your post.  I certainly do not think it was up to much.

What about xsplash?

---

### Post by k3lt01 on 2010-03-22
> **ranch hand said:**
> I assumed that it was a congratual message like "Hey now your computer will boot in less than a day".Your more sarcastic than I am, and that's saying something :popcorn:

---

### Post by emarkay on 2010-03-22
> **keybuk said:**
> Because you haven't suggested anything to replace it with.
usplash doesn't work correctly with in-kernel graphics drivers, and doesn't provide the mechanism to queue questions or password requests.

Please elaborate:
1. Usplash is a few second "pretty" on boot - who cares.

2. Queue questions?  Where do we ask questions during boot?

3. Password Requests - The Alpha's allowed me to log in fine without Plymouth - what's changed in Beta; other's who have removed it here seem to be able to log in too.

I am **seriously** thinking of removing this again - especially now that there's an ATI issue, too.
Give me a legit reason why I shouldn't - from a user standpoint.

---

### Post by k3lt01 on 2010-03-22
> **emarkay said:**
> Give me a legit reason why I shouldn't - from a user standpoint.Just do it, test your theory and stop demanding other people give you something to make you feel comfortable in your decision. Live dangerously for a minute.

---

### Post by emarkay on 2010-03-22
> **k3lt01 said:**
> Just do it, test your theory and stop demanding other people give you something to make you feel comfortable in your decision. Live dangerously for a minute.

Demanding?  I was just asking a question from someone more intelligent than I.

A real scientist gathers complete data before examining a theory; especially when lives, time or sanity may be at stake.

Now play nice, will ya?   :)

---

### Post by ranch hand on 2010-03-22
I have switched to my night OS - Jumpin Jackass (9.04).  I realize that the bootchart here need some conversion to really compare the 2 but I thought I would post it as the bootchart in 2 OS' in a row actually worked.  I do not care what you want to add to this.  It will not add up to what 10.04 is giving me.

This is on 9.04 with nothing modified to speed boot just as nothing has been done to any of my 10.04 installs to speed boot.

EDIT
All my installs are on the same box.  This is an internal drive.  10.04 is on a USB enclosure.

---

### Post by ronacc on 2010-03-22
@ Ranch Hand  I hope that boot time is off of your external USB drive , I thought mine was long back when it was taking 53 sec :lolflag:

---

### Post by k3lt01 on 2010-03-22
> **emarkay said:**
> Now play nice, will ya?   :)Oh sorry I mustn't have seen the "Please give me an answer" just like I didn't see the "Please play nice" ;)

---

### Post by ronacc on 2010-03-22
> **emarkay said:**
> Demanding?  
A real scientist gathers complete data before examining a theory; especially when lives, time or sanity may be at stake.


If you are looking for sanity you are in the wrong place .

---

### Post by ranch hand on 2010-03-22
> **ronacc said:**
> @ Ranch Hand  I hope that boot time is off of your external USB drive , I thought mine was long back when it was taking 53 sec :lolflag:
I just posted another from an internal running 9.04.  The external will boot on the version of bootchart with 10.04 in less than 40 seconds without plymouth installed.

I am getting a little bit tired of plymouth and hearing about how great it is.

The last post is 9.04.  Running usplash and readahead.

---

### Post by ronacc on 2010-03-22
I removed plymouth way back ,then reinstalled it to test supposed fixes , now its gone again .

---

### Post by tad1073 on 2010-03-22
> **ronacc said:**
> I removed plymouth way back ,then reinstalled it to test supposed fixes , now its gone again .

+1

did the same thing here...

---

### Post by ElSlunko on 2010-03-22
Kinda unrelated but the thing I liked about xsplash was using the script to automagically change it to my desktop background. I know first impressions & the booting experience is meant to be increased by plymouth but xsplash wasn't so bad.

---

### Post by ranch hand on 2010-03-23
> **ElSlunko said:**
> Kinda unrelated but the thing I liked about xsplash was using the script to automagically change it to my desktop background. I know first impressions & the booting experience is meant to be increased by plymouth but xsplash wasn't so bad.
Xslpash is really the only thing I really like about 9.10.  I like the ability to go, pretty smoothly, from grub menu background to xsplash/gdm to wallpaper.

If you want a great first impression that is hard to beat.

I even had that working in plymouth but now it is improved so that it is a bugger.  I guess all you need to do is write a new theme every time you change your wallpaper for a few seconds (if they ever get the speed back) of splash.

I have what is called an attention span.  That black screen does not bother me a bit.  Watching plymouth struggle to get anywhere is painfull.

I can boot (slowly) so, except for that one OS, I will leave that crap on my installs for the remainder of testing.  5 weeks will not kill me but after that it is off my box like dirty socks.

---

### Post by vishalrao on 2010-03-23
> **keybuk said:**
> Assuming you are using the nVidia binary driver, Plymouth *should* work fine, displaying "Ubuntu 10.04" written in a standard VGA font on a Purple background.

If I switch from nouveau to the binary driver can I not enable framebuffer renderer for plymouth (by setting gfxpayload in grub2) to draw the pretty graphics during boot before X shows up? (not that i plan to move away from nouveau now)...

---

### Post by vishalrao on 2010-03-23
> **ranch hand said:**
> I am getting a little bit tired of plymouth and hearing about how great it is.

One more time from me :lolflag:

Yes plymouth is like a dog but rather than being dropped it should be played with coz it gives you back that unconditional love...

I have a blast mucking about with the script theme because its so easy - makes my boring/stable lucid installations more fun to use...

---

### Post by ranch hand on 2010-03-23
Every time I have played with it lately all it does is die.

---

### Post by meborc on 2010-03-23
switched to vga=795 with proprietary nvidia driver... much better :) 

I really don't care about suspend/hibernate as it has always been slower for me than simple rebooting 

I now get the nicer ubuntu logo and the dots, but it still has a annoying purple background and it is a bit less polished than the nouveau one... still better than the vesa text though

the crash report is also gone now... weeeee

---

### Post by tad1073 on 2010-03-23
> **meborc said:**
> switched to vga=795 with proprietary nvidia driver... much better :) 

I really don't care about suspend/hibernate as it has always been slower for me than simple rebooting 

I now get the nicer ubuntu logo and the dots, but it still has a annoying purple background and it is a bit less polished than the nouveau one... still better than the vesa text though

the crash report is also gone now... weeeee

thanks for the tip!!!

I added

set gfxpayload=keep
to 

/etc/grub.d/00_header
and all is good

---

### Post by recluce on 2010-03-23
> **keybuk said:**
> Can you expand on this?

Assuming you are using the nVidia binary driver, Plymouth *should* work fine, displaying "Ubuntu 10.04" written in a standard VGA font on a Purple background.

I get the "Ubuntu 10.04" for less than 5 seconds, before the login screen appears. Text output (fsck messages and so forth) before that.

If displaying a nasty ascii screen for 5 seconds is considered "working fine", then just get us usplash or xsplash back. I guess I will just remove plymouth after the beta test phase.

---

### Post by kansasnoob on 2010-03-23
I have "auto-login" enabled, and with Plymouth installed my boot time from the moment I hit enter at the grub menu until Desktop is about 32 seconds.

If I remove Plymouth that decreases to about 23 seconds. Either way it's reasonably quick, but I also notice it takes about 15 to 20 seconds after the Desktop appears for things to actually become "usable".

That is I can click on something and nothing happens until I've waited an additional 15 to 20 seconds. All in all Jaunty still out performs Lucid hands down.

---

### Post by vishalrao on 2010-03-23
> **tad1073 said:**
> thanks for the tip!!!

I added

set gfxpayload=keep
to 

/etc/grub.d/00_header
and all is good

The cleaner/recommended way is probably to add

```

GRUB_GFXPAYLOAD_LINUX=keep

```

in /etc/default/grub under the GRUB_GFXMODE line and all should be good :)

(assuming you have set GRUB_GFXMODE and you want the plymouth resolution to be the same as the grub boot menu one - i have them both at 1024x768 for simplicity)

---

### Post by teh603 on 2010-03-23
> **keybuk said:**
> Because you haven't suggested anything to replace it with.

usplash doesn't work correctly with in-kernel graphics drivers, and doesn't provide the mechanism to queue questions or password requests.Now somebody tells me. Wonderful.

The trouble we've got here is that I don't know what bootsplashes there are out there, mainly because I'm not a programmer. If there was a list or comparison out there, it could help.

---

### Post by Stason on 2010-03-23
Correct me if I am wrong, but (and this might be true for 60% to 80% of Ubuntu users, since they also use nVidia GPU) aren't our options now limited to:

1) using nvidia driver and purging plymouth + come to terms with some boot up error messages (aka plymouth not connecting)

2) using nouveau for the sake of getting smooth boot up experience, but facing all sorts of graphical issues with media players, 3D and pretty much everywhere in the graphical part of the system

---

### Post by mc4man on 2010-03-23
> 1) using nvidia driver and purging plymouth + come to terms with some boot up error messages (aka plymouth not connecting)

nvidia-current and plymouth work fine here with 3 different nvidia adapters, no issues, no errors
Maybe some models have problems, best to try for yourself with your hardware


> 2) using nouveau for the sake of getting smooth boot up experience, but facing all sorts of graphical issues with media players, 3D and pretty much everywhere in the graphical part of the system

No 3d by default, some *very minor* graphical issues, media players work fine.
Possible that video tearing may happen, though haven't noticed any yet, will have to run some test clips I have that tend to expose (tearing is non-existent with nvidia-current

Again try with your hardware rather than just relying on what people post here...

---

### Post by keybuk on 2010-03-23
> **tad1073 said:**
> funny thing is, if I use vga=795 w/nvida drivers under fedora 12 I get the correct plymouth theme

That should be the same on Ubuntu, provided your initramfs has framebuffer support.  Adding vga=795 will force the loading of the vesafb driver, and set the resolution.

You may need to enable this though, best way:

  echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
  sudo update-initramfs -u

  sudo sed -i "/splash/s/splash/splash vga=795/" /etc/default/grub
  sudo update-grub

---

### Post by keybuk on 2010-03-23
> **emarkay said:**
> I am **seriously** thinking of removing this again - especially now that there's an ATI issue, too.
Give me a legit reason why I shouldn't - from a user standpoint.

You're free to break your computer however you want ;-)

Just don't come crying to me when you have a filesystem error, and the boot sequence doesn't tell you anything about it because you removed Plymouth.

---

### Post by keybuk on 2010-03-23
> **ranch hand said:**
> If I remove plymouth from this install it will boot in less than 40  seconds.  I decided to reinstall it.  After 5 reboots this is what I get.  The desktop name is shortened from Horny Horse which, as everyone should know is what 8.04 is called.  This is an 8.04.4 to 10.04 upgrade.

You appear to have cropped the most important part of the chart.

---

### Post by ranch hand on 2010-03-23
> **keybuk said:**
> You appear to have cropped the most important part of the chart.
I will be over there later today and send the whole thing if you want it.  It is not the primary 10.04 that I use.  It is one that bootchart seems to work on.

---

### Post by tad1073 on 2010-03-23
> **vishalrao said:**
> The cleaner/recommended way is probably to add

```

GRUB_GFXPAYLOAD_LINUX=keep

```in /etc/default/grub under the GRUB_GFXMODE line and all should be good :)

(assuming you have set GRUB_GFXMODE and you want the plymouth resolution to be the same as the grub boot menu one - i have them both at 1024x768 for simplicity)

> **keybuk said:**
> That should be the same on Ubuntu, provided your initramfs has framebuffer support.  Adding vga=795 will force the loading of the vesafb driver, and set the resolution.

You may need to enable this though, best way:

  echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
  sudo update-initramfs -u

  sudo sed -i "/splash/s/splash/splash vga=795/" /etc/default/grub
  sudo update-grub

@keybuck, will what you have showed me conflict with what vishalrao posted about the issue?

---

### Post by autumnraine on 2010-03-23
Seems to work fine for me now, and doesn't interfere with screen rotation. That's all I ask :)

---

### Post by kansasnoob on 2010-03-23
Anyone care to take a look at this silly thing now:

[ATTACH]151156[/ATTACH]

Back up to 44.65 seconds :o

One thing that looks odd to me is the kernel boot line ending in "ro splash quiet quiet splash". Why the repetition?

Another thing I might add is that I've never been able to change themes on this bugger.

---

### Post by ranch hand on 2010-03-23
Too small, can't be read.

That is a weird instruction string.

---

### Post by Uncle Spellbinder on 2010-03-23
> **ranch hand said:**
> Too small, can't be read.

That is a weird instruction string.

Ditto. Anytime anyone posts the bootchart images, they are ALWAYS unreadable. No clue why they post them in the first place.

---

### Post by kansasnoob on 2010-03-23
> **ranch hand said:**
> Too small, can't be read.

That is a weird instruction string.

That's why I included the tar.gz, you can just save it to your desktop (or wherever) and open it such that you can use your magnifying tools.

I just tried logging into a nearly virgin install and it puked with "nuking init". Guess it ain't my day :)

---

### Post by keybuk on 2010-03-23
> **tad1073 said:**
> @keybuck, will what you have showed me conflict with what vishalrao posted about the issue?

Both methods of setting up a video mode are equally cromulent.

---

### Post by keybuk on 2010-03-23
> **kansasnoob said:**
> Anyone care to take a look at this silly thing now:

[ATTACH]151156[/ATTACH]

Back up to 44.65 seconds :o

One thing that looks odd to me is the kernel boot line ending in "ro splash quiet quiet splash". Why the repetition?

Another thing I might add is that I've never been able to change themes on this bugger.

Filesystem check by the looks of it

---

### Post by kansasnoob on 2010-03-23
Well here's one from that other virgin install, same machine, this is second reboot after the new kernel upgrade (the first was over a minute):

[ATTACH]151166[/ATTACH]

Just over 40 seconds, nicer looking device string. (Don't know why the other one would be different).

Keybuk, is there any reason I'd be getting a longer fsck now?

I do mount more partitions than the average camper:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb3 during installation
UUID=33f6c50e-4665-4f7c-8f20-fa4cb8f0bb73 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb12 during installation
UUID=7b6e32f0-70bb-4450-8b66-425164d36a99 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=58aec1b2-6dfe-4f02-b77d-207fe6cc5551 none            swap    sw              0       0
# swap was on /dev/sdb11 during installation
UUID=bc99fdc7-0dd8-40e7-8567-f0882352d256 none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#/dev/sda6    /mnt/sda6 /home/lance/Documents
UUID=571cfad8-68c7-4703-883e-c0baa2a381d4 /mnt/sda6       ext3    defaults          0       2
#/dev/sda7    /mnt/sda7 /home/lance/Downloads
UUID=05289ee4-d681-4806-b6fd-aefd784f9323 /mnt/sda7       ext3    defaults          0       2
#/dev/sda8    /mnt/sda8 /home/lance/Pictures
UUID=8a3f6c83-cb52-4caf-96b8-5faf2c830453 /mnt/sda8      ext3    defaults          0       2
#/dev/sda9    /mnt/sda9 /home/lance/Backups
UUID=594c3d40-2791-4c0a-8644-d9812545da2d /mnt/sda9      ext3    defaults          0       2

```

---

### Post by ratcheer on 2010-03-23
As of this minute (I don't know what the future will bring), Lucid and plymouth are working perfectly, for me. For the first time, ever. It boots very fast, with no disk drive clicking / resetting.

What changed? aptitude picked up the new 2.6.32-17 kernel and whatever all came with it. I had just updated an hour or so before, so this was a very new change.

Kudos to all involved on these latest changes. I just hope it lasts.

Tim

---

### Post by kansasnoob on 2010-03-23
Jaunty bootchart same machine, mounting the same data partitions (less than 33 seconds):

[ATTACH]151182[/ATTACH]

Does that qualify as regression?

FYI I use the openchrome drivers w/P4M800 gpu.

---

### Post by yoasif on 2010-03-23
Plymouth is now broken for me with the latest update to -17. On the first boot, I get the text splash, which I had never gotten before (was getting the graphical one).

On subsequent boots, I don't get a splash at all, and I cannot switch to any consoles, and Xorg doesnt work.

---

### Post by keybuk on 2010-03-23
> **kansasnoob said:**
> Jaunty bootchart same machine, mounting the same data partitions (less than 33 seconds):

[ATTACH]151182[/ATTACH]

Does that qualify as regression?

FYI I use the openchrome drivers w/P4M800 gpu.

This doesn't cover the full boot!  Your jaunty bootchart only covers the bit up to the login screen, where as the lucid bootchart also covers the desktop login period.

For comparison, the bit of the lucid bootchart that matches the jaunty one (modulo ureadahead reading desktop files too) is somewhere not more than 20s

---

### Post by keybuk on 2010-03-23
> **yoasif said:**
> Plymouth is now broken for me with the latest update to -17. On the first boot, I get the text splash, which I had never gotten before (was getting the graphical one).

On subsequent boots, I don't get a splash at all, and I cannot switch to any consoles, and Xorg doesnt work.

Without more details, this doesn't sound like a Plymouth issue - since then you would be able to see the splash screen!

---

### Post by lidex on 2010-03-23
After today's updates -> 19.23 sec. Can that be right or am I reading it wrong?

---

### Post by VMC on 2010-03-23
> **lidex said:**
> After today's updates -> 19.23 sec. Can that be right or am I reading it wrong?

That could be right. I'm getting the fastest boot ever, from grub to desktop in 23 seconds. I have a P4, 2.6gHz, SATA HD, 2 gig ram.

You obviously have a more powerful cpu.

---

### Post by ranch hand on 2010-03-23
> **keybuk said:**
> You appear to have cropped the most important part of the chart.
I am sorry but bootchart can't be read today.  pybootchartgui appears t onot be able to read any but the first tgz file that was generated back when this install was still 8.04 with a boot time of 49 seconds.

I realize that this is not the same bootchart but it is still faster than the piss poor performance I am betting with plymouth installed.

I should have learned by now that boot chart is just not reliable and saved the image instead of the cropped image.

If the tgz is of any use to you it is readable by the archive manager.

---

### Post by kansasnoob on 2010-03-23
> **keybuk said:**
> This doesn't cover the full boot!  Your jaunty bootchart only covers the bit up to the login screen, where as the lucid bootchart also covers the desktop login period.

For comparison, the bit of the lucid bootchart that matches the jaunty one (modulo ureadahead reading desktop files too) is somewhere not more than 20s

Well, I only know that my boot changed for the worse. I get several seconds of black screen with 6 fsck messages, a few seconds of Purple "splash" cluttered with more messages, and then a Desktop that's unresponsive for another 15 seconds or so.

I'm only bringing this up because I want this to be a really great Ubuntu experience for everyone. I'm a fairly reliable iso tester (name there is Lance), and I try to report bugs properly (name there is Erick Brunzell).

I'm honestly not just whining. It just seems that things are going downhill! And I'm unsure how I'd even file a bug on this.

I do actually get to a "usable" Jaunty Desktop at least 30 seconds sooner than I do to a "usable" Lucid Desktop at this point.

---

### Post by ranch hand on 2010-03-23
I have too installs of the same name and checked the other one.  Same performance but bootchart is working so I have the image from the same day.  Plymouth was never removed and reinstalled on this installation.

---

### Post by ranch hand on 2010-03-23
> **kansasnoob said:**
> Well, I only know that my boot changed for the worse. I get several seconds of black screen with 6 fsck messages, a few seconds of Purple "splash" cluttered with more messages, and then a Desktop that's unresponsive for another 15 seconds or so.

I'm only bringing this up because I want this to be a really great Ubuntu experience for everyone. I'm a fairly reliable iso tester (name there is Lance), and I try to report bugs properly (name there is Erick Brunzell).

I'm honestly not just whining. It just seems that things are going downhill! And I'm unsure how I'd even file a bug on this.

I do actually get to a "usable" Jaunty Desktop at least 30 seconds sooner than I do to a "usable" Lucid Desktop at this point.
At least that much. I would say after timing the two with a clock that, for me, it is 53 seconds.

---

### Post by kansasnoob on 2010-03-23
> **ranch hand said:**
> I have too installs of the same name and checked the other one.  Same performance but bootchart is working so I have the image from the same day.  Plymouth was never removed and reinstalled on this installation.

Holy cow! Nearly two minutes!

---

### Post by kansasnoob on 2010-03-23
> **ranch hand said:**
> At least that much. I would say after timing the two with a clock that, for me, it is 53 seconds.

Some of it's hard to time.

As I said, once I'm in Jaunty it's active! I can go to work (or play).

Once I hit a "full" Lucid Desktop I can click away but to no avail!!!!! --- for as much as 15 seconds :eek:

And it has regressed big time in the past few days!

---

### Post by kansasnoob on 2010-03-23
I should also say that I don't care a lot about boot times. My computer stays on for days and weeks at a time.

But things should just work! A reboot shouldn't be painful!!!!!!!!!!!!!!!!!

---

### Post by ranch hand on 2010-03-23
> **kansasnoob said:**
> I should also say that I don't care a lot about boot times. My computer stays on for days and weeks at a time.

But things should just work! A reboot shouldn't be painful!!!!!!!!!!!!!!!!!
Would that be painfully purple?

Once  I get to the desktop 10.04 is actually quite a bit faster to be ready than 9.04.

---

### Post by garvinrick4 on 2010-03-24
Every other day or so I install plymouth and give it a go. With plymouth installed
a beautiful purple ubuntu and logo but know drive activity and of course no boot.
Go into karmic install and mount and chroot into lucid and remove plymouth and lucid
boots without splash. All else in good order in Lucid. Will keep doing daily's until 
one day a get a pure boot with plymouth installed.

---

### Post by DanaG on 2010-03-24
Heh, anyone here remember the old bootsplash, when it advanced from left to right when booting up, and receded from left to right when shutting down?

Well, the new boot splash looks like it's starting up and shutting down, over and over.  
If you think of red as full and white as empty, then the "progress bar" seems to be looping from 0% to 100% and back again. =þ
Make up your mind already... are you starting up, or shutting down?   

what we have now (think of dot as white, and asterisk as red):
```

..... -- empty
*....
**...
***..
****.
***** -- full

***** -- full (not really shown twice)
.****
..***
...**
....*
..... -- empty (not really shown twice)
```In my opinion, the animation should be "scrolling", not filling and emptying over and over.

This could be achieved by tweaking the dot behavior:
```

..... -- start
*....
**...
***.. -- loop start
.***.
..***
*..**
**..*
***.. -- goes to loop start
```It could also look good with 6 dots, instead of the 5 I believe it has.
[SIZE=1]
(Oh, and for some reason, the forum puts two extra newline characters at the end of every code tag.)[/SIZE]

---

### Post by kansasnoob on 2010-03-24
I see the following bug has gone to Fix Committed so we may see Fix Released soon :D

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/526892)

---

### Post by ShadowDragon on 2010-03-24
> **DanaG said:**
> Heh, anyone here remember the old bootsplash, when it advanced from left to right when booting up, and receded from left to right when shutting down?

Well, the new boot splash looks like it's starting up and shutting down, over and over.  
If you think of red as full and white as empty, then the "progress bar" seems to be looping from 0% to 100% and back again. =þ
Make up your mind already... are you starting up, or shutting down?   

what we have now (think of dot as white, and asterisk as red):
```

..... -- empty
*....
**...
***..
****.
***** -- full

***** -- full (not really shown twice)
.****
..***
...**
....*
..... -- empty (not really shown twice)
```In my opinion, the animation should be "scrolling", not filling and emptying over and over.

This could be achieved by tweaking the dot behavior:
```

..... -- start
*....
**...
***.. -- loop start
.***.
..***
*..**
**..*
***.. -- goes to loop start
```It could also look good with 6 dots, instead of the 5 I believe it has.
Dude, that requires even more redrawing and wasted processing power... Plymouth is already such a pain... :p

---

### Post by Trespasser on 2010-03-24
I don't know about you but plymouthd has stopped crashing on me. No crash reports in /var/crash...nothing. This is on a Lenovo G530 with an Intel graphics card and Broadcom bcm4312 rev 9 wireless card.

My crashes were related to this bug...

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262?comments=all](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/537262?comments=all)

Nice to be free of that problem.

Later...

---

### Post by Didius Falco on 2010-03-24
Plymouth itself is running well. Where I'm having a problem now is that it refuses to run fsck.

I have a total of 6 Ubuntu installs, (8.10, 9.10 and 4 clones of the 9.10 install, all set up for future releases) with all of them mounting at boot in every install. In addition, I have an ext3 Data partition that I'm using as a catch-all for downloads and files I created myself.

I I just booted into the version of 8.10 I keep installed as the base of my (legacy) grub system, and was informed that that partition had been mounted 110 (!!!) times without a file system check.

fsck has only run one time since the alpha install, and that one time it quit at 71%. This has me concerned...

---

### Post by pathos_84 on 2010-03-25
FWIW, I lost the graphical boot splash after a recent update to 2.6.32-17-generic. Turns out, update-initramfs was failing because I had /tmp mounted noexec in RAM. Disabling it and then running update-initramfs again resolved the issue.

---

### Post by makro on 2010-03-25
Upgraded to beta 1 from karmic.
No graphics during boot 'till checkdisks.
Ok during shutdown

I've Intel graphic chipset.

Any Idea?

---

### Post by bk109 on 2010-03-25
Hmm, i seem to be jumping on the bandwaggon here, but anyone else experiencing the sudden loss of the Graphical splash after switching to the proprietary(AMD in my case) drivers,or it's just a coincidence i lost it when I activated fglrx?

---

### Post by kurros on 2010-03-25
> **makro said:**
> Upgraded to beta 1 from karmic.
No graphics during boot 'till checkdisks.
Ok during shutdown

I've Intel graphic chipset.

Any Idea?

This makes everything work great on my Intel 4 series graphics:

[I]
sudo -s 
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u[/I]

---

### Post by makro on 2010-03-25
> **kurros said:**
> This makes everything work great on my Intel 4 series graphics:

[I]
sudo -s 
echo FRAMEBUFFER=y >>/etc/initramfs-tools/conf.d/splash
update-initramfs -u[/I]

BINGO!
Thank you very much kurros!!

---

### Post by garvinrick4 on 2010-03-25
Seem to get new one for me today. Nice purple splash with dots below going thru their lights  sequence one after another and below that a (failed to mount 0 [Sm] ). Still no boot with plymouth but today the new message.  The (failed to mount 0 [SM] ).


Just cannot seem to get the root file system to boot. Looks pretty though. If no idea's will remove plymouth to boot and wait for more upgrades.

Display controller              product: Mobile 4 Series Chipset Integrated Graphics Controller              vendor: Intel Corporation

---

### Post by Trespasser on 2010-03-25
> **garvinrick4 said:**
> 
Display controller              product: Mobile 4 Series Chipset Integrated Graphics Controller              vendor: Intel Corporation

That's the same chipset I'm running but I'm not having that problem. Actually, I'm not having any problems at all right now.

Good luck to you, though.

Later...

---

### Post by RomeReactor on 2010-03-25
> **bk109 said:**
> Hmm, i seem to be jumping on the bandwaggon here, but anyone else experiencing the sudden loss of the Graphical splash after switching to the proprietary(AMD in my case) drivers,or it's just a coincidence i lost it when I activated fglrx?

Not sure if this is exactly what you're referring to, but as far as I know, fglrx doesn't support kms; no kms, no plymouth.

---

### Post by amano on 2010-03-25
KMS --> KMS Plymouth
No KMS --> Plymouth fallbacks (VGA, VESA, Text)

---

### Post by kawaji on 2010-03-26
I have updated plymouth to 0.8.1-1, 'plymouth-set-default-theme' command gone away from my system...:confused:

---

### Post by Nickedynick on 2010-03-26
Just updated too - looks like I'm getting a very quick boot (17s, awesome for my setup) but the boot/shutdown logo has reverted to the Karmic style :(

---

### Post by kansasnoob on 2010-03-26
Looks the best it ever has here, but a bit over 43 seconds. hardly anything to brag about.

---

### Post by Uncle Spellbinder on 2010-03-26
> **kansasnoob said:**
> Looks the best it ever has here, but a bit over 43 seconds. hardly anything to brag about.
Indeed it looks great. Working rather well with my nVidia 9800GT.  As far as booting goes, It couldn't be much quicker. Grub to desktop less than 10 seconds every time.

---

### Post by zob on 2010-03-26
Very strange things happening to my computer after the plymouth update tonight. Not able to shutdown from the dialogbox following shutdown from the menu. (well, not able to is not exactly right, it just took a hard fight and a lot of CTRL+ALT+Del's).

I will see to it tommorow though.

I have a NVIDIA 7800GS and I'm using propietary drivers.

---

### Post by lidex on 2010-03-26
> **Nickedynick said:**
> Just updated too - looks like I'm getting a very quick boot (17s, awesome for my setup) but the boot/shutdown logo has reverted to the Karmic style :(

Yeah, I have generic logo also. What happened there?

---

### Post by seenthelite on 2010-03-26
Whats happening with Plymouth with 34 days to go ? 15 seconds to boot here.

---

### Post by hourna on 2010-03-26
i think my boot time has increased a little. but it does not show the ugly ubuntu text anymore. now it is old ubuntu logo.

---

### Post by ranch hand on 2010-03-26
Well, I am on wone of my "throw away" OS' chrooted into my Production OS doing the update to it.

My boot speed has improved tremendously.  Plymouth doesn't seem to work at all.  Hats off to the devs.

I really think they are getting close to the solution to this problem.

I am getting a lot of errors on shut down (judging by the other throw away but shut down is about 1/3 what it was when plymouth worked.

---

### Post by mc4man on 2010-03-26
I *believe* it goes something like this now for what theme is used (they need to be installed  first - 

> doug@doug-desktop:~$ sudo update-alternatives --config default.plymouth
There are 6 choices for the alternative default.plymouth (providing /lib/plymouth/themes/default.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       auto mode
  1            /lib/plymouth/themes/fade-in/fade-in.plymouth           10        manual mode
  2            /lib/plymouth/themes/glow/glow.plymouth                 10        manual mode
  3            /lib/plymouth/themes/script/script.plymouth             10        manual mode
  4            /lib/plymouth/themes/solar/solar.plymouth               10        manual mode
  5            /lib/plymouth/themes/spinfinity/spinfinity.plymouth     10        manual mode
  6            /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth   100       manual mode

Press enter to keep the current choice[*], or type selection number: 
 

And there are also these ..?
> doug@doug-desktop:~$ sudo update-alternatives --config text.plymouth
There are 2 choices for the alternative text.plymouth (providing /lib/plymouth/themes/text.plymouth).

  Selection    Path                                                   Priority   Status
------------------------------------------------------------
* 0            /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth   50        auto mode
  1            /lib/plymouth/themes/text/text.plymouth                 10        manual mode
  2            /lib/plymouth/themes/ubuntu-text/ubuntu-text.plymouth   50        manual mode


---

### Post by vishalrao on 2010-03-26
Must be something to do with the latest update having gotten latest upstream so the files/locations must be broken (/lib vs /usr/share whatever)... :)

I saw this during my update:

```

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-17-generic
/usr/share/initramfs-tools/hooks/plymouth: 39: /usr/sbin/plymouth-set-default-theme: not found
cp: cannot stat `/lib/plymouth/themes/default.plymouth': No such file or directory
grep: /lib/plymouth/themes//.plymouth: No such file or directory

```

---

### Post by vishalrao on 2010-03-26
OK I am trying the following:

* reinstall the ubuntu-logo and text theme packages (called plymouth-theme-ubuntu-logo and plymouth-theme-text i believe)
* re-link default.plymouth and text.plymouth to my customised plymouth theme and the fallback text theme in /lib/plymouth/theme
* rerun sudo update-initramfs -u (but that says plymouth-set-default-theme not found).

will reboot and report back...

---

### Post by vishalrao on 2010-03-26
(apologies for multiple posting)

It works though plymouth shows up pretty late to the party... :)

dmesg shows nouveau initialising quite fast (2 - 2.5 second marks) though there a few logs after 18 sec like "allocating FIFO" and my spinning theme shows up about 20 seconds into boot and GDM login shows up 25 seconds after GRUB...

Boot time (GRUB to login screen) is the same for me (abotu 25 sec)...

I'm sure the devs will fix it up real fast when they get back in to the office on Monday - unless there are a few crazy ones who work on weekends :D

---

### Post by VMC on 2010-03-26
> **mc4man said:**
> I *believe* it goes something like this now for what theme is used (they need to be installed  first - 



And there are also these ..?

I get this error, but my plymouth works.

> $ sudo update-alternatives --config default.plymouth
update-alternatives: error: no alternatives for default.plymouth.
and this one
> $ sudo update-alternatives --config text.plymouth
update-alternatives: error: no alternatives for text.plymouth.

I have an Intel i865 video chip.

---

### Post by mc4man on 2010-03-27
> I get this error, but my plymouth works.

> .....for what theme is used (*they need to be installed first*

Look in synaptic under plymouth

---

### Post by sgosnell on 2010-03-27
I get the same - no alternatives for either default or text.  It works, though.

---

### Post by mc4man on 2010-03-27
As an aside - if you ever want to see what may be available thru alt.'s and the terminolgy to config or whatever than run this

```
sudo update-alternatives --get-selections
```

Noting that normally there is very little need to change - but very useful or necessary sometimes.

( it would be a great thing (at least here) if browser plugins were avail. thru alt's..

---

### Post by kawaji on 2010-03-27
> **vishalrao said:**
> 
I'm sure the devs will fix it up real fast when they get back in to the office on Monday - unless there are a few crazy ones who work on weekends :D

Already fixed. :D
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/549247/comments/3]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/549247/comments/3")

Thanks vishalrao & mc4man, the following commands worked to change default theme.
```
sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/mytheme/mytheme.plymouth 100
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

---

### Post by vishalrao on 2010-03-27
already fixed?! i was right. the ubuntu devs/contributors really are crazy people working during weekends :lolflag:

---

### Post by philinux on 2010-03-27
This thing is crying out for a gui, same as gdm is well overdue one.

---

### Post by bk109 on 2010-03-27
> **RomeReactor said:**
> Not sure if this is exactly what you're referring to, but as far as I know, fglrx doesn't support kms; no kms, no plymouth.
Thanks for ^^^that clarification :) . In any case, I was just curious to see if both events were connected or not... Not that I care that much for 5 seconds worth of a splash screen...

---

### Post by ranch hand on 2010-03-27
Oh well, they must be trying to fix plymouth.  Wish that they had left it where it was last night.

Couldn't boot to my main OS after this mornings upgrade.

Tried recovery.  Some system 1365 was supposedly running.  Nothing was happening.  Alt-SysRg-b and try it again, same thing.

Cntrl-Alt-F5 and logged in and "startx" and here I am.  So plymouth is working as it should again.

Bummer.

---

### Post by ranch hand on 2010-03-27
I can boot again.  Easy fix.
```

sudo apt-get remove plymouth

```
With the plymouth "upgrade" yesterday that stopped plymouth from working I was booting in 36 seconds.

With the "fix" today I couldn't boot.

With plymouth removed and mountall looking for it I am booting (second reboot to check speed) it is at 48 seconds.

---

### Post by vishalrao on 2010-03-27
@RomeReactor and @bk109 - I believe a developer (keybuk) tried to clear the misconception about "no kms = no plymouth"... you can get plymouth themes running if you dont have KMS (for example with the NVIDIA and ATI prorietary driver) via alternate renderers to vesa, text etc...

---

### Post by dyltman on 2010-03-27
Apperently plymouth works for me with nvidia but it looks incredible ugly (no it's not the non-working one). Kinda looks like the quality of the picture dropped.

---

### Post by kansasnoob on 2010-03-27
My boot times are all over the place, from about 30 seconds to over a minute. So is the "graphic image", on one boot it may look acceptably pleasant, and on the next it may be so large it won't fit my 22" widescreen.

It's surely a hard hat area :D

---

### Post by jaco223 on 2010-03-27
I've noticed since updating yesterday I'm getting can't connect to plymouth when I boot up
I notice this msg when Ubuntu hangs at the flashing cursor momentarily, but it boots up ok
I'm getting about a 15 sec. boot time according to bootchart.

---

### Post by Didius Falco on 2010-03-27
I've had a bit of a regression since the last update. I'm getting a black screen at first, then the ureadahead info , then the gui part starts up. 

Roughly halfway through the gui part of the boot, the screen suddenly goes to solid black for about 2 seconds, then the gui reappears, winding up at the log in screen.

Not a major problem, of course, but it's still a regression...

---

### Post by TrevT93 on 2010-03-27
After the latest update, Plymouth has gone from not showing at startup or shutdown to showing at shutdown.  But not at startup.

An improvement, but not working as it should quite yet :\ .  Still more than a month left to fix it, though, so I'm confident it will come through eventually.

(Wondering: could this be because I'm using GRUB Legacy (via Arch Linux), not the Ubuntu-preinstalled GRUB2?  I doubt it, but I figured I may as well check with the professionnals before I go off and assume.)

---

### Post by ranch hand on 2010-03-27
The boot loader should have no effect on Plymouth.  It is over and done once Plymouth starts.  I do not have 0.97 on any installs using Plymouth to check but I do not think it worth the effort to revert one either.  It just should not matter.

---

### Post by RomeReactor on 2010-03-27
> **vishalrao said:**
> @RomeReactor and @bk109 - I believe a developer (keybuk) tried to clear the misconception about "no kms = no plymouth"... you can get plymouth themes running if you dont have KMS (for example with the NVIDIA and ATI prorietary driver) via alternate renderers to vesa, text etc...

You're right, thanks for the clarification. I should have specified I was referring to the graphical splash as opposed to the text-based one. Since I'm using an ATI X1650 Pro I had to disable modesetting (otherwise I get a barely usable desktop with metacity, and a mostly unusable one with compiz), and get the text-based splash... though it only lasts for about a second on bootup, and about five on shutdown.

---

### Post by vishalrao on 2010-03-27
working well for me after updating an hour or so ago from main archives :) i set the gfxpayload grub option for my laptop here...

---

### Post by VMC on 2010-03-27
> **jaco223 said:**
> I've noticed since updating yesterday I'm getting can't connect to plymouth when I boot up
I notice this msg when Ubuntu hangs at the flashing cursor momentarily, but it boots up ok
I'm getting about a 15 sec. boot time according to bootchart.

I get this too. I just installed live-daily Mar27th. Adding *--verbose* shows plymouth running and I also see the splash ok.

---

### Post by VMC on 2010-03-27
> **mc4man said:**
> I *believe* it goes something like this now for what theme is used (they need to be installed  first - 



And there are also these ..?
Ok, with todays daily-live, I only have one theme:

$ sudo update-alternatives --config default.plymouth
There is only one alternative in link group default.plymouth: /lib/plymouth/themes/ubuntu-logo/ubuntu-logo.plymouth
Nothing to configure.

solar and the rest are gone.

---

### Post by mc4man on 2010-03-27
> solar and the rest are gone.

Thay's what i meant by "installed' - go into synaptic, search plymouth and install 
(all the themes are now indiv. packages


edit:

Took a while to find because it's been superseded by the 1ubuntu1
> plymouth (0.8.1-1) lucid; urgency=low

  [ Scott James Remnant ]
  * Update to the upstream 0.8.1 release:
    - Our patches have been merged upstream, some changes due to cleaning
      them up for submission and noticing a few bugs along the way.
      Remaining changes are:
      + ubuntu-logo theme
      + ubuntu version of the text theme
      + call update-initramfs rather than plymouth-update-initrd in
        plymouth-set-default-theme
      + filter fsck progress updates from the progress bar tracker
      + watch for enter key press
      + support lbm-nouveau as an alternate driver name for nouveau to
        permit backports once Lucid has released
      + use /dev/fb0 as default framebuffer device name
      + stop animation of script plugin in idle function
    - Will become process group leader of its VT if possible (opens without
      O_NOCTTY when redirecting stdio to it), this is almost certainly
      correct keyboard-wise.
    - Deallocates VT on "plymouth quit" after switching VT back to VT1
    - Open terminal in text and details plugin, don't assume it's already
      open.
    - Calling "plymouth quit" or "plymouth deactivate" while the same
      command is already running will now block the new command until the
      old one complete, rather than returning immediately.
    - Various window fixes for script plugin
    - Script plugin updated to use the window X and Y offsets every time
    - Plymouth client tool has been updated to have commands for many cases
      in preference to the --command style.

  * Restored code to disable Plymouth's graphical plugins when an alternate
    init= is given on the kernel command-line, otherwise init=/bin/bash
    doesn't work so well when Plymouth is in the initramfs.
  * Restored crash handler that dumps boot messages to /dev/tty1.

  * Split themes out into different packages, reducing the size of the
    Plymouth package.  This also means that you can remove the themes
    packages to remove the "graphical splash" part of Plymouth while keeping
    the ability to prompt for questions on the console.
  * Use the alternatives system to select the default themes.  The existing
    symlink will be replaced on upgrade if you have not changed it.
  * Also use alternatives to select the text theme.
  * Restore the upstream text theme, renaming ours to "ubuntu-text".
  * Fallback to the built-in details theme (boot messages on console, but
    with the ability to prompt for questions) if no theme package is
    installed.
  (LP: #507238)

    Unfortunately these changes mean that if you've selected a custom
    theme, you will need to install that package and select it again.
    Sorry about that.

  * Include the 16-color VGA frame-buffer renderer.  LP: #526892.

  * Fix text, ubuntu-text and details themes to restore the console to text
    mode when adding text displays.

  * debian/rules:
    - Set default tty for boot and shutdown with configure arguments
    - Set default background color to the Ubuntu Aubergine, this provides
      some consistency with other default themes.
  * debian/plymouth.upstart, debian/initramfs-tools/scripts/init-top/plymouth:
    - Redirect console output to Plymouth, this will be both logged and made
      available to splash themes that want it (details by default).
      LP: #535108.
  * debian/plymouth.upstart, debian/plymouth.plymouth-splash.upstart:
    - Call show-splash from the plymouth script itself in the shutdown case.

  * ubuntu-logo theme:
    - Update in same manner as script has been to add Window.GetX() to
      math that centers things.

  [ Steve Langasek ]
  * ubuntu-logo theme:
    - fix the password prompt handling so the display of boot messages is
      restored after the passphrase has been entered, and subsequent password
      requests don't incorrectly reuse the previous prompt.  LP: #515822
    - turn the message_notification[0].y check right-way-round in
      password_dialogue_setup(), though this doesn't seem to have any
      practical impact.
    - pass logo.z to the SetZ() function, not the SetY() one; thanks to
      Vishal Rao for this catch.  LP: #542458.
    - refactor get_message_label: the y position of the second line shouldn't
      vary according to its own height.  This brings the passphrase prompts
      from cryptsetup back up to where they should be.  LP: #539723.
  * Turn tracing on post-beta.
  * src/main.c: when the user presses enter, compare the keystroke lists to
    the enter key, not to some previously-typed string that we may or may not
    have.
 -- Scott James Remnant < [email]scott@ubuntu.com[/email]>   Fri, 26 Mar 2010 18:52:37 +0000

---

### Post by TrevT93 on 2010-03-28
> **ranch hand said:**
> The boot loader should have no effect on Plymouth.  It is over and done once Plymouth starts.  I do not have 0.97 on any installs using Plymouth to check but I do not think it worth the effort to revert one either.  It just should not matter.

Thank you for clarifying.

---

### Post by Starks on 2010-03-28
Intel framebuffer should be enabled by default, but sadly, it isn't.

---

### Post by vishalrao on 2010-03-28
hey hey hey - got my name mentioned in a changelog :D see: [https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.1-1](https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.1-1)

> 
- pass logo.z to the SetZ() function, not the SetY() one; thanks to
      Vishal Rao for this catch.  LP: #542458.


loving my 15 milliseconds of fame! :lolflag:

---

### Post by kansasnoob on 2010-03-28
> **vishalrao said:**
> hey hey hey - got my name mentioned in a changelog :D see: [https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.1-1](https://launchpad.net/ubuntu/lucid/+source/plymouth/0.8.1-1)



loving my 15 milliseconds of fame! :lolflag:

Far out ;)

---

### Post by kansasnoob on 2010-03-28
Well I think that Plymouth is working OK here, but **think** is the key word. I've tried different themes and they all seem to work now. Shutdown and restart seem to display a "pleasant" quiet "splash" as the machine is "going down".

On the "uptake", or as it boots, from the moment I hit enter at the grub menu I first get a blank black screen with a blinking cursor in the upper left hand corner for about 20 to 25 seconds, that's followed by 3 to 5 seconds of "splash", and that's followed by another 4 or 5 seconds of black screen (no blinking cursor there), then finally the desktop - but the desktop is unresponsive for about another 20 to 30 seconds.

So it looks fairly good but it's slow, I can boot Jaunty to a usable desktop in about half the time :sad:

Not sure if that's an fsck thing, a ureadahead thing, or what. I'm on openchrome drivers here.

---

### Post by sparker256 on 2010-03-28
Is there a place to change the resolution for Plymouth? I am using the solar theme and when I browse to the to the /lib/plymouth/themes/solar/star.png image it looks like it is a much higher resolution that when Plymouth is booting up.Thanks

Bill

---

### Post by garvinrick4 on 2010-03-28
> **sparker256 said:**
> Is there a place to change the resolution for Plymouth? I am using the solar theme and when I browse to the to the /lib/plymouth/themes/solar/star.png image it looks like it is a much higher resolution that when Plymouth is booting up.Thanks

BillIN GUI is that not in startup-manager I believe.

---

### Post by Milos_SD on 2010-03-28
After latest update for plymouth and new package plymouth-theme-ubuntu-logo, my plymouth doesn't work anymore when starting Ubuntu, but works when turning it off. I just get something like this:

plymouth.log process (PID) has ended with error status (1). :(

---

### Post by dino99 on 2010-03-28
have removed plymouth-x11 to see if jockey return wrong info about nvidia driver "activated but not in use", nothing changed.

Don't know what that package brings anyway (seen documentation but too vague)

---

### Post by kansasnoob on 2010-03-28
> **garvinrick4 said:**
> IN GUI is that not in startup-manager I believe.

Not that I've seen, and I pay lots of attention to grub things. I'd like you to show me where you can change that thru grub2 in startupmanager.

---

### Post by VMC on 2010-03-28
For the last two days, on the last two daily-live installs I've been getting "mountall: could not connect to plymouth". 

I use to get that error when I removed plymouth, which I no longer do. So I looked up any relevant bug reports and was about to file a new one.

Now I just noticed we have another new plymouth update: "*plymouth_0.8.1-1ubuntu*2"

Edit:It made no difference, I still get mountall error. This was fixed in a previous version of plymouth. I guess I will file a new bug report.

---

### Post by ranch hand on 2010-03-29
> **VMC said:**
> For the last two days, on the last two daily-live installs I've been getting "mountall: could not connect to plymouth". 

I use to get that error when I removed plymouth, which I no longer do. So I looked up any relevant bug reports and was about to file a new one.

Now I just noticed we have another new plymouth update: "*plymouth_0.8.1-1ubuntu*2"

Edit:It made no difference, I still get mountall error. This was fixed in a previous version of plymouth. I guess I will file a new bug report.
I am not filing bugs on this.  I can boot, which I could not when plymouth "worked".

As far as I am concerned they have fixed it.  I am getting boot speeds under 30 seconds on installs that have never done better than 40 or 50.

I like plymouth that throws errors better than one that doesn't because it works better.

---

### Post by mc4man on 2010-03-29
> been getting "mountall: could not connect to plymouth". 

Been seeing that on both nouveau and nvidia-current installs, myself just condider it a message and pay it no mind.

Overall plymouth works fine on both with all the current themes available, obviously they look better on nouveau than nvidia though none atm are much to look at.

Personally just using the ubuntu logo (5 lights), which to me is the nicest of the bunch and looks ok on nvidia-current (though I did edit the ubuntu_logo.png for the  nvidia-current install so it displays smaller and sharper and also set a different background color more suitable for my  lcd.

I wouldn't doubt down the road you'll see some custom themes of some interest.

Myself don't pay much attention to the boot, the only ubuntu release to date with  one even  worth looking at is karmic's, now that could of made an interesting plymouth theme.

---

### Post by garvinrick4 on 2010-03-29
> **kansasnoob said:**
> Not that I've seen, and I pay lots of attention to grub things. I'd like you to show me where you can change that thru grub2 in startupmanager. Me either but I do know that there were 2 spots in startup-manager to change resolution and 1 spot in Sys/Pref/Monitors do not quite remember where all GUI settings are but would say 95% or so.

---

### Post by teh603 on 2010-03-29
> **VMC said:**
> For the last two days, on the last two daily-live installs I've been getting "mountall: could not connect to plymouth". 

I use to get that error when I removed plymouth, which I no longer do. So I looked up any relevant bug reports and was about to file a new one.

Now I just noticed we have another new plymouth update: "*plymouth_0.8.1-1ubuntu*2"

Edit:It made no difference, I still get mountall error. This was fixed in a previous version of plymouth. I guess I will file a new bug report.
Same thing here, and I hadn't updated for three or four days. Boot time's still nice and short, though.

---

### Post by zoomy942 on 2010-03-29
> **Milos_SD said:**
> After latest update for plymouth and new package plymouth-theme-ubuntu-logo, my plymouth doesn't work anymore when starting Ubuntu, but works when turning it off. I just get something like this:

plymouth.log process (PID) has ended with error status (1). :(

same here

---

### Post by vishalrao on 2010-03-29
im actually playing it safe and wont update anything til beta2 freeze/release... :) maybe just help test the candidate ISOs if i have time...

---

### Post by Uncle Spellbinder on 2010-03-29
Not working here any longer either. On login I get the purple screen with 2 highly pixelated Ubuntu logos places side by side. At least I think they're Ubuntu logos, it's impossible to make out. On logout, I get the same thing.

---

### Post by mc4man on 2010-03-29
I guess, as usual, it's all about hardware, those plymouth updates were mainly of a 'bookkeeping' sort, works fine here, though did replace the changes I made to the ubuntu logo theme.

For nvivdia-current, as mentioned, at the very least a simple rescaling of the .png's makes a world of difference here on a hd lcd and only takes a min. or so in gimp.

---

### Post by kansasnoob on 2010-03-29
Well after this AM's updates (including the kernel) I'm kind of back to normal. Can't boot at all with Plymouth installed :lolflag:

Seriously the only way I can boot is going into recovery mode, then selecting "netroot", and running apt-get purge plymouth. Then I boot just fine.

I've repeated the behavior 3 times just to be sure.

---

### Post by VMC on 2010-03-29
If you get this message on bootup:
> mountall: Could not connect to plymouth

I have a bug report filed [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551062").

> Note:Weird thing is if I add verbose to the boot string the message never occurs.

---

### Post by Owen.C93 on 2010-03-29
I'm ok, that might be due to having a xorg.conf though.

---

### Post by ratcheer on 2010-03-29
> **VMC said:**
> If you get this message on bootup:

I have a bug report filed [**_here_**]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551062").

I added myself you your bug report.

Tim

---

### Post by zoomy942 on 2010-03-29
my bootup still works after todays updates, but i dont see plymouth anymore.  I will just sit tight and see how the updates go in the coming days

---

### Post by ranch hand on 2010-03-29
I decided to reinstall plymouth on this install just to see if it would boot now, none of the other 10.04 installs had any problem with is so I figured with a couple updates it may work.

It did.  I ran this evenings upgrade and installed plymouth by chroot from another installation.

Knowing that ureadahead needed to update itself with the new stuff I booted, made sure it was up and rebooted.  The second time in I pulled up bootchart to see if it worked (ususally on this install it works).  It did.

The first boot in with the update and plymouth install was 37 seconds.  The second boot interested me the most as it should have been faster as I understand the function of ureadahead.  48 seconds.

This makes no sense to me at all.

---

### Post by ShadowDragon on 2010-03-30
> **ranch hand said:**
> The first boot in with the update and plymouth install was 37 seconds.  The second boot interested me the most as it should have been faster as I understand the function of ureadahead.  48 seconds.

This makes no sense to me at all.

But is it ureadahead who's taking more time to complete on your bootchart, or is it something else? That's the question ;)

---

### Post by k3lt01 on 2010-03-30
> **ShadowDragon said:**
> But is it ureadahead who's taking more time to complete on your bootchart, or is it something else? That's the question ;) ureadahead doesn't do the bootchart, bootchart does the bootchart and it is finalised when the boot process is completed. All ureadahead does is profile the boot files when they are changed so the subsequent boots are quicker.

It does remain however that for some systems ureadahead is a bottleneck and can in some cases cripple a system. keybuk is working on this though and I am confident he will work through it.

---

### Post by ratcheer on 2010-03-30
My boots with my latest installation (from Mar 29 Live CD) are very fast up to the point of giving me the desktop login dialog. But then, it takes another 30 seconds or so for the desktop to become usable.

On my system, the plymouth splash screen is now ugly and blurry, whereas a couple of weeks ago it was crisp and well-defined. But, it is now only lasting a few seconds.

Tim

---

### Post by praveenthivari on 2010-03-30
> **ratcheer said:**
> My boots with my latest installation (from Mar 29 Live CD) are very fast up to the point of giving me the desktop login dialog. But then, it takes another 30 seconds or so for the desktop to become usable.

On my system, the plymouth splash screen is now ugly and blurry, whereas a couple of weeks ago it was crisp and well-defined. But, it is now only lasting a few seconds.

Tim

Almost similar thing happening here. I hv auto login so I dont hv login screen. But it looks similar bcoz I here the start up sound immediately after plymouth disappears and then it takes lot of time to show the desktop. I cannot quantify though, how much it takes. 

However, in alpha3 stage, the bootchart showed around 18 sec, which I dont believe to be correct. So I hvn't tried to install bootcharting thing in this.

---

### Post by zika on 2010-03-30
It seems that I've stumbled on one more story about Plymouth: [http://ubuntuforums.org/showthread.php?t=1441299](http://ubuntuforums.org/showthread.php?t=1441299)... To be continued...

---

### Post by zoomy942 on 2010-03-30
what i am hoping is that a reinstall of the final release or even beta 2 won't be needed.  they will just iron out the plymouth issues on the fly.

---

### Post by emarkay on 2010-03-30
> **zoomy942 said:**
> what i am hoping is that a reinstall of the final release or even beta 2 won't be needed.  they will just iron out the plymouth issues on the fly.

FWIW, I plan to do a complete install of Beta2 - that way I am testing from a "known good point" in preparation for the RC, where I will again do that.  

Some believe in cumulating updates as testing to see incompatibilities, but I prefer to use the established "markers" as starting points.

I am also curious to see what the point of Plymouth is, beyond a few seconds of "pretty" and some booting config enablers in the grand scheme of things; it seems like this was something not well thought out to have been release so "not ready to go".

---

### Post by ranch hand on 2010-03-30
> **emarkay said:**
> FWIW, I plan to do a complete install of Beta2 - that way I am testing from a "known good point" in preparation for the RC, where I will again do that.  

Some believe in cumulating updates as testing to see incompatibilities, but I prefer to use the established "markers" as starting points.

I am also curious to see what the point of Plymouth is, beyond a few seconds of "pretty" and some booting config enablers in the grand scheme of things; it seems like this was something not well thought out to have been release so "not ready to go".
Yup, I have a lot of room and have a number of installs but one of them is for testing ISOs so it is reinstalled at every benchmark release (about a day ahead actually as it is from the last testing image).

That way I do have a comparison OS for the rest of them.  I also use it to update/upgrade first every time to find out if it is safe to do the rest that I do not want to reinstall.

---

### Post by zoomy942 on 2010-03-30
agreed mostly.  but for me i like to do the upgrade path because most standard users do the upgrade path rather than reinstall.  

also i use a verizon mifi, so i cant go DL'ing iso's all the time.  LOL  (5GB limit)

---

### Post by MrGreen on 2010-03-31
I have on many updates got grep error default.plymouth and text.plymouth no such file found...

Start up black screen some disc messages then login

Boot time is very good still

No more crashes from plymouth at the moment

MrG

---

### Post by Didius Falco on 2010-03-31
> **MrGreen said:**
> I have on many updates got grep error default.plymouth and text.plymouth no such file found...

Start up black screen some disc messages then login

Boot time is very good still

No more crashes from plymouth at the moment

MrG

The message you are seeing is because the various plymouth themes have been removed, and are now available as separate downloads.

Plymouth is just telling you that those two themes aren't being found. If you want those and/or others, just fire up Synaptic and do a search for 
```
plymouth-theme
```The way you change themes has changed as well, afaik. I never change it, so I don't know the code, but I've seen threads on it...

Regards,

Didius

P.S. I did a quick search and found out that if you read ```
/usr/share/doc/plymouth/README.Debian
```
It tells you how to install and change themes...

---

### Post by zoomy942 on 2010-03-31
> **Didius Falco said:**
> The message you are seeing is because the various plymouth themes have been removed, and are now available as separate downloads.

Plymouth is just telling you that those two themes aren't being found. If you want those and/or others, just fire up Synaptic and do a search for 
```
plymouth-theme
```The way you change themes has changed as well, afaik. I never change it, so I don't know the code, but I've seen threads on it...

Regards,

Didius

P.S. I did a quick search and found out that if you read ```
/usr/share/doc/plymouth/README.Debian
```
It tells you how to install and change themes...

wait...

so on people whose plymouht doesnt show up at all (no errors) should we do these steps too?

---

### Post by JUSTINBEAIRD on 2010-03-31
i didn't read all these posts but during boot i see a blinking underscore at the top then i sometimes see diskcheck text then a quick list of text one that stands out is unable to prob monitor invalid ESID or something like that then i see a quick flash of red too fast to see what it is i imagine its the splash then gdm starts however i do see Plymouth at shutdown

---

### Post by amano on 2010-03-31
New updates are in the queue! A new plymouth and a new mountall. Especially the mountall update seems to be very big:
[https://lists.ubuntu.com/archives/lucid-changes/2010-March/009527.html](https://lists.ubuntu.com/archives/lucid-changes/2010-March/009527.html)
>   * Rework the Plymouth connection logic; one needs to attach the client to
    the event loop *after* connection otherwise you don't get disconnection
    notification, and one needs to actually actively disconnect in the
    disconnection handler.
  * For safety and sanity reasons it becomes much simpler to create the
    ply_boot_client when we connect, and free it on disconnection.  Thus the
    presence or not of this struct tells us whether we're connected or not.
    LP: #524708.
  * Flush the plymouth connection before closing it and exiting, otherwise
    updates may be pending and the screen have messages that confuse people
    while X is starting (like fsck at 90%).  LP: #487744.

  * Replace the modal plymouth prompt for error conditions with code that
    continues working in the background while prompting.  This most benefits
    the old "Waiting for" message, which can now allow you to continue to
    wait and it can solve itself.  LP: #527666, #545435.
  * Integrate fsck progress updates into the same mechanism.
  * Allow fsck messages to be translated.  LP: #390740.
  * Change fsck message to be a little less alarming.  LP: #545267.
  * Add hard dependency on Plymouth; without it running, mountall will
    ignore any filesystem which doesn't show up within a few seconds or that
    fails to fsck or mount.  If you don't want graphical splash, you simply
    need not install themes.

  * Improve set of messages seen with --verbose, and ensure all visible
    messages are marked for translation.  LP: #446592.
  * Reduce priority of failed to mount error for remote filesystems since
    we try again, and this just spams the console.  LP: #504224.

  * Keep hold of the dev_t when parsing /proc/self/mountinfo, then after
    mounting /dev (or seeing that it's mounted) create a quick udev rules
    file that adds the /dev/root symlink to this device.  LP: #527216.
  * Do not try and update /etc/mtab when it's a symbolic link.  LP: #529993.
  * Remove odd -a option from mount calls, probably a C&P error from the
    fsck code long ago.  LP: #537135.
  * Wait for Upstart to acknowledge receipt of events, even if we don't
    hang around for them to be handled.
  * Always run through try_mounts() at least once.  LP: #537136.
  * Don't keep mountall running if the only remaining unmounted filesystems


Thanks to keybuk for his efforts to tame this beast ;)

From what I understand:
Mountall now DEPENDS on plymouth. Interesting for those, who totally removed plymouth. If they don't want the splash, they are advised to remove just the plymouth-themes package.

And the fsck messages should work better now.

---

### Post by ratcheer on 2010-03-31
I noticed I got a new mountall in this morning's updates. Is that the one you are referring to, or are still more changes imminent? At this point, things are working just fine, for me. Maybe a tad slower than yesterday, but functionally good.

Tim

---

### Post by amano on 2010-03-31
There will be a new one: Mountall 2.10

Mountall 2.9 just shipped a small fix.

---

### Post by keybuk on 2010-03-31
> **amano said:**
> Mountall now DEPENDS on plymouth. Interesting for those, who totally removed plymouth. If they don't want the splash, they are advised to remove just the plymouth-themes package.

Yes.  The only way to not have Plymouth is to go use Gentoo or something ;-)

If you don't want a graphical splash screen, that's quite different, just remove the plymouth-theme-* packages or remove "splash" from the kernel command-line.

(We're working things so you'll get all the old Starting messages back for lucid)

Plymouth is still installed, and still running, and is there so when a fsck fails, we can prompt you about it during boot, etc.

---

### Post by zoomy942 on 2010-03-31
> **JUSTINBEAIRD said:**
> i didn't read all these posts but during boot i see a blinking underscore at the top then i sometimes see diskcheck text then a quick list of text one that stands out is unable to prob monitor invalid ESID or something like that then i see a quick flash of red too fast to see what it is i imagine its the splash then gdm starts however i do see Plymouth at shutdown

me too.  so im wondering if thats a bug requiring reinstall or just a bug to sit tight and see if it will be fixed - or if i have to do something in synaptic

---

### Post by ShadowDragon on 2010-03-31
> **keybuk said:**
> If you don't want a graphical splash screen, that's quite different
Since loading the splash-screen almost takes longer than actually seeing it, I'm already booting with nosplash for a year now. :p

---

### Post by amano on 2010-03-31
> **keybuk said:**
> Yes.  The only way to not have Plymouth is to go use Gentoo or something ;-)

If you don't want a graphical splash screen, that's quite different, just remove the plymouth-theme-* packages or remove "splash" from the kernel command-line.

(We're working things so you'll get all the old Starting messages back for lucid)

Plymouth is still installed, and still running, and is there so when a fsck fails, we can prompt you about it during boot, etc.

Thank you again for sharing the details. Those explainations are very welcome. :KS

---

### Post by JUSTINBEAIRD on 2010-03-31
> **zoomy942 said:**
> me too.  so im wondering if thats a bug requiring reinstall or just a bug to sit tight and see if it will be fixed - or if i have to do something in synaptic

I don't know but i installed the daily yesterday and the same thing

---

### Post by zoomy942 on 2010-03-31
> **JUSTINBEAIRD said:**
> I don't know but i installed the daily yesterday and the same thing

good to know.  i will sit tight then

---

### Post by garvinrick4 on 2010-04-02
With download of recent mountall upgrade will go to splash screen of choice and will boot if I
press the s key which it tells me on bottom of plymouth default splash but not when solar is
installed but solar will go to boot also if I press s key. Getting better for me, can now keep plymouth installed and get to a boot.

---

### Post by prodigy_ on 2010-04-03
It seems, they've forcefully made Plymouth a dependency for everything, including Xorg, ntfs-3g and whatnot. So that you couldn't even remove this unneeded [censored].
/facepalm

Way to shoot yourself in the foot, dear Canonical. Well done.

---

### Post by emarkay on 2010-04-03
> **prodigy_ said:**
> It seems, they've forcefully made Plymouth a dependency for everything, including Xorg, ntfs-3g and whatnot. So that you couldn't even remove this unneeded [censored].
Way to shoot yourself in the foot, dear Canonical. Well done.

Confirmed, but apparently it's needed as noted above - prob has something to do with the silly "move the buttons to the left but don't tell anyone why" big secret idiocracy...

So far it's working; haven't needed to remove it, again.  Will do some digging to see why this "thing" has become so core intensive...

---

### Post by NightwishFan on 2010-04-03
Similar how it is nearly impossible to not have QT on OpenSUSE. Not easy anyway.

---

### Post by prodigy_ on 2010-04-03
Well, ```
sudo rm -f /bin/plymouth
``` took care of it nicely. I just wonder why I can't do the same via aptitude.

"Linux isn't a corporation", anyone? Haha. Now it is. The brand is everything, so they're just forcing it upon the community.

Disgusting!

---

### Post by Jordanwb on 2010-04-03
Update manager just told me there were three updates: mountall, plymouth and plymouth-theme-ubuntu-text. I uncheck plymouth-theme-ubuntu-text so that its not installed, but it gets installed anyways.

[img]http://img532.imageshack.us/img532/277/facepalmx.jpg[/img]

---

### Post by ranch hand on 2010-04-03
> **prodigy_ said:**
> Well, ```
sudo rm -f /bin/plymouth
``` took care of it nicely. I just wonder why I can't do the same via aptitude.

"Linux isn't a corporation", anyone? Haha. Now it is. The brand is everything, so they're just forcing it upon the community.

Disgusting!
Linux is not a corporation.  Red Hat is.  Canonical is.  Google has their OS.

There is no restriction on corporate participation in Linux.

There are distros like Debian that aren't.  PhatDebian is not either and it has ext4 support although it is ext3 (runs the 2.6.30 kernel).  Nice OS.

---

### Post by NightwishFan on 2010-04-03
There is room in free software for business.

---

### Post by fedexnman on 2010-04-04
plymouth and nvidia drivers are'nt jiving well, i get the purple boot screen in low resolution and then a black screen then the finally the desktop screen, not too smooth so far, but its beta, 25 more days to go woo hoo !

---

### Post by emarkay on 2010-04-04
Beta 2 about here - so we all good in Plymouth-land now?

---

### Post by VMC on 2010-04-04
I doubt it, since we just got another plymouth update in the past couple hours.

I'm ok, but we still have several people reporting errors booting. Either video or plymouth errors. Or a combination of both.

This may end up a long arduous process.

---

### Post by FrancoNero on 2010-04-05
will lucid final have plymouth working for everyone or will all the ati/nivida people get the ugly boot-up screen?

---

### Post by sgosnell on 2010-04-05
It would be easy if either company would make their drivers open-source, but it takes time to reverse-engineer them.  It will get done eventually, if not by the end of the month.

---

### Post by atlee on 2010-04-05
Yes the Plymouthd 4th April update does crash, I have "nouveau" blacklisted so my nvidia drivers load.

---

### Post by Martje_001 on 2010-04-05
> **FrancoNero said:**
> will lucid final have plymouth working for everyone or will all the ati/nivida people get the ugly boot-up screen?
ATi users won't when using the OSS driver. Same story for NVidia.

---

### Post by ratcheer on 2010-04-05
> **sgosnell said:**
> It would be easy if either company would make their drivers open-source, but it takes time to reverse-engineer them.  It will get done eventually, if not by the end of the month.

In fact, nVidia recently announced that they were dropping their open source drive project. I'll try to find a link and post it.

Tim

---

### Post by ratcheer on 2010-04-05
> **ratcheer said:**
> In fact, nVidia recently announced that they were dropping their open source drive project. I'll try to find a link and post it.

Tim


Here it is: [http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1)

Tim

---

### Post by NightwishFan on 2010-04-05
Nvidia are dropping it because Nouveau is already better. :lolflag:

The above is probably true, but it really is just opinion. (my post not the poster above)

---

### Post by jrothwell97 on 2010-04-05
> **NightwishFan said:**
> Nvidia are dropping it because Nouveau is already better.

Yes.

Anyway, IMHO the problems with the Plymouth splash looking ugly in non-KMS mode could probably be fixed by reducing or eliminating the glow on the "ubuntu" lettering - it's a little superfluous and doesn't work in low graphics.

Just my two cents' worth.

---

### Post by teh603 on 2010-04-05
> **NightwishFan said:**
> Nvidia are dropping it because Nouveau is already better. :lolflag:

The above is probably true, but it really is just opinion. (my post not the poster above)I won't consider it better until it gets full support for all chipsets. Including 3D support. Just because the Plymouth bootsplash looks nice doesn't mean anything else will.

---

### Post by NightwishFan on 2010-04-05
The open source Nvidia driver does not support 3D either. If you require 3d support you should use the proprietary driver until such a time Nouveau fits your needs.

---

### Post by BrokeMahPC on 2010-04-05
I found the new Proprietary ATI Driver listed under System - Administration - Hardware Drivers,  yesterday.
Graphics card - ATI Radeon HD4670
Monitor - Viewsonic 1920x1080 22inch VX2260wm
Clicked to activate it and rebooted and things did not go well.
Suddenly remembered to do.
code:
sudo aticonfig --initial -f

It was fine after this but Plymouth (which was working fine under the  open source ATI driver) went into some 640x480 low res mode and looked  awful. after a read of the "what's happening with plymouth?" thread I found  this document:
/usr/share/doc/plymouth/README.Debian

It mentions something about the proprietry driver doing this (the Nvidia  people are having problems as well) as there is a problem with  suspend/resume in higher resolutions. It also suggests a few lines of  code to fix the problem if you are not concerned about suspend/resume. 
I  tried them and it worked, don't use suspend so someone might want to  test that.

I don't get plymouth full screen though - there is a black border around  it but the dots under the ubuntu logo do change from white to orange  in sequence on startup and shutdown. It wasn't animating like this before the above fix. The image isn't great though.

Is there a way of changing resolution in Plymouth?
I suspect it might be my HD monitor 1920x1080 - not a common res?

---

### Post by QwUo173Hy on 2010-04-05
I'm getting plymouth on shutdown but darkness / console for boot. Is that what everyone else has at this stage?

---

### Post by garvinrick4 on 2010-04-05
Linux rick-laptop 2.6.32-19-generic #28-Ubuntu SMP Thu Apr 1 10:39:41 UTC 2010 x86_64 GNU/Linux
Lucid 10.04
rick@rick-laptop:~$ aptitude show plymouth
Package: plymouth
New: yes
State: installed
Automatically installed: yes
Version: 0.8.1-4ubuntu1
Priority: required
Section: x11
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 487k
Depends: libc6 (>= 2.8), libdrm-intel1 (>= 2.4.9), libdrm-nouveau1 (>=
         2.4.11-1ubuntu1~), libdrm-radeon1 (>= 2.4.17), libdrm2 (>= 2.4.3),
         libplymouth2 (= 0.8.1-4ubuntu1), upstart-job, udev (>= 149-2), mountall
         (>= 2.0)
Recommends: plymouth-theme-ubuntu-text | plymouth-theme
Conflicts: usplash
Breaks: gdm (< 2.29.1-0ubuntu4), lubuntu-plymouth-theme (<= 0.4),
        ubuntustudio-plymouth-theme (<= 0.38), xubuntu-plymouth-theme (<
        10.04.4)
Description: graphical boot animation and logger - main package
 Plymouth is an application that runs very early in the boot process (even
 before the root filesystem is mounted!) that provides a graphical boot
 animation while the boot process happens in the background.

rick@rick-laptop:~$ aptitude show mountall
Package: mountall
State: installed
Automatically installed: no
Version: 2.10
Priority: required
Section: admin
Maintainer: Scott James Remnant <scott@ubuntu.com>
Uncompressed Size: 238k
Depends: makedev, udev, plymouth, coreutils (>= 7.1), libc6 (>= 2.9),
         libdbus-1-3 (>= 1.2.16), libnih-dbus1 (>= 1.0.0), libnih1 (>= 1.0.0),
         libplymouth2 (>= 0.8.1-3), libudev0 (>= 147)
Breaks: policycoreutils (< 2.0.69-2ubuntu4), usplash (< 0.5.47)
Replaces: upstart (< 0.6.3-2)
Description: filesystem mounting tool
 mountall mounts filesystems when the underlying block devices are ready, or
 when network interfaces come up, checking the filesystems first.

rick@rick-laptop:~$ 

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Hewlett-Packard Company Device 306b
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4110 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915


#With last upgrades of mountall and plymouth and fstab with proper mount point
#plymouth now works fine.


proc /proc proc defaults 0 0 
# / was on /dev/sda5 during installation 
UUID=1fa6b366-0d18-442c-91cb-506460b1b9ab  /              ext4         errors=remount-ro                  0  1  
# swap was on /dev/sda6 during installation 
UUID=904f3813-9702-4940-ac21-33bdcbd44644  none           swap        

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 
#/dev/sda2 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0 
#/dev/sda1 /media/SYSTEM ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by VMC on 2010-04-05
> **garvinrick4 said:**
> ...
rick@rick-laptop:~$ aptitude show mountall
Package: mountall
State: installed
Automatically installed: no
Version: 2.10
...

Now explain output of mountall version:

```
mountall --version
```

Mine show 2.8 ?!

---

### Post by Orographic on 2010-04-05
My motherboard is a Gigabyte 945GZM-S2 (Rev 3.9) with Intel onboard graphics that works well in Karmic. No probs at all except a bit of tearing in full screen Flash videos.

In Lucid Beta One boot up, I get the white cursor on a black screen for a few seconds then 'Ubuntu' in white letters followed by six white dots. My boot time to the standard background is less than twenty seconds but then it takes another twenty to thirty seconds for all of the menus to appear.

Also, occasionally on boot up all of the above happens but the menus look different.The icons change appearance and the top and bottom panels change color to gray. Weird.

Just out of interest, How do I turn off Plymouth?

I'm sure things will improve but this is the buggiest Ubuntu on this system so far that has run well with Ubuntu since Hardy.

---

### Post by prodigy_ on 2010-04-06
> **Orographic said:**
> Just out of interest, How do I turn off Plymouth?
```
sudo rm -f /bin/plymouth
```

---

### Post by djchandler on 2010-04-06
> **prodigy_ said:**
> ```
sudo rm -f /bin/plymouth
```

Would it not be better to remove Plymouth via Synaptic or apt-get? Or does that cause a whold bunch of other stuff to be removed?

---

### Post by ranch hand on 2010-04-06
I am impressed with the number of updates lately.  Also impressed with the vast improvements.

Now when boot freezes because it is running fsck, which it does every time, I no longer have to unplug my box to reboot. Alt +SysRq+b works again.  That is just a huge improvement.

I figure that the bugger is ready for release.  I mean where can you get this much entertainment during boot.  Will it run fsck?  Oh the suspence!

I really like the randomness of the fsck too.  This install gets it nearly every time (at least 3 out of 4 boots) but another is actually predictable, it gets fsck run every 57th time.

Of coarse that mean that OS is no where near the FUN to boot as it doesn't freeze as often but hey, you can't have everything.

I also like the way that the updates have completely different effects on nearly identical installs on the very same drive.  Good example of chaos theory in everyday life.

Basically Plymouth is just a great addition to an otherwise fairly boring OS.

---

### Post by hikaricore on 2010-04-06
> **djchandler said:**
> Would it not be better to remove Plymouth via Synaptic or apt-get? Or does that cause a whold bunch of other stuff to be removed?

It didn't used to, but now nearly everything has plymouth listed as a dependency.
Personally I just removed it from /etc/init instead.  2 of my 5 systems refuse to boot with it active, there's no excuse for that.

---

### Post by ranch hand on 2010-04-06
> **hikaricore said:**
> It didn't used to, but now nearly everything has plymouth listed as a dependency.
Personally I just removed it from /etc/init instead.  2 of my 5 systems refuse to boot with it active, there's no excuse for that.
Are you removing all plymouth related files (4) or just the splash?

I have been eying them with thoughts of the future when we are done testing.

What is boils down to is I do not want to screw my system, but as much fun as plymouth is, there comes a time you just want your box to work.

---

### Post by hikaricore on 2010-04-06
> **ranch hand said:**
> Are you removing all plymouth related files (4) or just the splash?

I have been eying them with thoughts of the future when we are done testing.

What is boils down to is I do not want to screw my system, but as much fun as plymouth is, there comes a time you just want your box to work.

```
$ sudo apt-get remove plymouth
[sudo] password for hikaricore: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mono-2.0-gac gambas2-gb-pdf libstrigiqtdbusclient0 liblash2 xorg-docs-core libwildmidi0 libcaca-dev dvdrip-doc libzzip-0-13
  libcanberra-gtk-module xsltproc libopenal0a gambas2-gb-net-smtp gambas2-gb-web libnfsidmap2 libg15render1 libglade2.0-cil gambas2-dev
  gstreamer0.10-plugins-ugly libaudiofile-dev libfontforge1 libxcb-keysyms1 libgoffice-0.8-8-common libevent-execflow-perl dirmngr gambas2-doc
  libglib2.0-cil gambas2-gb-xml libpng3 libois-1.2.0 deluge-common libsoundtouch1c2 gambas2-gb-compress-zlib python-paramiko gambas2-gb-info
  mplayer-skins libgpac0.4.5 libxml-namespacesupport-perl dvdrip-utils libsvga1 libanyevent-perl gambas2-gb-net-curl libaio1 paintown-data
  seabios cli-common quassel-data libintl-perl liblircclient0 libopenexr2ldbl libevview2 bitpim-lib abiword-common libindicate-gtk2 bridge-utils
  reportbug lmms-common libart2.0-cil gambas2-gb-xml-rpc libopenspc0 bcmwl-modaliases libvncserver0 audacity-data amarok-common libcddb2
  transcode-utils libpar2-0 transcode-doc python-lxml python-reportlab-accel libexiv2-5 gambas2-gb-crypt libsysfs-dev libdirectfb-extra
  python-dsv mencoder libgpod4 firebird2.1-common libeina-svn-05 libdvbpsi5 caps libmono-cairo2.0-cil libpsiconv6 libgif-dev libeet1 k3b-data
  libloudmouth1-0 libasync-interrupt-perl ttf-lyx x11proto-record-dev sdparm gedit-common libqjson0 libfbclient2 libtorrent-rasterbar5
  libmono-i18n-west2.0-cil libgssdp-1.0-2 libqtscript4-core libbrlapi0.5 gambas2-gb-compress-bzlib2 gambas2-gb-pcre gambas2-runtime
  librpcsecgss3 libmono-posix2.0-cil deluge-core libexempi3 libibus-qt1 libgnomeprint2.2-data libkpathsea5 libcelt0 libmono-security2.0-cil
  vlc-nox libtiff-tools gambas2-gb-image libdirac-decoder0 gambas2-gb-vb libprotobuf5 libgii1 libupnp3 libgtk2.0-cil libxml-libxml-perl vgabios
  gambas2-gb-gtk-ext mono-gac qt4-qmake libssh2-1 gnome-doc-utils libgle3 icedax python-smbc libgme0 lsdvd libxml-sax-perl freepats python-apsw
  vamps libcanberra-gtk0 ffmpeg libwmf-bin edict libevdocument2 libavfilter0 libspeechd2 libspiro0 libesd0-dev libgii1-target-x netpbm
  libg15daemon-client1 libmono-corlib2.0-cil tileracer-data gstreamer0.10-plugins-bad libgpod-common sox python-uniconvertor stk fuseiso
  gambas2-gb-gtk-svg libkate1 gstreamer0.10-nice python-wxversion kanjidic libmimic0 libqtscript4-sql qt3-doc libcap-ng0 mono-runtime
  libcanberra0 libsidplay1 gocr libgupnp-1.0-3 libpurple-bin libslang2-dev libqtscript4-xml libg15-1 libstk0c2a x11proto-xf86vidmode-dev
  skype-common ktorrent-data libnetpbm10 filezilla-common libsilcclient-1.1-3 libindicate4 libepub0 libzephyr4 libpixman-1-dev libtag-extras1
  libtar libgtk2-ex-formfactory-perl python-wxgtk2.6 libuninameslist0 libcelt0-0 python-reportbug tap-plugins gambas2-gb-xml-xslt mkvtoolnix
  liblastfm0 python-eyed3 python-xlib marble-data libnice0 libgssglue1 libcommon-sense-perl python-chardet libgnomeprint2.2-0 libvcdinfo0
  amarok-utils libsubtitleeditor0 libebml0 python-reportlab gstreamer0.10-gnonlin firebird2.1-common-doc libqtscript4-network gambas2-gb-gtk
  libglademm-2.4-1c2a libgnomeprintui2.2-0 libmatroska0 libgupnp-igd-1.0-2 libmsn0.2 libboost-python1.40.0 libmono-system2.0-cil
  python-libtorrent libgnomeprintui2.2-common gambas2-gb-v4l libiptcdata0 gambas2-gb-opengl libgnomecups1.0-1 gambas2-gb-settings
  gambas2-gb-compress gambas2-gb-net qemu-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  abiword abiword-plugin-grammar abiword-plugin-mathview acetoneiso acpi-support acpid akregator alsa-base alsa-utils amarok anacron apache2
  apache2-mpm-prefork apache2.2-common apmd apport apport-hooks-medibuntu apturl ark arora at atanks audacity automoc avahi-daemon avahi-utils
  avidemux-plugins-common avidemux-plugins-gtk avidemux-plugins-qt avidemux-qt bitchx bitpim bluetooth bluez bluez-cups brltty bsd-mailx
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg comix computer-janitor-gtk console-setup consolekit creox cron cups
  cups-driver-gutenprint cups-pdf dbus dbus-x11 deluge deng deng-iwad-doom2-installer deng-iwad-doomu-installer deng-iwad-heretic-installer
  deng-iwad-hexen-installer deng-iwad-hexendd-installer deng-iwad-plutonia-installer deng-iwad-tnt-installer dhcdbd dkms dmsetup dolphin
  dragonplayer dvdauthor dvdrip e2fsprogs evince exim4 exim4-base exim4-daemon-light filezilla firefox firefox-branding flashplugin-installer
  fontforge foo2zjs foomatic-db foomatic-db-engine friendly-recovery ftp funguloids funpidgin gaim-data gambas2 gambas2-gb-chart gambas2-gb-db
  gambas2-gb-db-firebird gambas2-gb-db-form gambas2-gb-db-mysql gambas2-gb-db-odbc gambas2-gb-db-postgresql gambas2-gb-db-sqlite
  gambas2-gb-desktop gambas2-gb-form gambas2-gb-form-dialog gambas2-gb-form-mdi gambas2-gb-gui gambas2-gb-qt gambas2-gb-qt-ext gambas2-gb-qt-kde
  gambas2-gb-qt-kde-html gambas2-gb-qt-opengl gambas2-gb-report gambas2-gb-sdl gambas2-gb-sdl-sound gambas2-ide gcalctool gconf2 gconf2-common
  gdebi-kde gedit gelide ghostscript-cups ghostscript-x gimp gimp-gap gimp-plugin-registry gimp-resynthesizer gimp-texturize gksu gnome-keyring
  gnome-user-guide gnomebaker gnometab gnupg-agent gnupg2 google-gadgets googleearth gpac graphviz gsfonts-x11 gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gtk-recordmydesktop gtkguitune gvfs gvfs-backends gwenview handbrake-gtk hostname hotkey-setup hydrogen ibus-qt4
  icoutils ifupdown imagemagick initramfs-tools initscripts inkscape install-package intltool irqbalance istanbul jockey-common jockey-kde
  jokosher k3b k9copy kaddressbook kalarm kamera kanjisaver kannasaver kate kbd kbluetooth kcalc kcheckgmail kcm-gtk kcoloredit kcometen4 kcron
  kde-style-bespin kde-style-qtcurve kde-style-skulpture kde-window-manager kde-zeroconf kdebase-bin kdebase-plasma kdebase-runtime
  kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-dev kdebase-workspace-kgreet-plugins
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs4c2a kdelibs5 kdelibs5-dev kdemultimedia-kio-plugins
  kdenetwork-filesharing kdepasswd kdepim-groupware kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs5 kdeplasma-addons
  kdescreensaver-aasaver kdesudo kdm kepas kfind kftpgrabber kgpg khelpcenter khelpcenter4 kiten kleopatra klibido klipper kmag kmail kmix
  kmousetool kmymoney2 kmymoney2-plugin-aqbanking knotes kompozer konqueror konqueror-nsplugins konsole kontact kopete kopete-facebook
  kopete-message-indicator korganizer kpackagekit kpar2 kpovmodeler krdc krfb kscreensaver kscreensaver-xsavers kscreensaver-xsavers-extra
  ksnapshot ksysguard ksystemlog ktimetracker ktorrent ktux kubuntu-debug-installer kubuntu-notification-helper kuser kvkbd kwalletmanager
  kweather kwin kwin-style-bespin kwin-style-crystal kwin-style-dekorator kwin-style-qtcurve kwin-style-skulpture language-selector-qt
  laptop-mode-tools lftp libaa1-dev libabiword-2.8 libaldmb1 liballegro4.2 libapache2-mod-php5 libaqbanking20-plugins-qt
  libaqbanking29-plugins-qt libarts1-akode libarts1c2a libasound2-plugins libaudio-dev libaudio2 libavahi-qt3-1 libbonoboui2-0 libcairo2-dev
  libcamel1.2-14 libdbus-1-qt3 libdbus-qt-1-1c2 libdbusmenu-qt2 libdirectfb-dev libedataserver1.2-11 libfltk1.1-dev libfluidsynth1 libgcj9-0-awt
  libgconf2-4 libgconf2.0-cil libgconfmm-2.6-1c2 libgdraw4 libgdu0 libggi-target-x libggi2 libgksu2-0 libgl1-mesa-dev libglew1.4 libglew1.5
  libglew1.5-dev libglide2 libglu1-mesa-dev libgnome-vfs2.0-cil libgnome2-0 libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil
  libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgoffice-0.8-8 libgstfarsight0.10-0 libgtkglext1 libgtkhtml3.14-19
  libice-dev libice6 libimlib2-dev libindicate-qt0 libio-socket-ssl-perl libjasper-runtime libk3b6 libk3b6-extracodecs libkcddb4 libkdcraw8
  libkde4-ruby libkde4-ruby1.8 libkdecorations4 libkdepim4 libkephal4 libkexiv2-7 libkexiv2-8 libkfontinst4 libkimono4.1-cil libkipi7 libkiten4
  libkleo4 libknotificationitem1 libkonq5 libkonqsidebarplugin4 libkopete4 libkpgp4 libkscreensaver5 libksgrd4 libksieve4 libksignalplotter4
  libkwineffects1 libkworkspace4 liblancelot0 liblsofui4 libmagick++2 libmagickcore2 libmagickcore2-extra libmagickwand2 libmarble4 libmimelib4
  libnet-dbus-perl libnjb5 libnss-mdns libobrender21 libogmrip1 libogre14 libogremain-1.6.4 libokularcore1 libphonon-dev libphonon4
  libplasma-applet-system-monitor4 libplasma-ruby libplasma-ruby1.8 libplasma2.0-cil libplasma3 libplasmaclock4 libplasmagenericshell4 libplib1
  libpolkit-qt-1-0 libpolkit-qt0 libpoppler-qt2 libpoppler-qt4-3 libprocesscore4 libprocessui4 libpulse-browse0 libpulse-dev
  libpulse-mainloop-glib0 libpulse0 libpurple0 libqbanking5 libqbanking6 libqbanking8 libqedje0a libqimageblitz4 libqscintilla2-5 libqt-perl
  libqt3-mt libqt3-mt-dev libqt4-designer libqt4-dev libqt4-gui libqt4-help libqt4-multimedia libqt4-opengl libqt4-opengl-dev libqt4-phonon
  libqt4-qt3support libqt4-ruby1.8 libqt4-scripttools libqt4-svg libqt4-webkit libqtgui4 libqtruby4shared2 libqtscript4-gui libqtscript4-uitools
  libqtwebkit2.2-cil libqyoto4.5-cil libqyotoshared1 libqzion0a librpc-xml-perl libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl1.2-dev libsm-dev
  libsm6 libsmokekde4-3 libsmokeplasma3 libsmokeqt1 libsmokeqt4-3 libsmokesoprano3 libsmpeg-dev libsolidcontrol4 libsoup-gnome2.4-1
  libstartup-notification0 libtaskmanager4 libweather-ion4 libwebkit-1.0-2 libwnck22 libwww-perl libwxgtk2.8-0 libx11-dev libxau-dev libxaw7
  libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcursor-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxine1
  libxine1-misc-plugins libxine1-x libxinerama-dev libxklavier16 libxml-parser-perl libxml-sax-expat-perl libxml-twig-perl libxml-xpath-perl
  libxmu-dev libxmu-headers libxmu6 libxpm-dev libxrandr-dev libxrender-dev libxres1 libxss1 libxt-dev libxt6 libxtrap6 libxtst-dev libxtst6
  libxvmc1 libxxf86dga1 libxxf86vm-dev linux-generic linux-image-2.6.32-19-generic linux-image-generic linux-sound-base lmms logrotate
  maniadrive mesa-common-dev midori minitube mkvtoolnix-gui module-init-tools moto4lin mountall mozilla-plugin-vlc mplayer msn-pecan mumble
  mumble-11x namebench netbase nfs-common nfs-kernel-server notification-daemon ntfs-3g ntpdate nvidia-cg-toolkit nvidia-current
  nvidia-current-dev nvidia-settings nzb obconf obex-data-server ogmrip-dirac ogmrip-oggz ogre-plugins-cgprogrammanager okular
  okular-extra-backends openbox openbox-themes openprinting-ppds opensonic openssh-server opera oss-compat packagekit padevchooser paintown
  paman pandora paprefs pavucontrol pavumeter pcmciautils pdfmod perlmagick phonon phonon-backend-gstreamer phonon-backend-gstreamer-bad
  phonon-backend-xine php5 phun pidgin pidgin-convcharcount-plugin pidgin-facebookchat pidgin-lastfm pidgin-libnotify pidgin-microblog
  pidgin-plugin-pack pidgin-themes pinentry-qt pinentry-qt4 plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop
  plasma-runners-addons plasma-scriptengine-javascript plasma-scriptengine-python plasma-scriptengine-qedje plasma-scriptengine-ruby
  plasma-scriptengine-superkaramba plasma-scriptengine-webkit plasma-scriptengines plasma-wallpapers-addons plasma-widget-adjustableclock
  plasma-widget-bkodama plasma-widget-cpuload plasma-widget-customizable-weather plasma-widget-daisy plasma-widget-drop2ftp
  plasma-widget-droptoimageshack plasma-widget-facebook plasma-widget-fancytasks plasma-widget-flickr plasma-widget-folderview
  plasma-widget-fortunoid plasma-widget-googlecalendar plasma-widget-kbstate plasma-widget-kepas plasma-widget-kimpanel
  plasma-widget-kimpanel-backend-ibus plasma-widget-ktorrent plasma-widget-kubuntu-qa-feedback plasma-widget-lancelot plasma-widget-lastmoid
  plasma-widget-logout plasma-widget-mail plasma-widget-memusage plasma-widget-message-indicator plasma-widget-nextwallpaper plasma-widget-pgame
  plasma-widget-playwolf plasma-widget-quickaccess plasma-widget-runcommand plasma-widget-searchmoid plasma-widget-simplemonitor
  plasma-widget-stasks plasma-widget-stockquote plasma-widget-system-status plasma-widget-teacooker plasma-widget-tictactoe
  plasma-widget-toggle-compositing plasma-widget-translatoid plasma-widget-tvprogramme plasma-widget-weather plasma-widget-weatherforecast
  plasma-widget-wifi plasma-widget-xbar plasma-widgets-addons plasma-widgets-workspace plasmoid-quickaccess plasmoid-system-status
  plasmoid-teacooker plasmoid-toggle-compositing plasmoid-weather plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  pm-utils pokerth policykit-1 policykit-1-gnome polkit-kde-1 polly-b-gone portmap powermgmt-base ppp pppconfig pppoeconf printer-applet procps
  pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils pxljr pyrenamer
  python-gconf python-gnome2 python-imaging-tk python-kde4 python-qt4 python-tk python-webkit python-wxgtk2.8 qca-tls qemu-kvm qjackctl
  qt3-assistant qt3-designer qt3-dev-tools qt3-dev-tools-compat qt3-linguist qt3-qtconfig qt4-designer qt4-dev-tools qt4-qtconfig quassel
  recordmydesktop rss-glx rsyslog scim-bridge-client-qt scim-qtimm screen-resolution-extra scribus scummvm sdlmame skencil skype snes9express
  snes9x-x software-properties-gtk software-properties-kde soundconverter speech-dispatcher speedcrunch splix sqlitebrowser sreadahead
  stepmania4 strigi-client strigi-daemon subdownloader subtitleeditor subtitleripper sysinfo system-config-printer-common
  system-config-printer-kde systemsettings tagainijisho tagainijisho-dic-en telnet tileracer timidity tk8.5 transcode transfig
  ttf-mscorefonts-installer ubufox ubuntu-minimal ubuntu-standard udev udisks ufw update-manager-kde update-notifier-kde upstart ureadahead
  userconfig util-linux util-linux-locales vertris vlc wine1.2 winff winff-doc wireless-crda x-ttcidfont-conf x11-apps x11-common
  x11-session-utils x11-utils x11-xfs-utils x11-xkb-utils x11-xserver-utils x11proto-fixes-dev x11proto-xext-dev xbase-clients xfonts-100dpi
  xfonts-75dpi xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xine-console xine-ui xinit xorg xscreensaver-data
  xscreensaver-data-extra xscreensaver-gl xscreensaver-gl-extra xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-fbdev xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-intel
  xserver-xorg-video-mach64 xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l xserver-xorg-video-vesa
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xtightvncviewer xtrans-dev xulrunner-1.9.2 xutils yakuake yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  e2fsprogs util-linux (due to e2fsprogs) hostname upstart (due to hostname)
0 upgraded, 0 newly installed, 783 to remove and 0 not upgraded.
After this operation, 2,251MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] hell no
```

So yea... ya can't remove plymouth anymore.

Renaming or removing /etc/init/plymouth.conf pretty much keeps it from ever starting.

---

### Post by ranch hand on 2010-04-06
Ah, sounds like a plan to me.  I will try that on my ISO testing install.  It gets reinstalled this week at least once so no harm in absolutely frying it.  Renaming can't even hurt it.

I like to hear folks recommend renaming.  It is so easy to fix if it is wrong.

Thanks a bunch.  I though maybe just the splash was the main problem here but I sure could be wrong.

---

### Post by zika on 2010-04-06
**mv plymouth*.conf *.conf.backup** is one of the cheapest fixes lately... Plymouth messed up one the best tricks ever (touch /forcefsck) for quick and clean check of file-system(s)...

---

### Post by BrokeMahPC on 2010-04-06
> **jarlath said:**
> I'm getting plymouth on shutdown but darkness / console for boot. Is that what everyone else has at this stage?

I am getting the splash on startup and shutdown with the fix I found (see my post before yours, same page) but yes, also black screen plus console and brief flashes of text. I am not sure what I did is recommended though, as the devs are doing updates.

Startup - animated splash for 4 seconds, few lines white text appear over splash for an instant, black screen plus blinking cursor for 4 seconds then login screen appears.

Shutdown - animated splash for 4 seconds, black screen for 1 second, shutdown

---

### Post by QwUo173Hy on 2010-04-06
Thanks BrokeMahPC. I'll give it a little longer so, then I'll follow your footsteps :)

---

### Post by BrokeMahPC on 2010-04-06
I thought I had better type out everything I did to get Plymouth working - I was reading blogs and forum threads, changing things and keeping my fingers crossed. Maybe those more knowledgeable can comment on the validity of this?
**Please** **backup these files before editing them!**

First I set the grub 2 resolution - As I could not find anything to change the Plymouth splash screen res, I wondered if it used the resolution from the grub2 settings.

step 1 code:
sudo gedit /etc/default/grub
-remove the “#” in front of the line “*#GRUB_GFXMODE=640×480*” and  change the resolution to your screen resolution.
-save and exit

step 2 code:
sudo gedit /etc/grub.d/00_header
-edit line 103 to your resolution, it was originally640x480 on my PC.
set gfxmode=1920x1080
-add the following line underneath (this will be line 104)
set gfxpayload = keep
-line 105 reads: insmod gfxterm
-save and exit

step 3 code:
sudo update-grub
-this updates grub - now restart the computer. If you were using the open source video drivers this may solve your problems but I activated the ATI proprietary driver which did something nasty to plymouth and the boot time increased, there was much stuttering resolution changing etc and the splash looked low res, low colour and awful.

To solve the ATI proprietary driver problem I followed the steps in this Plymouth readme file:
code:
gedit /usr/share/doc/plymouth/README.Debian
-(might be useful to save a copy to your homefolder - I think we may be using this often!)

It's the bit under "High-color graphics on nVidia, ATI and other cards"
As it says this may cause issues with suspend / resume so test it for yourself. I don't use suspend so didn't have any problems after.
**Please** **backup these files before editing them!**

step 1 code:
sudo gedit /etc/default/grub
-add/replace the following video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT so it looks like this: GRUB_CMDLINE_LINUX_DEFAULT="video=vesafb"
-save and exit

step 2 code:
sudo update-grub

step 3 code:
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

step 4 code:
sudo update-initramfs -u
-restart / reboot the PC

My fast boot times were back after this and the Plymouth boot / shutdown screens were animating correctly and of a decent quality but not perfect. They were not full screen, black border around the edge. Anyone know how to solve that?

---

### Post by VMC on 2010-04-06
> **zika said:**
> **mv plymouth*.conf *.conf.backup** is one of the cheapest fixes lately... Plymouth messed up one the best tricks ever (touch /forcefsck) for quick and clean check of file-system(s)...

I think mountall is the culprit here.

---

### Post by djchandler on 2010-04-07
> **hikaricore said:**
> It didn't used to, but now nearly everything has plymouth listed as a dependency.
Personally I just removed it from /etc/init instead.  2 of my 5 systems refuse to boot with it active, there's no excuse for that.

I went back to see if Synaptic would remove a bunch of stuff last night, and lo and behold, it does, just as you posted.

[COLOR=Red]**Disclaimer: Wild speculation follows!**[/COLOR]

If it's for the purpose of branding, I get it. But this looks like it forces a dependency on what some would consider an unnecessary package (we have gotten by without it until now) to insert a registered trademark. Could that be construed as as a violation of the free and open source licenses of any of the other software packages that would be deleted where there is no actual connection, i.e., removing Plymouth artificially restricts the use of that other software? It makes me wonder. I don't want anybody getting into trouble over this, but if the package continues being troublesome, this could give Canonical a problem in more ways than one.

At the very least, this could be something that further unintentionally strains the relationship with the upstream community. Am I exaggerating this?

---

### Post by castrojo on 2010-04-07
[QUOTE=djchandler]Could that be construed as as a violation of the free and open source licenses of any the other software that would be deleted where there is no actual connection, i.e., removing Plymouth artificially restricts the use of that other software?[/QUOTE]

What?

> At the very least, this could be something that further strains the relationship with the upstream community.

This also makes no sense.

---

### Post by k3lt01 on 2010-04-07
Actually whiprush, djchandler is making perfect sense. Forcing packages onto the end user via dependencies that have never been in place before has been discussed many times on this forum. We, the end users, cannot help it if the devs etc don't visit here often to see what we think.

---

### Post by Mr. Picklesworth on 2010-04-07
> **k3lt01 said:**
> Actually whiprush, djchandler is making perfect sense. Forcing packages onto the end user via dependencies that have never been in place before has been discussed many times on this forum. We, the end users, cannot help it if the devs etc don't visit here often to see what we think.

Not really much sense being made to me, either. This sort of thing is usually a packaging-specific issue. These happen all the time. Please file a bug report (if one isn't already filed), and try not to jump to ugly conclusions :)

Granted, I'm not clued in on this lower level stuff. From the looks of it, mountall lists Plymouth as a dependency, and practically everything else (naturally) depends on mountall via a nice chain. Looks like there may be a strange circle going on somewhere, since both Plymouth and Upstart list the other as dependents (in Synaptic). Not sure if that's meant to happen — I'm a bit of a packaging newbie — but it feels funny.

In the defense of integration, that is the point of an operating system like Ubuntu; there wouldn't be much point making it if things weren't molded to fit together.

---

### Post by k3lt01 on 2010-04-07
> **Mr. Picklesworth said:**
> Not really much sense being made, actually. This sort of thing is usually a packaging-specific issue. These happen all the time. Please file a bug report (if one isn't already filed), and try not to jump to ugly conclusions.Ugly conclusions? Who's jumping here? My comment is defence of djchandler as I can see where he is coming from, in no way shape or form have I made a conclusion. Methinks Mr. Picklesworth it is thee who hath jumpethed to an ugly conclusion and shouldst probably take a step back before thee maketh another comment without knowing where the quote you are quoting cometh from.

As for filing a bug report, don't you think we have bigger fish to fry?

You do realise you may be about to get a pinch don't you.

---

### Post by NightwishFan on 2010-04-07
I hate being pinched. The advice is sound though. Misunderstanding happen, and I know we all mean well. Like was said, perhaps put your 2 cents in on any relevant bug reports. I think that plymouth will be sorted about before the release otherwise there would be no way to have an easy CLI system or to use something like usplash if desired.

---

### Post by djchandler on 2010-04-07
> **Mr. Picklesworth said:**
> Not really much sense being made, actually. This sort of thing is usually a dependency issue. These happen all the time. Please file a bug report (if one isn't already filed), and don't jump to conclusions.

Granted, I'm not clued in on this lower level stuff. It could also be caused by this component being more deeply integrated with the system, since that is the point of an operating system like Ubuntu. (If you want loose coupling, I hear Arch is fantastic!). From the looks of it, mountall is dependent on Plymouth now, and everything else (naturally) depends on it.

Some of us that have been using Ubuntu for a while have experienced similar cascades. I didn't think if it as a bug so much as there were perhaps underlying dependencies I wasn't aware of. Removing Evolution used to cause the Ubuntu Desktop to get removed. I've encountered other such situations as well, although no other one quite as memorable. Fortunately I stopped myself before borking my system. I never knew why it would and just accepted Evolution was going to be on my computer whether I used it or not.

Since this is a "bug" we've seen before, and it seemed intentional or unavoidable before, it's difficult to differentiate this bug from a feature. [See this post where]("http://ubuntuforums.org/showpost.php?p=9078434&postcount=6") somebody did strip the GUI from the system by trying to alter Plymouth. From what I can tell, (s)he wasn't trying to remove it, just add a theme from the repository.

Thanks for the explanation, Mr. Picklesworth. I had not seen where mountmanager has a dependency to Plymouth now. Is it a bug or feature? Apparently it was only recently introduced. So is the bug/feature in mountmanager or plymouth? Since I don't know that, I will leave that to you.
:confused:
As for the part about leaping to conclusions, I would classify my post as wild speculation. I'll put such a disclaimer on the front end.

---

### Post by hikaricore on 2010-04-07
It's really easy to sweep this under the rug with rubbish about people not making sense but it is hardly the way to handle it.

Lets look at the facts:

1. Plymouth is causing many users to be unable to boot AT ALL.
2. Previous solutions revovled around removing plymouth, this worked.
3. Recently everything has become a dependancy of a process which only acts as a visual boot screen for a few seconds at startup.

This is the point that is being made and it makes perfect sense.
Bug reports have been filed many many times on plymouth, most of them are closed as solved when they are not, the others are still open with varying low levels of importance.

---

### Post by NightwishFan on 2010-04-07
Ubuntu Desktop is just a metapackage. It can be safely removed. The only exception is if you installed it with aptitude. Then just uncheck "Automatically Installed" for anything that is tried to be removed. Then it is fine.

---

### Post by k3lt01 on 2010-04-07
> **NightwishFan said:**
> Ubuntu Desktop is just a metapackage. It can be safely removed. The only exception is if you installed it with aptitude. Then just uncheck "Automatically Installed" for anything that is tried to be removed. Then it is fine.And it is for this reason when a new release comes out I do a minimal install and choose what I want on it. If I can get away without having Plymouth it wont get on my machines when 10.04 is finally released.

---

### Post by djchandler on 2010-04-07
> **whiprush said:**
> What? This also makes no sense.

It might to someone with an appetite for frivolous litigation. It's best to avoid those types.

See [this post]("http://ubuntuforums.org/showpost.php?p=9078434&postcount=6") if you want to get an idea of how much trouble this could cause to the end-user.

---

### Post by k3lt01 on 2010-04-07
> **djchandler said:**
> It might to someone with an appetite for frivolous litigation. It's best to avoid those types.Lol, now I know why we are friends :popcorn:

To those gentlemen who think this is just bluster, the point is it does make sense and the situation is causing people some problems. I myself am lucky as plymouth has never caused me any real issues but others have had nothing but difficulty. I personally can see their point, maybe I'm just a very perceptive person I don't know, while people like yourselves obviously can't. Neither situation is a problem, what is a problem is putting others down for pointing out their thoughts when they are quite relevant to the discussion at hand.

---

### Post by Mr. Picklesworth on 2010-04-07
> **hikaricore said:**
> It's really easy to sweep this under the rug with rubbish about people not making sense but it is hardly the way to handle it.

Lets look at the facts:

1. Plymouth is causing many users to be unable to boot AT ALL.
2. Previous solutions revovled around removing plymouth, this worked.
3. Recently everything has become a dependancy of a process which only acts as a visual boot screen for a few seconds at startup.

This is the point that is being made and it makes perfect sense.
Bug reports have been filed many many times on plymouth, most of them are closed as solved when they are not, the others are still open with varying low levels of importance.

I'm not "sweeping anything under the rug." (Thankfully I don't believe I, or anyone *at all* involved in the Ubuntu project, have the posture to do that. Hopefully I never will; that would be scary). My point about "not making sense" was, in more words, "that speculation we were momentarily discussing doesn't make sense to me." On that topic, thanks for fixing it, djchandler; hopefully it'll cure the near-derailment I've caused :)

I am quite content with your list of facts. It's a solid one. Carry on!


Just to be clear, everything does not have a dependency on Plymouth; everything is (logically) dependent on some low level package which Depends on Plymouth and probably should only Recommend it or something.

Has the inability to remove Plymouth appeared recently?
(I'm poking through Mountall's changes right now; last update is just six days old. There is probably an easier way to figure out which package is at fault for these kinds of things. Anyone?).

---

### Post by cariboo on 2010-04-07
@djchandler

The post you linked to looks like it was more user error, than dependencies that caused many packages to be uninstalled. Just look at the timing.

plymouth-theme-solar installation started at 19:42:00 and finished at 19:42:19

The package removal started at 19:44:37 and errored out at 19:49:08.

That looks like two separate operations to me

---

### Post by djchandler on 2010-04-07
> **Mr. Picklesworth said:**
> I'm not "sweeping anything under the rug." (I don't believe I, or anyone *at all* involved in the Ubuntu project, have the posture to do that). My point about "not making sense" was, in more words, "that conspiracy theory we were momentarily discussing doesn't make sense." On that topic, thanks for fixing it, djchandler; hopefully it'll cure the near-derailment I've caused :)

I am quite content with your list of facts. Carry on.

Just to be clear, everything does not have a dependency on Plymouth; everything is (logically) dependent on some system component which Depends on Plymouth and probably should only Recommend it.

Has the inability to remove Plymouth appeared recently?
(I'm poking through Mountall's changes right now; last update is just six days old).

I'll share the blame. If you get into any trouble, point the "pickled" finger of fate at me.:)

---

### Post by hikaricore on 2010-04-07
Within the last week or so I'd say.  I had it removed on my media server and noticed after an update it had reinstalled.
Upon removal attempts to be able to boot again next time I found that it wanted to take out my whole installation.  :p
I do understand that everything is not dependant on it but things that are dependant on things are dependant on it, so the case ends up with everything being removed no matter what the exacpt specifics. ^_^
Would be a horrible thing for this to still be as such on release day unless the bugs with plymouth, mountall, or whatever is causing the black screen of death are fixed.

---

### Post by Mr. Picklesworth on 2010-04-07
Okay, here you go! Synaptic was indeed trying to tell us something.

lp:ubuntu/mountall, revision 294 (released a week ago)

```

Revision:
294 revid:scott@netsplit.com-20100331182618-c27th36r7cwe8g27
Parents:
&#65532;293: Flush the plymouth connection before closing it and exiting…
Children:
&#65532;295: Don't start a maintenance shell - if plymouth is not runnin…
Date:
10-03-31 11:26 AM
Committer:
Scott James Remnant <scott@netsplit.com>
Branch:
mountall

* Add hard dependency on Plymouth; without it running, mountall will
  ignore any filesystem which doesn't show up within a few seconds or that
  fails to fsck or mount. If you don't want graphical splash, you simply
  need not install themes.
```

```


=== modified file debian/control
--- debian/control	2010-03-31 18:24:33 +0000
+++ debian/control	2010-03-31 18:26:18 +0000
@@ -1,16 +1,16 @@
 Source: mountall
 Section: admin
 Priority: required
 Maintainer: Scott James Remnant <scott@ubuntu.com>
 Standards-Version: 3.8.0.0
 Build-Depends: debhelper (>= 7.3.15ubuntu2~boot7), pkg-config (>= 0.22), libnih-dev (>= 1.0.0), libnih-dbus-dev (>= 1.0.0), nih-dbus-tool (>= 1.0.0), libdbus-1-dev (>= 1.2.16), libexpat1-dev (>= 2.0.0), libudev-dev (>= 146), libplymouth-dev (>= 0.8.1-3)
 
 Package: mountall
 Architecture: any
-Depends: makedev, udev, coreutils (>= 7.1), ${shlibs:Depends}, ${misc:Depends}
+Depends: makedev, udev, plymouth, coreutils (>= 7.1), ${shlibs:Depends}, ${misc:Depends}
 Replaces: upstart (<< 0.6.3-2)
 Breaks: usplash (<< 0.5.47), policycoreutils (<< 2.0.69-2ubuntu4)
 Description: filesystem mounting tool
  mountall mounts filesystems when the underlying block devices are
  ready, or when network interfaces come up, checking the filesystems
  first.

```

Full changelog for the release: [https://edge.launchpad.net/ubuntu/+source/mountall/2.10](https://edge.launchpad.net/ubuntu/+source/mountall/2.10)

---

### Post by djchandler on 2010-04-07
> **cariboo907 said:**
> @djchandler

The post you linked to looks like it was more user error, than dependencies that caused many packages to be uninstalled. Just look at the timing.

plymouth-theme-solar installation started at 19:42:00 and finished at 19:42:19

The package removal started at 19:44:37 and errored out at 19:49:08.

That looks like two separate operations to me

The OP admitted PEBKAC. Something odd happened obviously. But it having happened as it did, it certainly makes me wonder how.

Somebody maybe ought to check my last post in that thread and see if I muddied the waters.

---

### Post by djchandler on 2010-04-07
> **Mr. Picklesworth said:**
> Okay, here you go! Synaptic was indeed trying to tell us something.

lp:ubuntu/mountall, revision 294

```

Revision:
294 revid:scott@netsplit.com-20100331182618-c27th36r7cwe8g27
Parents:
&#65532;293: Flush the plymouth connection before closing it and exiting&#8230;
Children:
&#65532;295: Don't start a maintenance shell - if plymouth is not runnin&#8230;
Date:
10-03-31 11:26 AM
Committer:
Scott James Remnant <scott@netsplit.com>
Branch:
mountall

* Add hard dependency on Plymouth; without it running, mountall will
  ignore any filesystem which doesn't show up within a few seconds or that
  fails to fsck or mount. If you don't want graphical splash, you simply
  need not install themes.
``````


=== modified file debian/control
--- debian/control    2010-03-31 18:24:33 +0000
+++ debian/control    2010-03-31 18:26:18 +0000
@@ -1,16 +1,16 @@
 Source: mountall
 Section: admin
 Priority: required
 Maintainer: Scott James Remnant <scott@ubuntu.com>
 Standards-Version: 3.8.0.0
 Build-Depends: debhelper (>= 7.3.15ubuntu2~boot7), pkg-config (>= 0.22), libnih-dev (>= 1.0.0), libnih-dbus-dev (>= 1.0.0), nih-dbus-tool (>= 1.0.0), libdbus-1-dev (>= 1.2.16), libexpat1-dev (>= 2.0.0), libudev-dev (>= 146), libplymouth-dev (>= 0.8.1-3)
 
 Package: mountall
 Architecture: any
-Depends: makedev, udev, coreutils (>= 7.1), ${shlibs:Depends}, ${misc:Depends}
+Depends: makedev, udev, plymouth, coreutils (>= 7.1), ${shlibs:Depends}, ${misc:Depends}
 Replaces: upstart (<< 0.6.3-2)
 Breaks: usplash (<< 0.5.47), policycoreutils (<< 2.0.69-2ubuntu4)
 Description: filesystem mounting tool
  mountall mounts filesystems when the underlying block devices are
  ready, or when network interfaces come up, checking the filesystems
  first.

```Full changelog for the release: [https://edge.launchpad.net/ubuntu/+source/mountall/2.10](https://edge.launchpad.net/ubuntu/+source/mountall/2.10)

Thank you Mr. Picklesworth! I wonder if un-installing all the themes will speed or slow boot times.

Time for yet another experiment! I guess you have to be having fun doing this or we wouldn't be doing this.

**REBOOT!**

And removing *all* the themes works, even the text theme. The screen goes from GRUB2 to black to the log-in screen.

The screens are gorgeous when it works right. But it's being stubborn about getting along with the ATI fglrx driver. How is that possible? Because reverting back to the Radeon xorg driver makes it work properly.

I have bootchart installed. I'll post where folks are posting their boot times and charts.

---

### Post by ranch hand on 2010-04-07
Well, I think that perhaps we should cool down just a tad.

Yes,  I think plymouth is a large mistake.  Yes, I think the reason we are using it is because Fedora uses it (badly) so it must be great.  Yes, I tend to think it is the root of all boot problem.

The last has the base of experience.

I do not think there is a conspiracy.  It is easy to understand the feeling though.

If you have had nothing but escalating problems booting and modifying or removing plymouth has helped and the only visible sign that anything is being done is to see your work arounds dismantled.  Well, maybe the world is out to get you.

I know that plymouth does not like my box.  Out of 7 variations of 10.04 on here 5 are very similar, certainly enough so that booting should be consistent.  It in no way is.  One gets fsck  run every time I boot.  Removing plymouth fixed this which is good because boot freezes on all 5 if fsck is run (ah ha there is consistency).  On another fsck is run every 54th mount.

Yes a conspiracy is easy to dream up.

Bull headed sticking to a buggy dog is what I think is going on here and I understand that.  I am very good at being bull headed too.

I have come to believe that this will never work on all hardware and a large plurality of users are going to NEED to be able to disable or better yet remove this easily or be forced to use a different version of Ubuntu that does not have plymouth or look for some distro without it.

Seeing that we are here testing probably indicates a certain fondness for Ubuntu.  Having it look like we are being forced to buy new boxes or switch does not leave a good taste in the mouth.

Being in Montana I could say that the problem is that too many devs are from "back east" (if you go far enough everywhere is back east).  Worse yet some of them may be Canadian (sick attempt at humor).

I think the problem is simply following a plan that has proven itself bad.  It is too late to do any thing about this now so we are stuck for the ride.

Rather than scream at each other I think we better figure out how to salvage what we can of an otherwise very fine OS.  If you can't boot it just isn't any good.

---

### Post by ranch hand on 2010-04-07
> **hikaricore said:**
> It's really easy to sweep this under the rug with rubbish about people not making sense but it is hardly the way to handle it.

Lets look at the facts:

1. Plymouth is causing many users to be unable to boot AT ALL.
2. Previous solutions revovled around removing plymouth, this worked.
3. Recently everything has become a dependancy of a process which only acts as a visual boot screen for a few seconds at startup.

This is the point that is being made and it makes perfect sense.
Bug reports have been filed many many times on plymouth, most of them are closed as solved when they are not, the others are still open with varying low levels of importance.
I think that separating the themes is an attempt to salvage this.  I do know that I have them on some and not on others.

The ones with out the themes do work less badly.

The dependencies are really a mystery to me.  I think the most likely thing is that they need to be tied together to get plymouth to work this well.  This strikes me as being very silly.  Kind of like building an idiot dead fall.

That is a dead fall you build and then walk under it to see if it works.

---

### Post by djchandler on 2010-04-07
> **ranch hand said:**
> Well, I think that perhaps we should cool down just a tad.
<snip>
Being in Montana I could say that the problem is that too many devs are from "back east" (if you go far enough everywhere is back east).
<snip>

So is Kansas too far east?

My take is that the deadline is fast approaching for the RC and the Final all to soon. Consequently, in order to create some cohesion, people may be taking taking shortcuts.

It's just human nature to want to take a way that seems easier. Being out west (I've spent a lot of time in the Rockies and Great Basin, but to the south in Wyoming and Utah) Ranch Hand and I know all too well that taking a shortcut can have disastrous consequences, especially if you make your living outdoors. Do it in the winter and your life could be on the line.

You'll excuse me if I wax melodramatic I hope. But I want to point out that the community would be better served in the long run if the long way were taken and this gets completely sorted out before the final release. While having goals and deadlines are good in principle, it doesn't do much good if you don't get where you planned to go.

The history of the American West is full of such [stories where a shortcut ended in disaster]("http://en.wikipedia.org/wiki/Donner_Party"). We certainly don't want to be at each others' throats--that makes things harder than they need to be. A dangerous job has taught me that being in a hurry can sometimes land you almost anywhere but where you intended.

---

### Post by k3lt01 on 2010-04-07
So what's involved in delaying 10.04 to 10.06 like Dapper was delayed from 6.04 to 6.06 to make it a better release? It's obvious Plymouth could quite possibly be the one thing that really puts a damper on what is an otherwise excellent release.

It could be seen to be unfair to those who help noobs migrate from Windows, Mac or even another version of Linux that doesn't use Plymouth only to find their hardware is not compatible without some major reworking of settings just to get it to boot efficiently let alone have a pretty splash screen. Then you have professionals who have to be seen to be suggesting the best options to their customer base, will they suggest a distribution with Plymouth when they know half the time it may cause boot issues of some sort. What about customers who have been told about this brilliant system called Ubuntu, and yes it is brilliant, only to find the very 1st thing they see (or don't see) on boot up may work on one machine but cause endless grief on another similar or even identical machine?

I know these are just hypothetical scenarios, but if you look through this thread and other things on Plymouth they are quite valid scenarios that deserve serious consideration by those who are making the upper level decisions. Testers are used to having problems, the general public etc expect things to work with a minimum of fuss.

---

### Post by teh603 on 2010-04-07
I'm beginning to think the whole switch to Plymouth was an attempt to beat on nVidia to make a better driver. Which has obviously failed since nV has removed their open source driver. Nouveau isn't ready for release yet, and probably won't for a very long time.

Sometimes people like having 3D accelleration. There are some decent games out there for Linux, y'know. All it takes is one smart sheep to figure out a business model that can still make money off free software.

I got the business model, but I don't quite qualify as a smart sheep. ](*,)

---

### Post by vredley on 2010-04-07
Plymouth is a disaster. It doesn't work properly on my Eee PC with integrated Intel graphics, so I can imagine what it must be like for people using proprietary drivers.

This has to be be fixed before release, and I can't see that happening in the next three weeks. I really hope I'm proved wrong.

---

### Post by MacUntu on 2010-04-07
> **vredley said:**
> so I can imagine what it must be like for people using proprietary drivers

Working fine, thanks! :KS

---

### Post by cyberkilla on 2010-04-07
> **MacUntu said:**
> Working fine, thanks! :KS

Mine looks awful with the nVidia proprietary driver. I've tried Nouveau, which works, but I need 3D for my work.

Will it ever look good, or am I going to have to endure a 16 colour rendition of the splash screen every time I boot my computer?

Is there a splash theme that is basically a black screen with a string in the top-left saying "Loading Ubuntu..." ? That would be a nicer fallback than a broken-looking 16 colour image.

---

### Post by mc4man on 2010-04-07
> Will it ever look good,
I gather you can change to vesa for a better 'look', I haven't bothered for the several seconds it shows.
( though decided to just use 'ubuntu_logo' theme and rescale the various .png's so they *appear* to look better, sharper, ect.
( for a 23" hd screen - ubuntu_logo @ 83x22, on, off dots @ 9x9, darker background

---

### Post by seenthelite on 2010-04-07
> **macuntu said:**
> working fine, thanks! :ks

+1

---

### Post by vredley on 2010-04-07
You lucky dogs. ;) All I get is:

sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] Assuming drive cache: write through

...followed by something about bytes and a broken pipe.

Can I have a simple black screen, please? :p

---

### Post by cheapsaket on 2010-04-07
I am using the ATI fglrx driver and since the update I did on 4/5, Plymouth has somehow been working for me with the nice font and graphic and its the correct size.
I thought I was imagining things and double checked to see if I was using fglrx and whether the module was loaded so I checked using dmesg and lsmod and fglrx was indeed loaded.
I thought that this was not something possible? Does anyone have a similar experience?

---

### Post by BrokeMahPC on 2010-04-07
Not sure if this has any bearing on the matter as I'm not exactly sure what a dependency is, just after Beta1 was released I had a strange experience with synaptic.

I was installing something - could have been hpijs, hpijs-ppds or hplip or even something else like xsane. The odd thing was synaptic wanted to install gimp and a host of other things along with it????? 
Now I definitely had only selected 1 item for install and synaptic was acting like like this install of this item depended on the install of gimp plus a host of other things. I thought it must be a mistake, shut down synaptic and tried again with the same result.

I installed anyway and sure enough I now have gimp plus who knows what else. Don't know how the repositories work and I now wish I had made some notes about this and taken it more seriously at the time.

Are the Ubuntu gods sure everything is ok with synaptic and the repos and is plymouth / themes installing other things it shouldn't, or not installing things it should?

---

### Post by wnelson on 2010-04-07
This is how I got Ubuntu to boot for me.

Added vga=792 GRUB_CMDLINE_LINUX into /etc/default/grub
#update-grub -u

commented out vesafb in blacklist-framebuffer.conf so it would load

created the file
echo FRAMEBUFFER=y | sudo tee  /etc/initramfs-tools/conf.d/splash
#update-initramfs


Rebooted and it worked

---

### Post by castrojo on 2010-04-07
> **hikaricore said:**
> It's really easy to sweep this under the rug with rubbish about people not making sense but it is hardly the way to handle it.

No one is sweeping anything under any rug. There's a difference between Plymouth being broken and it's dependency being a "violation of the free and open source licenses", which is what I was talking about.

[QUOTES]This is the point that is being made and it makes perfect sense.
Bug reports have been filed many many times on plymouth, most of them are closed as solved when they are not, the others are still open with varying low levels of importance.[/QUOTE]

Do you have any specific examples?

---

### Post by castrojo on 2010-04-07
On a related note, I wonder where all the people from the 50 page thread from last cycle talking about how great Plymouth was and how it would solve world hunger and how Ubuntu was lame for not including it 6 months ago...

---

### Post by ranch hand on 2010-04-07
Yes I would love to hear how great their experience is with this great addition too.

Now all we need is packagekit to make things even better.

Hey, dogs love company.

---

### Post by zika on 2010-04-07
> **ranch hand said:**
> Hey, dogs love company.I know I'm a happy dog after```
sudo mv /etc/init/plymouth-log.conf /etc/init/plymouth-log.conf.backup
sudo mv /etc/init/plymouth-splash.conf /etc/init/plymouth-splash.conf.backup
sudo mv /etc/init/plymouth-stop.conf /etc/init/plymouth-stop.conf.backup
sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.backup
```... I'm the one that, even, did not have great troubles with Plymouth. Only with fsck, to be honest. The rest was cosmetics...

---

### Post by ranch hand on 2010-04-07
I am chicken.  I am only renaming one at a time and trying it for a while.  The splash conf file seems to help so I am going to try it here on my main install and see what happens here.

---

### Post by zika on 2010-04-07
> **ranch hand said:**
> I am chicken.  I am only renaming one at a time and trying it for a while.  The splash conf file seems to help so I am going to try it here on my main install and see what happens here.Working with lumber and on a ranch, I could call You anything **but** a chicken... :) Parsing through woods of GRUB, I could call You anything **but** a chicken... :) You're just modest, and, suddenly, cautious... :)

---

### Post by djchandler on 2010-04-07
> **cheapsaket said:**
> I am using the ATI fglrx driver and since the update I did on 4/5, Plymouth has somehow been working for me with the nice font and graphic and its the correct size.
I thought I was imagining things and double checked to see if I was using fglrx and whether the module was loaded so I checked using dmesg and lsmod and fglrx was indeed loaded.
I thought that this was not something possible? Does anyone have a similar experience?
Not similar, and fairly negative.

Interesting, I see in your signature that you are avoiding the backfill patch. I'm using fglrx too, but even with themes disabled, I'm getting garbage on the screen between GRUB2 and the log-in screen and then again on shutdown.

I'm getting overheating while watching video on this laptop. The power abruptly powered off, which is a BIOS safety feature. This also happens with the xorg radeon driver.

My laptop has a Radeon 3100 IGP on AMD 780V northbridge.

---

### Post by emarkay on 2010-04-07
> **whiprush said:**
> On a related note, I wonder where all the people from the 50 page thread from last cycle talking about how great Plymouth was and how it would solve world hunger and how Ubuntu was lame for not including it 6 months ago...

So again, and referencing an "official's" post - with an attitude like that I am surprised we aren't all still using Win 98Se. 

Come on, there are serious problems with this thing, for 2 seconds of booting and for some supposed "other still secret" purpose deep down in the OS.

Why doesn't this just "work" like the way things work Karmic, and why are so many qualified and intelligent testers still having issues with it.  Maybe Beta2 has some surprises (naw...) or maybe there's something being held back for RC, but remember, this is an LTS - it must be stable for all for years... (again,* for all, for years..*.)

---

### Post by VMC on 2010-04-07
> **emarkay said:**
> .. but remember, this is an LTS - it must be stable for all for years... (again,* for all, for years..*.)
Not LT-Stable but LT-Supported for three years. Its Long Term **Support**.

Granted plymouth has its share of issues, but not all things point to plymouth. Even though they appear so. I have a bug opened that appears to be plymouth related but it looks like mountall is to blame.

---

### Post by ranch hand on 2010-04-08
> **zika said:**
> Working with lumber and on a ranch, I could call You anything **but** a chicken... :) Parsing through woods of GRUB, I could call You anything **but** a chicken... :) You're just modest, and, suddenly, cautious... :)
Well, just for that I tried it on a throw away OS and it really sucks!

No real bad  messages and according to bootchart that I installed after the first boot (which I think was faster) it booted in 30.94 seconds on my USB external enclosure and password login.

The boot that I got the chart on included an fsck so I think I will reboot and try it again.

EDIT

Nope the fsck last time was just checking to see if it needed to run (I think).  It ran this time and was 2 seconds slower.  I have had one boot faster (29.something).  It did not freeze running the fsck either.

I will not be doing this to other installs, probably, but you can be sure that when I get the final it will be done.  Had the big black flasher for several seconds at the start but then everything was fast and smooth.

I may finish doing this to the install I use the most.  Half way there now.  Each one renamed seems to make it work less badly.  Doing all of them seems to give a pretty decent result.

It is all your fault, zika, that I am abusing this poor innocent OS this way.  It only boots about 20 to 25 seconds faster than the norm this way.  Probably a bad idea.  

A>Fedora uses plymouth.
B>Fedora=Good
C>Therefore plymouth=good
D>Therefore removing plymouth=bad

So there.

---

### Post by Jordanwb on 2010-04-11
How would I go about changing the theme that plymouth uses?

---

### Post by grandtoubab on 2010-04-11
> **ranch hand said:**
> Well, just for that I tried it on a throw away OS and it really sucks!

No real bad  messages and according to bootchart that I installed after the first boot (which I think was faster) it booted in 30.94 seconds on my USB external enclosure and password login.

The boot that I got the chart on included an fsck so I think I will reboot and try it again.

EDIT

Nope the fsck last time was just checking to see if it needed to run (I think).  It ran this time and was 2 seconds slower.  I have had one boot faster (29.something).  It did not freeze running the fsck either.

I will not be doing this to other installs, probably, but you can be sure that when I get the final it will be done.  Had the big black flasher for several seconds at the start but then everything was fast and smooth.

I may finish doing this to the install I use the most.  Half way there now.  Each one renamed seems to make it work less badly.  Doing all of them seems to give a pretty decent result.

It is all your fault, zika, that I am abusing this poor innocent OS this way.  It only boots about 20 to 25 seconds faster than the norm this way.  Probably a bad idea.  

A>Fedora uses plymouth.
B>Fedora=Good
C>Therefore plymouth=good
D>Therefore removing plymouth=bad

So there.
cheap apples are rare
what is rare is expensive
cheap apples are expensives
:lolflag:

---

### Post by AClark on 2010-04-11
> **Jordanwb said:**
> How would I go about changing the theme that plymouth uses?

```
sudo update-alternatives --config default.plymouth
```
Gives you a dialog to change the theme.

More themes are in Synaptic - just search for plymouth

```
sudo update-initramfs -u
```
needed after the change

Documented in /usr/share/doc/plymouth/README.debian

---

### Post by cyberkilla on 2010-04-11
[COLOR="Gray"]I just used update alternatives to change it to the default text.plymouth (which I installed from the repository).

It gives me a blue bar which isn't too jarring a change from GRUB, then KDM loads. vga16fb issue completely side-stepped.
[/COLOR]

EDIT: Strike that, I've reverted to the default. It's still a seemingly pointless exercise. It only appears for a brief instant and crashes once I log into my account.:P

---

### Post by ASULutzy on 2010-04-13
Could use some help, not sure if my tty's were busted before or after I fiddled, but either way my plymouth boot splash looks worse than ever and all my tty's are hosed up.

I have a Geforce 360M, using Nvidia's 195.36.15 driver version as reported by Nvidia X Server Settings.

/etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash quiet vga=769"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```


/etc/grub.d/00_header
```
#! /bin/sh -e

# grub-mkconfig helper script.
# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
#
# GRUB is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# GRUB is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.

transform="s,x,x,"

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
grub_prefix=`echo /boot/grub | sed ${transform}`
locale_dir=`echo /boot/grub/locale | sed ${transform}`
grub_lang=`echo $LANG | cut -d _ -f 1`

. ${libdir}/grub/grub-mkconfig_lib

# Do this as early as possible, since other commands might depend on it.
# (e.g. the `loadfont' command might need lvm or raid modules)
for i in ${GRUB_PRELOAD_MODULES} ; do
  echo "insmod $i"
done

if [ "x${GRUB_DEFAULT}" = "x" ] ; then GRUB_DEFAULT=0 ; fi
if [ "x${GRUB_DEFAULT}" = "xsaved" ] ; then GRUB_DEFAULT='${saved_entry}' ; fi
if [ "x${GRUB_TIMEOUT}" = "x" ] ; then GRUB_TIMEOUT=5 ; fi
if [ "x${GRUB_GFXMODE}" = "x" ] ; then GRUB_GFXMODE=640x480 ; fi

cat << EOF
if [ -s \$prefix/grubenv ]; then
  load_env
fi
set default="${GRUB_DEFAULT}"
if [ \${prev_saved_entry} ]; then
  set saved_entry=\${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z \${boot_once} ]; then
    saved_entry=\${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n \${have_grubenv} ]; then if [ -z \${boot_once} ]; then save_env recordfail; fi; fi
}
EOF

case ${GRUB_TERMINAL_INPUT}:${GRUB_TERMINAL_OUTPUT} in
  serial:* | *:serial)
    if ! test -e ${grub_prefix}/serial.mod ; then
      echo "Serial terminal not available on this platform." >&2 ; exit 1
    fi

    if [ "x${GRUB_SERIAL_COMMAND}" = "x" ] ; then
      grub_warn "Requested serial terminal but GRUB_SERIAL_COMMAND is unspecified. Default parameters will be used."
      GRUB_SERIAL_COMMAND=serial
    fi
    echo "${GRUB_SERIAL_COMMAND}"
  ;;
esac

case x${GRUB_TERMINAL_INPUT} in
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_input ${GRUB_TERMINAL_INPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal ${GRUB_TERMINAL_INPUT}
fi
EOF
  ;;
esac

case x${GRUB_TERMINAL_OUTPUT} in
 xgfxterm)
    # Make the font accessible
    prepare_grub_to_access_device `${grub_probe} --target=device ${GRUB_FONT_PATH}`

    cat << EOF
if loadfont `make_system_path_relative_to_its_root ${GRUB_FONT_PATH}` ; then
set gfxmode=${GRUB_GFXMODE}
  insmod gfxterm
  insmod ${GRUB_VIDEO_BACKEND}
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
EOF
if [ x$GRUB_THEME != x ] && [ -f $GRUB_THEME ] \
	&& is_path_readable_by_grub $GRUB_THEME; then
    echo "Found theme: $GRUB_THEME" >&2
    prepare_grub_to_access_device `${grub_probe} --target=device $GRUB_THEME` | sed -e "s/^/  /"
    cat << EOF
  insmod gfxmenu
  set theme=(\$root)`make_system_path_relative_to_its_root $GRUB_THEME`
  set menuviewer=gfxmenu
EOF
fi
    cat << EOF
fi
EOF
  ;;
  x)
    # Just use the native terminal
  ;;
  x*)
    cat << EOF
if terminal_output ${GRUB_TERMINAL_OUTPUT} ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal ${GRUB_TERMINAL_OUTPUT}
fi
EOF
  ;;
esac

# Gettext variables and module
if [ "x${LANG}" != "xC" ] ; then
    prepare_grub_to_access_device $(${grub_probe} --target=device ${locale_dir})
  cat << EOF
set locale_dir=(\$root)$(make_system_path_relative_to_its_root ${locale_dir})
set lang=${grub_lang}
insmod gettext
EOF
fi

cat << EOF
if [ \${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=${GRUB_TIMEOUT}
fi
EOF

# Play an initial tune
if [ "x${GRUB_INIT_TUNE}" != "x" ] ; then
  cat << EOF
insmod play
play ${GRUB_INIT_TUNE}
EOF
fi
```

I also installed startupmanager at some point and tried to fiddle using that, so not sure what all that could have busted. I'd really like to avoid having to reinstall, so any help on at least getting my tty's back would be greatly appreciated.
Ideally I'd get a pretty plymouth boot screen AND my tty's, but I figure functionality >> all, so thanks in advance for your help!:P

---

### Post by Jordanwb on 2010-04-13
> **AClark said:**
> ```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u
```


Thanks.

---

### Post by Starks on 2010-04-13
I guess that this won't be fixed. I recall it being tracked for Beta 2 at one point.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)

---

### Post by Half-Left on 2010-04-13
Is there any reason why Canonical are having issues with Plymouth so much?

Fedora have the splash screen graphics and animation showing just fine, even with the NVIDIA binary driver on their alpha. Maybe they can help you with it? :)

---

### Post by philinux on 2010-04-13
I get a black screen with a flashing cursor top left for what seems ages. Plymouth starts and lasts for at most 2 or 3 seconds. Hardly worth it.

---

### Post by Half-Left on 2010-04-13
> **philinux said:**
> I get a black screen with a flashing cursor top left for what seems ages. Plymouth starts and lasts for at most 2 or 3 seconds. Hardly worth it.

The whole idea is for the splash and animation to start just after grub. The switching seems to actually delay the boot because the framebuffer and splash seem to use different resolutions, plus xorg starting.

Nouveau driver is all nice and smooth of course, thanks to the KMS.

---

### Post by ranch hand on 2010-04-13
> **Half-Left said:**
> Is there any reason why Canonical are having issues with Plymouth so much?

Fedora have the splash screen graphics and animation showing just fine, even with the NVIDIA binary driver on their alpha. Maybe they can help you with it? :)
I think that the Ubuntu devs are having a problem because they are trying to get this dog to work for everyone.

The fedora splash does not now, nor ever has, worked on this box from when they started using plymouth.

In my line of work we do a lot of fence repair.  If you have good corners built it is amazing what you can get away with in between them.  The fence will hold up bad posts.

With bad corners you can replace everything in between the corners, posts and wire, and what you will have is an expensive, loose fence that critters walk through.

What folks need to realize is that plymouth does not have good corners and the attempts to fix it are just that.  Attempts.

Some times you just need to jack it up and back a new one under it.

---

### Post by Half-Left on 2010-04-13
> **ranch hand said:**
> I think that the Ubuntu devs are having a problem because they are trying to get this dog to work for everyone.

The fedora splash does not now, nor ever has, worked on this box from when they started using plymouth.

In my line of work we do a lot of fence repair.  If you have good corners built it is amazing what you can get away with in between them.  The fence will hold up bad posts.

With bad corners you can replace everything in between the corners, posts and wire, and what you will have is an expensive, loose fence that critters walk through.

What folks need to realize is that plymouth does not have good corners and the attempts to fix it are just that.  Attempts.

Some times you just need to jack it up and back a new one under it.


Everyone? From what I've gathered it doesn't work well for that many here, so it's in a worse state.

In Fedora is worked just fine when using vga=795 back in even Fedora 12, so I'm not sure who "everyone" is.

---

### Post by meborc on 2010-04-13
> **Half-Left said:**
> Everyone? From what I've gathered it doesn't work well for that many here, so it's in a worse state.

In Fedora is worked just fine when using vga=795 back in even Fedora 12, so I'm not sure who "everyone" is.

it works fine... as long as you use nouveau drivers :) so you can't say it does not work for everyone

---

### Post by Half-Left on 2010-04-13
> **meborc said:**
> it works fine... as long as you use nouveau drivers :) so you can't say it does not work for everyone

haha, well in the real world, most people will want to use the proprietary driver with 3D support, which will then screw up the nice splash screen.

I suspect that the next release will fix it, just like all the other bugs. :p

---

### Post by uBeer on 2010-04-13
> **Half-Left said:**
> The whole idea is for the splash and animation to start just after grub. The switching seems to actually delay the boot because the framebuffer and splash seem to use different resolutions, plus xorg starting.

Nouveau driver is all nice and smooth of course, thanks to the KMS.

Well, the first few boots it did work out nice with nouveau, but now I have the blinking cursor as well for a few seconds after which plymouth kicks in for 1 second and then my desktop displays.

So there is still something not quite right...

---

### Post by ranch hand on 2010-04-13
> **meborc said:**
> it works fine... as long as you use nouveau drivers :) so you can't say it does not work for everyone
Some how, this is a shock, the nouveau driver just does not seem to work well on my ATI card.

---

### Post by ratcheer on 2010-04-13
> **Half-Left said:**
> Everyone? From what I've gathered it doesn't work well for that many here, so it's in a worse state.



It doesn't really bother me one way or the other. I get an ugly low-res plymouth splash. So what? My machine boots and it boots fast. Usually about 17 seconds from making my selection in grub until the desktop login dialog.

What ***is*** bothering me is the 32 seconds Lucid is taking between when I enter my password and the desktop becomes usable. It shows me the default background during this time with no controls or panels. When it is finally ready, my chosen background is displayed along with the top and bottom panels. It is reminding me of Windows XP, a lot. :(

Tim

---

### Post by Half-Left on 2010-04-13
> **ranch hand said:**
> Some how, this is a shock, the nouveau driver just does not seem to work well on my ATI card.

That's because it only supports NVIDIA GPUs or are you being sarcastic? :)

---

### Post by sgage on 2010-04-13
He was being sarcastic.

Anyway, yes, plymouth works fine with the nouveau drivers. For my needs, the nouveau drivers work fine (at least at the xorg-edgers version), EXCEPT... they don't allow a resume from sleep. 

The nvidia drivers work great in all respects, and with the /etc/defaults/grub, /etc/grub.d/00_headers tweak work just fine with plymouth.

My machine boots nice and quickly, as well - 18 seconds from grub to desktop.

There are just so many hardware permutations out there - it must be hell trying to nail this sort of thing down.

---

### Post by teh603 on 2010-04-13
> **Half-Left said:**
> haha, well in the real world, most people will want to use the proprietary driver with 3D support, which will then screw up the nice splash screen.

I suspect that the next release will fix it, just like all the other bugs. :pI don't think so. From what I've seen (and this is all in my not-so-humble opinion), the Ubuntu devs are trying to use Plymouth as a club to get better open source drivers. That leaves us with the choice of looking good on boot or looking good with everything else, because drivers like nouveau don't support 3D and probably won't.

---

### Post by Macchia on 2010-04-13
Since i need to read the boot messages (text boot), there's a way to disable the graphics boot?

---

### Post by ranch hand on 2010-04-13
> **Half-Left said:**
> That's because it only supports NVIDIA GPUs or are you being sarcastic? :)
Yes, as is called for when people are saying how great plymouth runs anywhere.

---

### Post by Didius Falco on 2010-04-13
> **Macchia said:**
> Since i need to read the boot messages (text boot), there's a way to disable the graphics boot?

Remove "splash" from the kernel command-line. For Grub2, change the > GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub.

For Legacy Grub, remove "splash" from the kernel line. This:

```
title        Ubuntu lucid (development branch), kernel 2.6.32-20-generic
uuid        b5dbdf90-9819-4d84-a3b0-03df1dabd451
kernel        /boot/vmlinuz-2.6.32-20-generic root=UUID=b5dbdf90-9819-4d84-a3b0-03df1dabd451 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-20-generic
quiet

```

Would become this:

```
title        Ubuntu lucid (development branch), kernel 2.6.32-20-generic
uuid        b5dbdf90-9819-4d84-a3b0-03df1dabd451
kernel        /boot/vmlinuz-2.6.32-20-generic root=UUID=b5dbdf90-9819-4d84-a3b0-03df1dabd451 ro quiet 
initrd        /boot/initrd.img-2.6.32-20-generic
quiet

```

---

### Post by paxmark1 on 2010-04-13
Thanks ever so much.  I was not lucking out trying to search for how to disable splash, kept finding the ones who wanted splash but it was missing.  I often lurk for a couple weeks in beta and rc. 

I have used the live cd successfully and could not get over how b. ugly the splashes were.  I much prefer seeing the initial info scrolling past while looking for glitches.   

I will definitely go with no splash when I do a clean install for the LTS.  Thank you very kindly Didius Falco.

---

### Post by bruce89 on 2010-04-13
> **teh603 said:**
> That leaves us with the choice of looking good on boot or looking good with everything else, because drivers like nouveau don't support 3D and probably won't.

Actually, the nouveau in F13 apparently has experimental 3D support (if you install a seperate package).

---

### Post by Ibidem on 2010-04-13
Removing "splash" isn't working here, it seems (might need to double check)...
And besides that, I see some issues with the fsck.
(Press C to skip file system check; I press C; boot hangs w/ message about dosfsck encountering an unrecoverable error).
It might be plymouth (per older discussions) or it might be crazy stuff like running KDE over SSH to a RHEL4 server (here at Chico), but I'm seeing occasional hard freezes/kernel panics since I let it install.

---

### Post by Macchia on 2010-04-14
> **Didius Falco said:**
> Remove "splash" from the kernel command-line. For Grub2, change the  line in /etc/default/grub.

For Legacy Grub, remove "splash" from the kernel line. This:

```
title        Ubuntu lucid (development branch), kernel 2.6.32-20-generic
uuid        b5dbdf90-9819-4d84-a3b0-03df1dabd451
kernel        /boot/vmlinuz-2.6.32-20-generic root=UUID=b5dbdf90-9819-4d84-a3b0-03df1dabd451 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-20-generic
quiet

```

Would become this:

```
title        Ubuntu lucid (development branch), kernel 2.6.32-20-generic
uuid        b5dbdf90-9819-4d84-a3b0-03df1dabd451
kernel        /boot/vmlinuz-2.6.32-20-generic root=UUID=b5dbdf90-9819-4d84-a3b0-03df1dabd451 ro quiet 
initrd        /boot/initrd.img-2.6.32-20-generic
quiet

```

already tried before asking but sadly it doesn't work

---

### Post by djchandler on 2010-04-14
> **Didius Falco said:**
> Remove "splash" from the kernel command-line. For Grub2, change the  line in /etc/default/grub.

I knew how to disable the splash for a single boot such as when running forcefsck, which has been hanging, but not how to safely make it permanent on GRUB2.

Now that you point out how to change it, I feel a bit embarrassed. But we were trying to make Plymouth work plus I try not to muck around in those configuration files unless there's no other option. I'm giving up on Plymouth for now. It doesn't seem to work with fglrx. Text is not being rendered with ascii text apparently being sent straight into graphics buffer resulting in garbage pixels across the top of the splash screen. Added to that problem is the ati xorg driver has a bug that overheats my laptop and triggers a BIOS safety shutdown frequently, running ~20°C hotter all the time than with the fglrx driver.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/557829](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/557829)
xserver-xorg-video-ati (Ubuntu) Triaged High Unassigned

Last I heard yesterday via email, it is being passed upstream to xorg; they must not have accepted it yet as it's still unassigned.

Many, many thanks for your help.

---

### Post by djchandler on 2010-04-14
> **Macchia said:**
> already tried before asking but sadly it doesn't work

Did you run sudo update-grub after editing /etc/default/grub?

---

### Post by makro on 2010-04-14
I've black screen with a flashing cursor in the top left corner, Plymouth starts for a couple of seconds before GDM login.
I've Intel Graphic Card.
Boot always hangs during disks checking...

---

### Post by Macchia on 2010-04-14
> **djchandler said:**
> Did you run sudo update-grub after editing /etc/default/grub?

For sure.
And i add this: i can't get anymore a console (CTRL-ALT-Fn), only a black screen.

---

### Post by Jordanwb on 2010-04-14
My laptop has a x1600 (or was it x1300?) ATI Radeon chip. Plymouth works just fine, although purple isn't one of my favourite colours. Although I can fix that.

---

### Post by ASULutzy on 2010-04-14
A friendly little bump as I still don't have working tty's :(

[http://ubuntuforums.org/showpost.php?p=9115532&postcount=660](http://ubuntuforums.org/showpost.php?p=9115532&postcount=660)

Any help would be really appreciated!

---

### Post by meborc on 2010-04-14
> **ASULutzy said:**
> A friendly little bump as I still don't have working tty's :(

[http://ubuntuforums.org/showpost.php?p=9115532&postcount=660](http://ubuntuforums.org/showpost.php?p=9115532&postcount=660)

Any help would be really appreciated!

have you tried using vga=794 or similar on kernel line... i don't know if it works at the moment, but vga used to do the trick to get tty's working under nvidia drivers before (you will get an error/warning message saying that vga is deprecated, but it will still work)

the boot will still be crappy and if you have huge resolution, it will not look as good as with nouveau, but it should be operational

i will test when i get home

---

### Post by Half-Left on 2010-04-14
> **teh603 said:**
> I don't think so. From what I've seen (and this is all in my not-so-humble opinion), the Ubuntu devs are trying to use Plymouth as a club to get better open source drivers. That leaves us with the choice of looking good on boot or looking good with everything else, because drivers like nouveau don't support 3D and probably won't.

Nouveau does actually have experimental 3D support now with the mesa-dri. I've tried it and compiz works with my 9600GT.

Exciting times for opensource in that regard.

---

### Post by ratcheer on 2010-04-14
> **makro said:**
> 
Boot always hangs during disks checking...

See bug 554737 on Launchpad.

Tim

---

### Post by meborc on 2010-04-14
> **Half-Left said:**
> Nouveau does actually have experimental 3D support now with the mesa-dri. I've tried it and compiz works with my 9600GT.

Exciting times for opensource in that regard.

interesting... have to try it out soon

---

### Post by Didius Falco on 2010-04-14
QUOTE=Macchia;9121148]For sure.
And i add this: i can't get anymore a console (CTRL-ALT-Fn), only a black screen.[/QUOTE]

Per the README.Debian file, located at /usr/share/doc/plymouth/README.Debian:

> Changing Themes
---------------

Plymouth themes are installed into sub-directories of /lib/plymouth/themes,
some themes may require plugins installed (as .so files) into /lib/plymouth.

Search the archive for packages named plymouth-theme-*

To change the current theme:

  sudo update-alternatives --config default.plymouth
  sudo update-initramfs -u

To restore the default theme:

  sudo update-alternatives --auto default.plymouth
  sudo update-initramfs -u


Disabling the splash screen
---------------------------

There are two methods to disable the splash screen.  Both have the
same effect.  Your boot will show such messages as are emitted by
the starting services, and will still be able to prompt if needs be.

 [COLOR=Red]1) Remove all of the plymouth-theme-* packages from your system,
    including the text ones.  Plymouth will remain installed to
    permit boot-time prompts.[/COLOR]

 2) Remove "splash" from the kernel command-line.  You can do this
    per-boot, or make it permanent by changing the
    GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub


High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -uThe pertinent part for you is highlighted in [COLOR=Red]red[/COLOR], but I thought it made sense to just post the whole file, since it's relatively short.

I hope this helps you out...

---

### Post by DanaG on 2010-04-14
I've grabbed a serial-console log of Plymouth actively refusing to show me a splash screen.  Take a note of my kernel command line -- though even with "quiet", it still gives me no splash.

[www.csc.calpoly.edu/~dgoyette/no_splash_for_you.log](www.csc.calpoly.edu/~dgoyette/no_splash_for_you.log)

video=uvesafb:mode_option=1280x960-24@60,scroll=ywrap,blank=1 plymouth:debug splash

The advantage of uvesafb is that you can use fbset to change its mode on the fly.  Note that it does need the "v86d" package to be installed, however.

---

### Post by teh603 on 2010-04-14
> **Half-Left said:**
> Nouveau does actually have experimental 3D support now with the mesa-dri. I've tried it and compiz works with my 9600GT.

Exciting times for opensource in that regard.No kidding. Anyone think there's a chance of it getting added to the default loadout, or will it just slowly waste away into nothingness in the repositories?

---

### Post by Longinus00 on 2010-04-15
> **teh603 said:**
> No kidding. Anyone think there's a chance of it getting added to the default loadout, or will it just slowly waste away into nothingness in the repositories?

It won't waste away because it's actively being developed. It probably won't make it into lucid because it's still too new. See 3D support for R600+ cards via radeon in karmic.

---

### Post by ratcheer on 2010-04-15
Both plymouth and mountall have been updated since earlier, this morning.

Tim

---

### Post by Half-Left on 2010-04-15
> **teh603 said:**
> No kidding. Anyone think there's a chance of it getting added to the default loadout, or will it just slowly waste away into nothingness in the repositories?

I don't think so because Ubuntu is not as bleeding edge as Fedora. Fedora 13 have them in their default repos.

---

### Post by ranch hand on 2010-04-16
Wha Hoo.  Updates that did something.

Yes sir re Bob.

I have this, my main install with plymouth pretty much wiped.  My 2 backups are different.

One is default.  The other has the themes removed.

Seeing some possible improvement in my throw aways (they are somewhat modifided so I couldn't be sure) I upgraded the 2 mentioned above.

The one with no themes booted great.  Would not shut down.  Well I only waited a minute after the last activity noted.

The default one, my oldest most reliable 10.04 (upgraded to tool chain on first day old), the one that did have some boot problems back before A1, will not boot (looping gdm - will see if I can get in tomorrow and file a bug).  It did shut down nicely from the login screen.

Wow, Plymouth sure is wonderful.

---

### Post by ranch hand on 2010-04-16
Ah, looking into this further I see even more improvement.

The install that boot, not only has the advantage of not shutting down, but also a doubling of boot time.

I love plymouth and think that every one should use it.  These fast boot times are just too much too handle.

---

### Post by ranch hand on 2010-04-16
And it just gets better all the time.  Amazing.

Just fooled with the OS left just as the default intends it to be.  This is the best improvement I have found in plymouth to date (I am sure that the best is still to come).

There are just too many bugs being filed.  THIS has been fixed.  I can't even boot through recovery.  If you can't get in, you can't file bugs.

No bugs = it works great

Therefore it works great.

Doesn't get much better than that, but I am sure it will.

Now I will go and disable the bugger which, of coarse, will make filing a bug on it a little tough.  But hey, my OS will work.

Now I realize that it is not the purpose of plymouth to let your OS work but I really prefer it to.  I am sure that with re-education I can be brought around to a more reasonable attitude.

---

### Post by makro on 2010-04-16
I've just upgraded...

freeze during disks checking seems to be solved even if it stops at 73% of 1of3 checking... anyway GDM starts

Black screen with a flashing cursor in the top left corner during boot remains...

(Anyway I know the FRAMEBUFFER=y workaround...)

---

### Post by null_pointer_us on 2010-04-16
I updated to the latest kernel and plymouth. Upon rebooting to see what had changed, init locked up (with many errors, incl. not being able to start plymouth properly). The next boot was fine.

:confused:

---

### Post by flipper9 on 2010-04-16
Perhaps we should rename Plymouth to Pinto? :lolflag:

---

### Post by Stason on 2010-04-16
Seriously, 12 days from final - can this be solved? The number of people unable to boot has grown exponentially since beta2, and I am one of them.

---

### Post by dyltman on 2010-04-16
> **Stason said:**
> Seriously, 12 days from final - can this be solved? The number of people unable to boot has grown exponentially since beta2, and I am one of them.

13 days here,

still yes the time is running short. Hopefully ubuntu team (or someone else) will manage to fix this in time.

---

### Post by fedexnman on 2010-04-16
> **flipper9 said:**
> Perhaps we should rename Plymouth to Pinto? :lolflag:

or common abbreviations for profanity.   p.o.s     p.i.t.a.  :lolflag:

---

### Post by cdude42 on 2010-04-16
im not sure it matters when 10.04 is released as long as everything works right. although there is an official release day. every time i boot i get

mountall: could not connect to plymouth
thats it. then everthing goes as it should.

so im not sure if thats related to any of this, but ive never had a real problem.

---

### Post by fedexnman on 2010-04-16
i know alot of people use ati and nvidia propriety drivers, and plymouth just does'nt jive, its just plain ugly. point blank, xsplash was so awesome ( why plymouth ), the way plymouth boots or does'nt boot is a deal breaker  ( sorry ), i might stay with karmic and see what 10.10 does, sorry for venting here ..

---

### Post by sgage on 2010-04-16
Is there an accurate sense of how many/what proportion of people are unable to boot with plymouth?

I am using the proprietary nvidia drivers, and it all works fine. After applying the /etc/defaults/grub and etc/grub.d/00_headers tweaks, it even looks good. And I boot in 18 seconds. It's been this way for weeks.

Please, I'm NOT saying that there isn't a problem with plymouth, just wondering about the magnitude of the problem, and if there is any sense of which hardware is interacting poorly...

As far as it being only 12 days until release, well, I've been amazed before at how much can happen in 12 days, even (maybe especially) towards the end of the cycle. 

Here's hoping!

---

### Post by ratcheer on 2010-04-16
It is strange to me. Many people say they can't boot since Beta 2, while I was unable to boot all through the Alphas and have only been able to boot *since* the Betas came along.

My plymouth screen started looking much cleaner, today, too. I use the nVidia proprietary driver and just about everything is working perfectly for me, now. There have been a ton of updates in the past few days and, for me, everything really is getting better and better. A few days ago, I even upgraded my primary use system to Lucid.

Tim

---

### Post by Didius Falco on 2010-04-16
Mine boots okay, but the fsck not finishing problem has returned, after having been taken care of before.

Now, I get faux "checking the file system" messages at every boot, and when it actually does try to run fsck, it quits at 71% and continues on to the gdm screen.

Still, I'm in a lot better shape than a lot of the poor buggers having problems with it...

---

### Post by FrancoNero on 2010-04-16
the thing with boot is, i have a black screen for such a long time, that's where you need the splash screen with the progress bar. i mean that's what it's for, but when it finally comes up, the process is over and that's it.... i never really get to see plymouth really

---

### Post by ranch hand on 2010-04-16
sgage, ratcheer and all others for whom this dog works.

Plymouth has a long history with Fedora of working just this well.  It works fine on some hardware combinations and not at all on others.  There is no real good pattern in this failure to see.

This is core of the problem.  It is the reason for katie-xx saying how impressed she was with the progress the Ubuntu devs have made.

It is not possible to fix something that has no pattern to failure.  While I am not a programmer at all, I do have diagnostic skills in other fields.  I read the stuff on plymouth here.  The pattern is one of a basic fault in the design of the mechanism, if I may use that term for code, and this usually means it is not worth fixing.

I hope they do.  Fedora would certainly like it if they did.

I do not think they will because as they plug one leak, the patch causes more elsewhere (yes mixing metaphors).  That is why it is getting worse, not better.

---

### Post by ranch hand on 2010-04-16
To update on the OS of mine that will not boot.

I have fooled with it on and off all day.  No go.  I will keep updating.  I doubt that it will boot before testing is over.

My other drives have gone from booting in the high thirties (all on the same external) and low 40s to about 1.5 minutes.

There is one exception to that.  I have one, same hardware, that has all /ect/init/plymouth-watever files (all 4) renamed.  The /lib/plymouth directory renamed plymouth.<censored>.  That OS throws up a bunch of errors on its way to consistently boot (password login) at 26 seconds (best=23, worst=28 yes I am rounding).

EDIT

I know how this will be set up on the "real" install on my main drive after release.

---

### Post by sgage on 2010-04-16
ranch hand,

that was what I was wondering - if there was a discernible pattern. If not, woe be unto plymouth!

---

### Post by ranch hand on 2010-04-16
> **sgage said:**
> ranch hand,

that was what I was wondering - if there was a discernible pattern. If not, woe be unto plymouth!
If you read this entire thread (have fun) you will see there are time it looks like a pattern and then it gets fixed.

More problems, more serious problems pop up.  Admittedly in fewer boxes but they are always worse than the old ones and harder to work around.

This means the more boxes that will boot, maybe not with plymouth working well but booting, the more boxes are excluded form running 10.04 all together because the fixes have destroyed the workarounds that worked on those boxes.

I admire the ability of Linux in general an Ubuntu in particular for the ability to run on a lot of very different hardware.  The thing is that this box has always just loved Ubuntu.  Very few problems at all.  Plymouth is killing it.

You can see my box in my sig.  This is not weird hardware, pretty mainstream.  How many of this kind of box can you exclude.

No it will not exclude me or this box because  I can go in from somewhere else and disable plymouth completely.

Where does this leave the new user with a similar XPS 420 desktop box?  Or for that matter a lot of folks that may already be using Ubuntu on such a box but take advantage of the fact that in Ubuntu you really have to do little to get it to work.  I do not think that they are going to search the archives to find this forum.  I do not think they are going to be comfortable with hunting down and deleting or renaming system files.

Think of all the bad information, available today on grub2 written by bloggers who have never seen or used grub2 (at least from what they say that is how it seems).  Grub2 may have problems yet but it works.

Think of the coming confusion, caused by different bloggers on their different hardware, holding forth as experts on plymouth problems and workarounds.  Some of these are going to be real wrecks.

This is not, assuming no stunning improvement, going to be pretty.

---

### Post by mc4man on 2010-04-17
Well it appears they're fairly commited to it.

Happened to just notice some changes to the theme I use - ubuntu_logo.
There are now 2 sets of .png's, the orig (RGB), and a new set, ubuntu_logo16 (Indexed color (16 colors)

It appears that with nouveau the orig. is used and with nvidia-current the ..16 is used.
Why I'm not sure - if this is to make it look better it really doesn't, it's still displayed to large.

If they were to scale down the ubuntu_logo16 png it would look half decent, how much is debatable.

Here on a 23" screen I've scaled it at 87x23 pixels, w/ the dots at 10x10 and it looks pretty good.

Don't have any other themes so don't know if they have 16 png's also.

---

### Post by ranch hand on 2010-04-17
They sure are working at it.  Complete over haul two days in a row.

On the other hand, at this point in the dev cycle, that seems kind of sad.

I really hope they backport what ever they replace this dog with in the future.

This really is shaping up to be a really great OS.  It is a shame that something as silly as this is going to be a large problem.

---

### Post by ranch hand on 2010-04-17
I just had a chance to check what the new update did for my unbootable OS.

The gdm loggin no longer loops!!!!!!!!!!  Isn't that great?  It just freezes solid.

---

### Post by k3lt01 on 2010-04-17
Plymouth is broken on my laptop after updating to the new kernel (2.6.32-21). I can get into Lucid with 2.6.32-20 with no problems and Plymouth works and looks like it should but with 2.6.32-21 Plymouth takes up the entire screen and then the laptop wont go any further. No hdd activity, nothing.

Reboot and select recovery mode for 2.6.32-21, select low graphics mode and everything is fine, infact it looks like the graphics are normal. Will do a search to see if anyone else has posted this specific issue because it's a pain having to go through recovery mode.

---

### Post by philinux on 2010-04-17
Ok we've passed final freeze. This is my boot up as of now.

Hit the grub boot and start timing.

15 seconds with a black screen and blinking cursor top left.

4 seconds of plymouth then GDM

4 seconds to desktop.

Pretty fast boot and I'm happy with that but 15 seconds wait with a black screen!

nVidia 8600gt standard install.

---

### Post by Milos_SD on 2010-04-17
You got 4sec from gdm to desktop? :O
Here it takes about 37sec. :(
But I have awn with a lot of icons and applets, and compiz that starts on login.

---

### Post by makro on 2010-04-17
> **philinux said:**
> Ok we've passed final freeze. This is my boot up as of now.

Hit the grub boot and start timing.

15 seconds with a black screen and blinking cursor top left.

4 seconds of plymouth then GDM

4 seconds to desktop.

Pretty fast boot and I'm happy with that but 15 seconds wait with a black screen!

nVidia 8600gt standard install.

For me it's the same... with Intel graphic

On tty1 i can see "mountall: plymouth command failed"
GDM starts on tty8

---

### Post by Yellow Pasque on 2010-04-17
My solution was to hack mountall and revert plymouth from a hard dependence to a recommended package. This allowed me to remove plymouth, (hey, now I can see my boot messages, my system boots faster, and Xserver doesn't randomly crash anymore ;) )
Hacked version of mountall: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

You may have issues with mountall when plymouth isn't running according to the changelog:
> Add hard dependency on Plymouth; without it running, mountall will
    ignore any filesystem which doesn't show up within a few seconds or that
    fails to fsck or mount.  If you don't want graphical splash, you simply
    need not install themes.
However, I removed plymouth and everything Works For Me (TM)

---

### Post by cdude42 on 2010-04-17
> **Milos_SD said:**
> You got 4sec from gdm to desktop? :O
Here it takes about 37sec. :(
But I have awn with a lot of icons and applets, and compiz that starts on login.

i probably have 20 seconds from when i push the power button until im in google chrome. I have compiz and docky to start too. what are your system specs?

---

### Post by jkxx on 2010-04-17
Kubuntu boots up real quick so no complaints there.

However, plymouth doesn't seem to work. I get a strange 16 color version of the progress bar which appears briefly amid some [ OK ] and other warning messages, then the screen blinks and kdm loads. 

No big deal though the boot screen is clearly borked.

(Opteron 180, Nvidia GeForce 8800 GTS, Kubuntu 10.04/64 here)

---

### Post by Milos_SD on 2010-04-17
> **cdude42 said:**
> i probably have 20 seconds from when i push the power button until im in google chrome. I have compiz and docky to start too. what are your system specs?

Intel Core2Duo E6550 2.33Ghz, 8GB RAM, Nvidia 7600GT, WD Green 1TB (system disk). and I use custom 2.6.34-rc4 kernel. Maybe problem is that I did the upgrade from Karmic, and not the clean install? :S

Btw, plymouth works great here with nvidia binary drivers.

---

### Post by ranch hand on 2010-04-17
> **Temüjin said:**
> My solution was to hack mountall and revert plymouth from a hard dependence to a recommended package. This allowed me to remove plymouth, (hey, now I can see my boot messages, my system boots faster, and Xserver doesn't randomly crash anymore ;) )
Hacked version of mountall: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages]("https://launchpad.net/%7Edtl131/+archive/mediahacks/+packages")

You may have issues with mountall when plymouth isn't running according to the changelog:

However, I removed plymouth and everything Works For Me (TM)
Well I had to give that a whack.

I think they better make that the default mountall.  Has got me back under a minute anyway.

The problem now is just in libplymouth2 I am sure but this is a big improvement.

Shut down time is about as long as boot time.  Multi-boot system and it has to go through unmounting every one of the buggers and remounting as RO.

Not sure why this is.  Never did this before.  Shut down time was one of the impressive things about 10.04 until just recently.  Now it takes forever.

---

### Post by Owen.C93 on 2010-04-17
I get plymouth throughout with a 20 second boot. You can change it to start early which worked for me. The solution is in this thread somewhere.

---

### Post by ranch hand on 2010-04-17
Change what to start early?  Plymouth?  This would be great.  That way it would freeze quicker every time fsck is run, which is every time if plymouth is running.

I don't think I would like that any better.

---

### Post by Owen.C93 on 2010-04-17
> **ranch hand said:**
> Change what to start early?  Plymouth?  This would be great.  That way it would freeze quicker every time fsck is run, which is every time if plymouth is running.

I don't think I would like that any better.
It was more a general statement to people who don't like a blank screen.

---

### Post by madmax1735 on 2010-04-18
> **k3lt01 said:**
> Plymouth is broken on my laptop after updating to the new kernel (2.6.32-21). I can get into Lucid with 2.6.32-20 with no problems and Plymouth works and looks like it should but with 2.6.32-21 Plymouth takes up the entire screen and then the laptop wont go any further. No hdd activity, nothing.

Reboot and select recovery mode for 2.6.32-21, select low graphics mode and everything is fine, infact it looks like the graphics are normal. Will do a search to see if anyone else has posted this specific issue because it's a pain having to go through recovery mode.


hey i am facing the same issue on lucid with plymouth... doesnt boot with the latest kernel... did u manage to figure out anythig or file a bug report.

thnx

---

### Post by KlavKalashj on 2010-04-18
> **Owen.C93 said:**
> I get plymouth throughout with a 20 second boot. You can change it to start early which worked for me. The solution is in this thread somewhere.


Could you please point this out? 74 pages is a lot to look through :P

---

### Post by mfraser on 2010-04-18
> **madmax1735 said:**
> hey i am facing the same issue on lucid with plymouth... doesnt boot with the latest kernel... did u manage to figure out anythig or file a bug report.

thnx

I'm getting this too. Did a fresh install of Kubuntu 10.04 and the only way I can boot at the moment is by using the recovery option.

Has a bug report been filed?

---

### Post by k3lt01 on 2010-04-18
> **madmax1735 said:**
> hey i am facing the same issue on lucid with plymouth... doesnt boot with the latest kernel... did u manage to figure out anythig or file a bug report.

thnx

> **mfraser said:**
> I'm getting this too. Did a fresh install of Kubuntu 10.04 and the only way I can boot at the moment is by using the recovery option.

Has a bug report been filed?In answer to you both I have only just now got the time to take a breath. I can boot through recovery mode > FailsafeX. The stupid thing is X boots into full resolution and colour it is by no means a poor option. I will do a bug report after a little more trial and error so I can give as much info as possible. Although I think I have as much info as I am going to get, I will post the bug report # when it is done.

EDIT 1: Bug #566379 just reported. To madmax1735, mfraser, and anyone else with this problem please add to this report with any relevant information you have. Please don't just mark as "affects me to" because the devs need as much information as they can get to get Plymouth working properly.

EDIT 2: My issue is now fixed you can read about it in Launchpad. Needless to say it wasn't Plymouth but instead it is the kernel. Apparently they changed a setting within 2.6.32-21 that disabled KMS so I had to modify a line in grub.cfg to get it to work in normal mode. I wouldn't go using the setting Steve Langasek advised me to use unless you have the same hardware as I do. If you have different hardware the setting may well b different so post in the bug report to find out what your setting should be if indeed we have the same problem.

---

### Post by Stason on 2010-04-21
> **Temüjin said:**
> My solution was to hack mountall and revert plymouth from a hard dependence to a recommended package. This allowed me to remove plymouth, (hey, now I can see my boot messages, my system boots faster, and Xserver doesn't randomly crash anymore ;) )
Hacked version of mountall: [https://launchpad.net/~dtl131/+archive/mediahacks/+packages](https://launchpad.net/~dtl131/+archive/mediahacks/+packages)

You may have issues with mountall when plymouth isn't running according to the changelog:

However, I removed plymouth and everything Works For Me (TM)

Oh, man, this is ugly. Is that what it gets to boot an otherwise decent OS these days?

Did you just replace mountall or you had to remove and reinstall it?

---

### Post by Yellow Pasque on 2010-04-21
I just installed the new mountall .deb, which then allows you to purge plymouth without taking out half of the system's packages.

---

### Post by ranch hand on 2010-04-21
It really does help if plymouth is screwing with you.  I hope that mountall gets this version.  It would have to wait, probably, until after the final release but that would be fine.  It would sure be a help to a lot of folks.

---

### Post by Ibidem on 2010-04-21
I have removed plymouth (mountall 2.9 official installed), and am booting fine (it does  give one extra error, about plymouth terminating).
I checked to see if the latest official mountall requires plymouth:
```
sudo apt-get update
apt-get -s upgrade mountall|grep plymouth
# -s is "run a simulation"
```And it only wants to update libplymouth2, no sign of installing plymouth.

So it looks like the issue with plymouth is how the package manager handles "recommends"?

---

### Post by Yellow Pasque on 2010-04-21
@Ibidem - Huh? Plymouth was made a hard dependency in mountall 2.10. From changelog:
> * Add hard dependency on Plymouth; without it running, mountall will
    ignore any filesystem which doesn't show up within a few seconds or that
    fails to fsck or mount.  If you don't want graphical splash, you simply
    need not install themes.
That's why I've reverted it to a recommended package in the version of mountall in my PPA.

---

### Post by Stason on 2010-04-22
Good news with the RC updates and 21 kernel I am able to boot again and it looks that it is a 100% boot now. With Beta1 I get around 60% boot with the rest hanging with that SM error. Beta2 made my system totally unbootable. Now it boots solid, but I still see some crap on screen and it is a different error every time. 

If it is not improved within 2 weeks after final I will be looking at that alternative mountall and purging plymouth whatsoever.:guitar:

---

### Post by teh603 on 2010-04-22
> **Temüjin said:**
> @Ibidem - Huh? Plymouth was made a hard dependency in mountall 2.10. From changelog:

That's why I've reverted it to a recommended package in the version of mountall in my PPA.Ok, this smells to me like someone's trying to just stuff this down our throats and say "Oh, if it doesn't work then just remove the theme package." Not that I've had any problems since they fixed the first string of broken pipe errors, but it still bugs the hell out of me.

---

### Post by Longinus00 on 2010-04-22
> **teh603 said:**
> Ok, this smells to me like someone's trying to just stuff this down our throats and say "Oh, if it doesn't work then just remove the theme package." Not that I've had any problems since they fixed the first string of broken pipe errors, but it still bugs the hell out of me.

What?

---

### Post by Mr. Picklesworth on 2010-04-22
> **teh603 said:**
> Ok, this smells to me like someone's trying to just stuff this down our throats and say "Oh, if it doesn't work then just remove the theme package." Not that I've had any problems since they fixed the first string of broken pipe errors, but it still bugs the hell out of me.

Sounds like you got the bottom half of the changelog entry. The top half has the rationale&#8230;
&#8220;Add hard dependency on Plymouth; without it running, mountall will ignore any filesystem which doesn't show up within a few seconds or that fails to fsck or mount&#8221;
Seemed quite reasonable to me :/

---

### Post by teh603 on 2010-04-23
> **Mr. Picklesworth said:**
> Sounds like you got the bottom half of the changelog entry. The top half has the rationale…
“Add hard dependency on Plymouth; without it running, mountall will ignore any filesystem which doesn't show up within a few seconds or that fails to fsck or mount”
Seemed quite reasonable to me :/Can you explain that rationale to me? I'm not a programmer, but I do remember having a fair few bugs in the alpha and beta that were fixed by removing plymouth completely, and not just its theme packages. So even with the rationale it still reads like "Sorry, you're stuck with it."

---

### Post by Stason on 2010-04-23
> **Mr. Picklesworth said:**
> Sounds like you got the bottom half of the changelog entry. The top half has the rationale&#8230;
&#8220;Add hard dependency on Plymouth; without it running, mountall will ignore any filesystem which doesn't show up within a few seconds or that fails to fsck or mount&#8221;
Seemed quite reasonable to me :/

Making at best tertiary package, which is only supposed to run for 5 seconds, essential to boot the whole system - seems highly unreasonable to me. I would prefer to have black screen during boot-up for 30 seconds rather that that psychedelic flickering between text errors, purple screen with blinking dots, blinking cursor, some greenish lines, two "starting up" message in different fonts etc plymouth gives me. But perhaps it is a perceptual difference.
:P

---

### Post by ShadowDragon on 2010-04-23
> **Mr. Picklesworth said:**
> Sounds like you got the bottom half of the changelog entry. The top half has the rationale&#8230;
&#8220;Add hard dependency on Plymouth; without it running, mountall will ignore any filesystem which doesn't show up within a few seconds or that fails to fsck or mount&#8221;
Seemed quite reasonable to me :/

Making mountall (a mounter) hard-dependent on plymouth (something that has to do with graphics)? Seriously? Bad smell, anyone?

Ah, found the source of the smell...
```
mountall  reads  fstab(5)  and calls fsck(8), mount(8) and swapon(8) in
       the correct order to mount filesystems once the underlying devices have
       been created by udevd(8)

       [b]This is a temporary tool until init(8) itself gains the necessary flex&#8208;
       ibility to perform this processing[/b]; you should not rely on  its  behav&#8208;
       iour.
```
Both the same author.
Go, init, Go! We all depend on you!

---

### Post by Longinus00 on 2010-04-23
> **teh603 said:**
> Can you explain that rationale to me? I'm not a programmer, but I do remember having a fair few bugs in the alpha and beta that were fixed by removing plymouth completely, and not just its theme packages. So even with the rationale it still reads like "Sorry, you're stuck with it."

I don't know what there is to understand. If you don't have plymouth, mountall might not recognize your hard drives. I suspect most people like having their hard drives mounted.

As has just been pointed out, the mountall situation is hopefully only temporary. This is probably all fallout from the long term goal of moving the boot process away from a serial init based process to a parallel (i.e. event based) one. All the major distros are doing this because it's the smart long term thing to do so you'll have a hard time trying to escape it.

---

### Post by emarkay on 2010-04-23
> **Longinus00 said:**
> I don't know what there is to understand. If you don't have plymouth, mountall might not recognize your hard drives. I suspect most people like having their hard drives mounted.

So in other words, kill Plymouth (and it's otherwise unneeded bloat), and then just manually mount whatever drives you want to access - and if need be, a simple boot script in GRUB2 can mount the boot drive, eh? 

Now who's gonna assist so we can "Break Plymouth Rock"? 

It's time for a fork - UUbuntu: Ubuntu for the Users!

---

### Post by MacUntu on 2010-04-23
> **emarkay said:**
> It's time for a fork - UUbuntu: Ubuntu for the Users!

A distro with you in charge would definitely be entertaining.

---

### Post by csaket on 2010-04-23
I have moved to using the minimal install cd and doing an expert install and choosing what I want to install, thus no plymouth.

An additional benefit I noted is that now when I resume from hibernate, I can see a percentage progress indicator for the resume process.

:P

---

### Post by Genesius on 2010-04-23
Not sure if this has been posted before - if it has, my search skills must be getting rusty because I couldn't find it.

I have an Nvidia GeForce 8400 card, running the 195.36.15 drivers on Lucid. Originally had the blue bar problem with Plymouth, but this thread showed me how to fix that. So I've got the Ubuntu logo coming up, but it's shifted all the way to the left of the screen (got a 17" widescreen monitor, 1440 x 900 resolution). Anybody got a way to get it back to the center?

---

### Post by ratcheer on 2010-04-23
> **Genesius said:**
> Not sure if this has been posted before - if it has, my search skills must be getting rusty because I couldn't find it.

I have an Nvidia GeForce 8400 card, running the 195.36.15 drivers on Lucid. Originally had the blue bar problem with Plymouth, but this thread showed me how to fix that. So I've got the Ubuntu logo coming up, but it's shifted all the way to the left of the screen (got a 17" widescreen monitor, 1440 x 900 resolution). Anybody got a way to get it back to the center?

I have a very similar situation with my nvidia 9400GT, same driver, and 19" 1440x900 monitor. I believe it is a hardware detection problem. If I go to my monitor's setup menu and do a Picture Adjustment >> Auto Adjust, it resets the screen, properly. However, if I do that when the system is in its bootup screens, I just have to do it again after the desktop is started. So, I just let the bootup screens be offset and ignore it.

Tim

---

### Post by aviramof on 2010-04-24
Something happen to my Plymouth logo it has become huge i described it in this thread
[http://ubuntuforums.org/showthread.php?t=1461301](http://ubuntuforums.org/showthread.php?t=1461301)

it like desktop icons stretch to the max as for my desktop icon i tried to use the stretch icon option and i did managed to reduce there size but there default size is big size
as seen in the picture in the thread i mentioned  even in new icons so what ever caused the icons on desktop to change there default size changed Plymouth logo size as well.

was there any update recently that might have caused this?

---

### Post by motorbreath on 2010-04-24
I'm having real problems with this and I hope someone can help. 
File attached is an image of my boot -bloody ugly

Have a GeForce 7300 and am using the NVidia 195.36.15 driver.

Have been using Lucid since alpha 5 and was at one stage getting a text splash. Don't know when it went pear shaped.

---

### Post by Stason on 2010-04-25
wow! I have got the same card, but all I see of Plymouth is a few errors and then 2 seconds of purple 10.04 text screen. You are sort of lucky you got something looking closer to normal boot screen.:lolflag:

Seriously, are there any other way of _not_ seeing plymouth 
(including text errors and text fallback screen) besides hacked mountall and purging it from the system? I am afraid this way would be too radical and might break the system, since plymouth is now a dependency for everything. I just want 30 seconds of black screen between grub and desktop - no error messages, no shiny sunrise, no screwed logo, no purple screen, no nothing. :confused:

---

### Post by grandtoubab on 2010-04-25
> **Stason said:**
> wow! I have got the same card, but all I see of Plymouth is a few errors and then 2 seconds of purple 10.04 text screen. You are sort of lucky you got something looking closer to normal boot screen.:lolflag:

Seriously, are there any other way of _not_ seeing plymouth 
(including text errors and text fallback screen) besides hacked mountall and purging it from the system? I am afraid this way would be too radical and might break the system, since plymouth is now a dependency for everything. I just want 30 seconds of black screen between grub and desktop - no error messages, no shiny sunrise, no screwed logo, no purple screen, no nothing. :confused:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. **For a black screen with boot processes displayed in text, remove "quiet splash"**. To see the grub splash image plus a condensed text output, use "splash". The entry "acpi=off", if required, would also be an option entered on this line.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by flipper9 on 2010-04-25
With Lucid due for final release in 4 days, shouldn't the epic-fail that is Plymouth be fixed and the release delayed before Ubuntu becomes a negative reviewers delight?

---

### Post by MacUntu on 2010-04-25
No.

---

### Post by fedexnman on 2010-04-25
> **flipper9 said:**
> With Lucid due for final release in 4 days, shouldn't the epic-fail that is Plymouth be fixed and the release delayed before Ubuntu becomes a negative reviewers delight?

i 100% agree, but  then again maybe the negative reviews or publicity will get ubuntu some more attention . i know most computer users be it laptop or desktop users use some sort of gpu wether it be nvidia,ati, or intel, the whole boot process or no boot process seems bad to me. oh well i guess we'll see soon in a couple of days, i was guessing lucid to be a more polished version of karmic for a LTS version, but its looking to be an entirely different beast ???

---

### Post by Owen.C93 on 2010-04-25
Alot of the problem is the drivers though. If we are moving away from nvidia binary and ATI then the nouveau needs to work with plymouth (which it does most of the time) and needs to run compiz....which isn't ready yet.

Someone needs to make a wiki on how to get it to work with the bootsplash. I had to make it run earlier in the boot process and mess around with framebuffer and resolution for it to work. It won't out of the box.

---

### Post by 23meg on 2010-04-25
> **flipper9 said:**
> With Lucid due for final release in 4 days, shouldn't the epic-fail that is Plymouth be fixed and the release delayed before Ubuntu becomes a negative reviewers delight?

[N]("https://wiki.ubuntu.com/TimeBasedReleases")[o]("http://mdzlog.alcor.net/2008/10/29/ubuntu-quality/").

---

### Post by k3lt01 on 2010-04-25
> **23meg said:**
> [N]("https://wiki.ubuntu.com/TimeBasedReleases")[o]("http://mdzlog.alcor.net/2008/10/29/ubuntu-quality/").However, and I quote
> #

But it's very important!

    *

      The overall quality and punctuality of an Ubuntu release are more important than any single feature, and a high-quality feature is superior to a hastily-added one, even if it arrives in a later release. Free software developers are passionate about their work, and it is easy to get carried away by a particular feature, losing sight of the greater goals of Ubuntu. Pause, breathe, and consider whether it is more important to get it now or to get it right. 

#

But it works fine for me! What's the big deal?

    * Testing is hard! Many bugs only manifest themselves under certain circumstances, and these take time to discover. For example, your feature may malfunction only if the user is using a different language than you are, or in the live CD environment, or in a different desktop environment (GNOME/KDE/XFCE), or on a fresh install, or when certain other packages are installed, or on a certain hardware platform...there are many relevant variables. Ubuntu users are a diverse bunch, and given the chance, history shows that they will test new features thoroughly simply by using and experimenting with their systems. You should take advantage of the adventurous spirit of users who track the development branch, and give them a chance to help you test. 

---

### Post by Stason on 2010-04-25
> **grandtoubab said:**
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only. This is similar to the "defoptions" line in menu.lst. **For a black screen with boot processes displayed in text, remove "quiet splash"**. To see the grub splash image plus a condensed text output, use "splash". The entry "acpi=off", if required, would also be an option entered on this line.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Thanks, but I am on fake raid, therefore grub2 does not work for me either - I get your point though. However I do not want to see anything at all between grub and desktop, not even plymouth error messages.

---

### Post by tajreed on 2010-04-25
Interesting, there are nearly 52000 posts re: Plymouth. I have been tinkering with Lucid on my laptop since just before Beta 1 and have yet to see a sign of Plymouth. Don't even have a good idea of what it is or supposed to be.

Aspire 5610z with Intel 943/945 express graphics

---

### Post by davidmohammed on 2010-04-25
> **tajreed said:**
> Interesting, there are nearly 52000 posts re: Plymouth. I have been tinkering with Lucid on my laptop since just before Beta 1 and have yet to see a sign of Plymouth. Don't even have a good idea of what it is or supposed to be.

Aspire 5610z with Intel 943/945 express graphics

try switching on kms via i915.modeset=1 and
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash sudo update-initramfs -u 

as per this [link]("https://wiki.ubuntu.com/X/KernelModeSetting").  These are the usual tricks needed for us ancient intel graphics users. You might need to add the glasen ppa as well if you get lots of X-server graphics though.

---

### Post by ranch hand on 2010-04-25
I would not mess with it.  Sounds like it is working the best way possible right now.

---

### Post by teh603 on 2010-04-25
I really wish the developers weren't using Plymouth like I think they are. I keep hearing words like "kernel mode setting" and all that, but I really don't know what they mean. All I see is that we've gone from a bootsplash which caused very few problems to me, the end user, to one that seems to cause people nothing but problems.

---

### Post by leetone on 2010-04-25
Ubuntu 10.04 Lucid Lynx RC (tried also daily-live 20100425).

**Intel 82852/82855 GM/GME Graphics Controller**
**Intel Pentium M 1,73 GHz, Fujitsu-Siemens AMILO V1100**

System hangs after Ubuntu splash (when starts X). No HDD activity, no keyboard replies. Can't boot.

Tried vesa driver, tried i915.modeset=1 or 0, nomodeset options and vesa in xorg.conf -- no luck.

**Tried failsafe mode with single option in GRUB, works fine, but it's not a solution :(**

Same bug here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/568779)

---

### Post by The Cog on 2010-04-26
I read something earlier in this thread that seems to have stabilised my system:
> sudo chmod -x /bin/plymouth /sbin/plymouthd

It's ugly and gives an error message at startup, but since I did that, my PC has booted reliably and seems to have shaken off a tendency to think it's got a second monitor (it hasn't). It's a nuisance when it decides to put the login dialog on the non-existent monitor - just leaves you with a blank purple screen. 

I might try the suggestion in post #758 of this thread and see if that's a better fix, but at least I have one fix that works for me.

---

### Post by The Cog on 2010-04-26
Nope. Making plymouth executable again and removing "quite splash" from the GRUB command line gave me a boot-up with the login prompt on the non-existent screen again. Sigh.

---

