---
title: "Nouveau video driver failing"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Elfy on 2008-10-05
I have to use the nouveau driver to get suitable screen resolutions as I have an old nvidia card which is not supported as yet. I've tried searching here and on the wider net, looked at the nouveau wiki buit not found anything that helps.

I had it working fine with (I think) Alpha 5 - since then I've unfortunately done a clean install of the beta after some partition changes. Sadly I can no longer get it to work - there was an error which I caught a fleeting glimpse of when I was running the drm module install - a symlink failure

If I try and use the driver in xorg I get this error 

> (EE) nouveau (0):failed to open the drm 
(EE) nouveau (0):1365
(EE) Screens found, but none have usable configuration

Stuck with a max resolution of 1152x864


Can anyone help - hoping that RAOF sees the thread :)

---

### Post by RAOF on 2008-10-05
Hm.  Hello!

So, as you've found, nouveau doesn't work at all without the drm module :).  I can't do much troubleshooting without some form of log; can you capture the output of module-assistant?

---

### Post by Elfy on 2008-10-05
I can do my best :)

How would I go about installing it again - at the moment I can rerun the sudo m-a a-i drm-modules command with (Ithink -f) to force it to go through the install again - but I don't get the original error - (which I think was a symlink to kernel problem)

Not sure how to completely remove what has been installed/changed by installing it.

As an aside when I had it working previously it did so well without problems, other than 3d and tvout which I wasn't expecting :)

---

### Post by Elfy on 2008-10-05
Rerun the command and got this - before it gives the 

> Creating symlink...
apt-get install build-essential 

I get this which is no longer present once the command has completed.

> Couldn't create the /usr/src/linux symlink!


> sudo module-assistant auto-install drm-modules -f

Updated infos about 1 packages
Getting source for kernel version: 2.6.27-4-generic
Kernel headers available in /usr/src/linux-headers-2.6.27-4-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.

Done!
download 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 9 not upgraded.
Need to get 0B/569kB of archives.
After this operation, 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  drm-modules-source
(Reading database ... 121677 files and directories currently installed.)
Preparing to replace drm-modules-source 2.3.1+git20080922-0~ppa1 (using .../drm-modules-source_2.3.1+git20080922-0~ppa1_all.deb) ...
Unpacking replacement drm-modules-source ...
Setting up drm-modules-source (2.3.1+git20080922-0~ppa1) ...

Updated infos about 1 packages
unpack 
Extracting the package tarball, /usr/src/drm-modules.tar.bz2, please wait...
"/usr/share/modass/packages/drm-modules-source" build KVERS=2.6.27-4-generic KSRC=/usr/src/linux KDREV=2.6.27-4.6 kdist_image
Done with /usr/src/drm-modules-2.6.27-4-generic_2.3.1+git20080922-0~ppa1+2.6.27-4.6_i386.deb .
dpkg -i /usr/src/drm-modules-2.6.27-4-generic_2.3.1+git20080922-0~ppa1+2.6.27-4.6_i386.deb 
(Reading database ... 121677 files and directories currently installed.)
Preparing to replace drm-modules-2.6.27-4-generic 2.3.1+git20080922-0~ppa1+2.6.27-4.6 (using .../drm-modules-2.6.27-4-generic_2.3.1+git20080922-0~ppa1+2.6.27-4.6_i386.deb) ...
Unpacking replacement drm-modules-2.6.27-4-generic ...
Setting up drm-modules-2.6.27-4-generic (2.3.1+git20080922-0~ppa1+2.6.27-4.6) ...

I have no idea how to capture the building of the drm-module-sources window, however it appears to build without any issue.

Edit - after I reran the command I tried to boot with the nouveau driver again and have attached the failsafeX backup that you can get now with intrepid

---

### Post by RAOF on 2008-10-05
Geforce4MX.  Oldschool :).

Could you also attach dmesg, and the output of running "sudo modprobe -vvv nouveau"?  It looks like the kernel modules got built, so I'm not sure why they're not loading.

---

### Post by Elfy on 2008-10-06
Oh yes - old school, I use a starting handle to wind it up :)

Enclosed the dmesg and 2 terminal outputs from modprobe - I get this to start with

> FATAL: Error inserting nouveau (/lib/modules/2.6.27-4-generic/char/drm/nouveau.ko): Unknown symbol in module, or unknown parameter (see dmesg)

then it gives

> insmod /lib/modules/2.6.27-4-generic/kernel/drivers/gpu/drm/drm.ko 
insmod /lib/modules/2.6.27-4-generic/char/drm/nouveau.ko so I included both

Thanks for the help

---

### Post by subixonfire on 2008-10-07
i have the seame card & i i think the seame problem, is there a sollution to make nuveau drivers working!

ps: i know it is not polite to ask but is there maybe any 3D support for this card i can test, or perhaps that works... because nvidia folkes make me craise with the legacy driver not coming or coming but slowly ishue! 

thx in adwance & sorry for my bad english writing!

---

### Post by Elfy on 2008-10-07
From my understanding of the issue, nouveau is at the moment a work in progress - no 3d or tvout - have you seen the wiki - the link is in RAOF's sig - or at least some of it.

If you are getting the same issue as me then I assume that is good as it means the problem is not just me - or at least I hope so anyway.

Do you get the same response when trying the modprobe command once nouveau is installed?

As far as a solution - I hope there is one, that's why there's a thread :)

I assume that RAOF will return here at some point - being a developer I guess he's fairly busy at the moment with intrepid around the corner, in the meantime I'm fairly glad that there are others with the same issue.

I guess that nvidia will pitch up eventually - but I have doubts as to whether it will be before Intrepid is released, fedora 9 is in the same position I think.

If once it gets released there is still no nvidia driver, then I hope it gets a mention as a issue on the release page or there could be more than a few fed up people.

---

### Post by FuturePilot on 2008-10-07
> **forestpixie said:**
> From my understanding of the issue, nouveau is at the moment a work in progress - no 3d or tvout - have you seen the wiki - the link is in RAOF's sig - or at least some of it.

If you are getting the same issue as me then I assume that is good as it means the problem is not just me - or at least I hope so anyway.

Do you get the same response when trying the modprobe command once nouveau is installed?

As far as a solution - I hope there is one, that's why there's a thread :)

I assume that RAOF will return here at some point - being a developer I guess he's fairly busy at the moment with intrepid around the corner, in the meantime I'm fairly glad that there are others with the same issue.

I guess that nvidia will pitch up eventually - but I have doubts as to whether it will be before Intrepid is released, fedora 9 is in the same position I think.

If once it gets released there is still no nvidia driver, then I hope it gets a mention as a issue on the release page or there could be more than a few fed up people.

I am also getting the same problem you are. The exact same errors. I get the failed to open the drm error and if I try to modprobe the module I get the Unknown Symbol in module error. However it appeared to compile it fine. I followed the directions in RAOF's sig exactly. I'm trying this with a GeForce 2 Go.

---

### Post by Elfy on 2008-10-07
Well I assume that this will all be good for the getting it fixed then :)

There's not a great deal of difference between 1152x864 and 1280x1024,1280x960 - which is all I'm after - but enough to stay with hardy for the moment.

Though I must say that this is the first time I've had any problem whatsoever with new versions of ubuntu.

---

### Post by jarekh on 2008-10-07
Hello, I have that same problem. I'm using Kubuntu Intrepid Beta + updates.
My graphic card is GForce 2MX 32MB
Ther is some logs:
kern.log (some errors related to nouveau)
[http://pastebin.com/m2e0edc06](http://pastebin.com/m2e0edc06)
Xorg.0.log
[http://pastebin.com/mf853a6e](http://pastebin.com/mf853a6e)
dmesg
[http://pastebin.com/m5b83292f](http://pastebin.com/m5b83292f)

---

### Post by RAOF on 2008-10-08
Aha!  I see the problem.  I wonder why it doesn't appear on my system.

Additionally, I know how to fix it, and will do so soon.  And then I'll work out how to add some DKMS, and it'll be even swankier.

---

### Post by FuturePilot on 2008-10-08
> **RAOF said:**
> Aha!  I see the problem.  I wonder why it doesn't appear on my system.

Additionally, I know how to fix it, and will do so soon.  And then I'll work out how to add some DKMS, and it'll be even swankier.

Nice! :)

---

### Post by Elfy on 2008-10-08
> **RAOF said:**
> Aha!  I see the problem.  I wonder why it doesn't appear on my system.

Additionally, I know how to fix it, and will do so soon.  And then I'll work out how to add some DKMS, and it'll be even swankier.

Superhero - now don't keep us in suspense for too long :lol:

---

### Post by Elfy on 2008-10-08
Ok - so don't know if you have done something RAOF and it was in my updates today - but, I ran the sudo module-assistant auto-install drm-modules after an update and it works now - I have more resolutions to choose from :)

Edit - ok, been trying it out all afternoon, it appears that xorg is constantly using more cpu - ~15-20% up to 35% - free -m reports a marked increase in memory usage as well

Not to sure what is going on now, I'm using fluxbox as a wm so I assume that it should be lighter on memory.

Not completely sure whether it's the driver causing this? Edit edit - could be xorg problems as xkbd is actting up and changing keynames?

---

### Post by RAOF on 2008-10-08
The apparent memory use increase may be due to nouveau - I say apparent, because nouveau will map AGP or VRAM or somesuch into X's memory space, making it look like X is cosuming more memory when it really isn't.

As for the CPU usage - it's possible that you're hitting a poorly-accelerated path in the nouveau driver.  If you'd like to dig into this, the "oprofile" page linked to from the wiki in my sig will tell you how to get the info the nouveau devs will want.

---

### Post by plun on 2008-10-08
@RAOF

If a user wants to test, report and be involved,  what is the best way to handle a "dual config" with Intrepids solutions ?

Is it possible just to switch to tty and restart X with Nouveaus driver ?   

A new function for Envy maybe...???:)

---

### Post by RAOF on 2008-10-08
The link in my sig is pretty easy: add my PPA, install some packages, change driver to "nouveau" in xorg.conf.  Done!

---

### Post by plun on 2008-10-08
> **RAOF said:**
> The link in my sig is pretty easy: add my PPA, install some packages, change driver to "nouveau" in xorg.conf.  Done!

Well I did  (maybe fast) and also read this...

> Switching between the nouveau and nVidia proprietary drivers should be as simple as reinstalling the appropriate nvidia-glx{,-new,-legacy} package, and reverting the xorg.conf change. This will leave a git snapshot package of libdrm2 on your system, but that shouldn't cause problems. To revert completely, you would need to remove the PPA from your apt sources and downgrade the libdrm2 (and possibly libdrm-dev) package. 

If a user is lazy, Envy for this...:)

---

### Post by Elfy on 2008-10-09
> As for the CPU usage - it's possible that you're hitting a poorly-accelerated path in the nouveau driver. If you'd like to dig into this, the "oprofile" page linked to from the wiki in my sig will tell you how to get the info the nouveau devs will want.Ok - I'll have a look into that then if it is going to be of help to someone - might be back with questions :)

> The apparent memory use increase may be due to nouveau - I say apparent, because nouveau will map AGP or VRAM or somesuch into X's memory space, making it look like X is cosuming more memory when it really isn't.That's fine - just wondering really - it's a bit pointless having memory if it's not going to be used - I'm not a windows uses less memory then linux merchant :)

RAOF - finally thanks for the help, it's appreciated

---

### Post by Elfy on 2008-10-09
Got a nouveau update amongst others, kernel update needed the sudo m-a a-i drm-modules command - all still works.

I run the oprofile, couldn't find vmlinux to do opcontrol --vmlinux=/path/to/vmlinux though, no idea where it is :(

I did run it with opcontrol --no-vmlinux - I don't know what to do with the output I got - not whether it's of any use as it is, perhaps you could point me in the right direction.

Edit - just as an aside - the buffers in free -m has gone in a newly restarted system from ~90 to ~600

---

### Post by RAOF on 2008-10-09
Honestly, I've never used oprofile myself - maybe the next step is attaching the oprofile output to a bug on the nouveau component of xorg at freedesktop.org's bugzilla?  You may be able to get direction from the people in #nouveau on freenode/irc.ubuntu.com.  I'm not really sure what's required or wanted here ;).

---

### Post by Elfy on 2008-10-10
Ok thanks RAOF - all appreciated. I'll mark this now, if I find anything out I'll post back for others.

---

### Post by phenest on 2008-10-16
I'm unable to use the nouveau driver. I've installed the driver as per your instructions with no problems. I amended the xorg.conf file to use the nouveau driver but I receive this error when X starts:
```
(EE) NOUVEAU(0): [dri] GlxSetVisualConfigs not found.
(EE) NOUVEAU(0):       NVIDIA's glx present, or glx not loaded.

```

EDIT: I've checked that nvidia-glx is not installed. I did use the 177.78 driver from nVidia if that makes a difference.

---

### Post by phenest on 2008-10-16
Got it!

```
sudo sh NVIDIA-Linux-x86_64-177.78-pkg2.run --uninstall
```
...and reboot. Sorted! Now to test this nouveau driver.

---

### Post by Elfy on 2008-10-16
I'd like to know if it doesn't hammer ram at start and the cpu every time you change desktops/ move something.

It probably doesn't help I have an old card but...

---

### Post by bash on 2008-10-16
Just an a question out of curiosity to all those people using oldschool NV cards: 

How come you don't use the closed-source nvidia driver? Personal preference? I have an old PC standing around with a Geforce 2 GTS. Jockey installed drivers never worked for me (be it new or legacy). So I used Envy and installed the legacy nvidia driver and that did the trick for me. Has worked so far with all Ubuntu versions.

---

### Post by Elfy on 2008-10-16
I generally do use the closed source driver - or have up until now.

At the moment the nvidia driver doesn't work with the new xorg in intrepid - are you saying that you have the driver working?

I would though use nouveau instead if it worked 3d and tvout, at the moment it is still in development.

---

### Post by bash on 2008-10-16
Last time I tested was under Hardy. Forgot that Intrepid got X.org 7.4/Xserver 1.5. But I thougth Nvidia used to updated their legacy drivers at the same times as their normal drivers.

I'll give it a shot on the weekend. The computer needs to be updated anyways. Have you tried using Envy though? Because thats the only way it worked for me.

---

### Post by Elfy on 2008-10-16
They haven't updated yet, last released driver was in July, there's more than one thread here [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&order=desc](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14&order=desc) about it :(

tseliot's blog writes about the same thing - [http://albertomilone.com/wordpress/](http://albertomilone.com/wordpress/)

I'm sure that it'll get done sooner or later, but I think that other distro's have been waiting longer for it though.

---

### Post by bash on 2008-10-16
That answers that question. Lets hope Nvidia pulls an AMD and suddenly a nice new nvidia-legacy drivers pops up.

---

### Post by Elfy on 2008-10-16
It'd be nice, but ...

---

### Post by Manasia on 2008-10-28
Hello anyone succesful in compiling the Nouveau driver on Ubuntu 8.10 with kernel 2.6.27? 

I keep getting seg faults and what not, I am running a Geforce3 (another dinosaur). 

Anyone had any luck with legacy nvidia on Ubuntu 8.10? I have been stuck.

---

### Post by Elfy on 2008-10-28
I have nouveau working ok, leagcy is still not working.

---

### Post by Megatog615 on 2008-10-28
Nouveau crashes my laptop with a NVIDIA Geforce2 Go. As soon as X starts all I get is a black screen. I can't even SSH in to get a log, as I assume it has locked the kernel somehow. I will try to get a log somehow.

---

### Post by Elfy on 2008-10-28
If you've a problem with nouveau it might be best to start athread of you're own - this thread was for my problem which I couldn't fix:)

---

### Post by Elfy on 2008-10-29
nvidia released a beta for the legacy cards today [http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

---

