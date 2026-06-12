---
title: "AMD/ATI Radeon drivers from website vs. drivers in Ubuntu 12.04 repo"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by jasonwyz98 on 2012-05-07
I have 2 questions regarding to different AMD Radeon drivers:

1. What is the difference between the 3?

* AMD/ATI Driver ( 12.04 Repo )
* AMD/ATI Driver, Post release update ( 12.04 Repo )
* AMD/ATI Driver 12.4 ( AMD Website )

2. If I install the "Post release update" driver from Ubuntu Repos, Will I get future updates from Ubuntu, In other words what's Ubuntu Radeon driver update policy?

Thanks :)

---

### Post by ratcheer on 2012-05-07
I don't recall anyone having any luck with the one labeled "post release updates".

The other one from the repo and the one from AMD are the same, or should be. I have had better luck with the one from the repo. Others have reported the exact opposite.

Tim

---

### Post by vVvSHADOWvVv on 2012-05-07
> **jasonwyz98 said:**
> I have 2 questions regarding to different AMD Radeon drivers:

1. What is the difference between the 3?

* AMD/ATI Driver ( 12.04 Repo )
* AMD/ATI Driver, Post release update ( 12.04 Repo )
* AMD/ATI Driver 12.4 ( AMD Website )

2. If I install the "Post release update" driver from Ubuntu Repos, Will I get future updates from Ubuntu, In other words what's Ubuntu Radeon driver update policy?

Thanks :)

I have noticed that installing the post version of my NVIDIA drivers will cause graphics problems. I think this may help you.

Further,  Installing the post release of proprietary drivers may cause the video driver to be loaded at the wrong time causing system graphics failure. This is first hand from my systems.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by jasonwyz98 on 2012-05-07
@ratcheer
@vVvSHADOWvVv

Thanks for the quick response

So, does Ubuntu update the proprietary Radeon drivers in their Repo? In other word if I use the driver from Ubuntu repo, will I get 12.5, 12.6, etc. later?

---

### Post by vVvSHADOWvVv on 2012-05-07
> **jasonwyz98 said:**
> @ratcheer
@vVvSHADOWvVv

Thanks for the quick response

So, does Ubuntu update the proprietary Radeon drivers in their Repo? In other word if I use the driver from Ubuntu repo, will I get 12.5, 12.6, etc. later?

If there is a new driver, yes. But it generally takes them (NVIDIA & AMD) a while to update the drivers as Linux versions are not a top priority.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by ratcheer on 2012-05-07
Yes, I believe they will be updated when Ubuntu changes the version in the repo. That has been my experience in the past.

I am also beginning to wonder the proper use of the post release updates package. I am going to research this with aptitude and see if I can find out exactly what is what in the repo. Thanks for bringing this up. I will report back.

Tim

---

### Post by vVvSHADOWvVv on 2012-05-07
> **ratcheer said:**
> Yes, I believe they will be updated when Ubuntu changes the version in the repo. That has been my experience in the past.

I am also beginning to wonder the proper use of the post release updates package. I am going to research this with aptitude and see if I can find out exactly what is what in the repo. Thanks for bringing this up. I will report back.

Tim

@ratcheer

Beware of using those post releases. I have NEVER had ANY good luck with them.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

---

### Post by ratcheer on 2012-05-07
Wow, this is confusing. Examining the actual packages with aptitude shows that both fglrx and fglrx-updates are version "2:8.960-0ubuntu1". So, as near as I can tell, at this point in time, they are exactly the same.

Someone please correct me if I am wrong, and tell me why.

Tim

---

### Post by jasonwyz98 on 2012-05-07
> **ratcheer said:**
> Wow, this is confusing. Examining the actual packages with aptitude shows that both fglrx and fglrx-updates are version "2:8.960-0ubuntu1". So, as near as I can tell, at this point in time, they are exactly the same.

Someone please correct me if I am wrong, and tell me why.

Tim

Noticed this as well, they are the same, also found a few bug reports stating that currently you can't use Jockey to install proprietary ATI drivers:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/873058](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/873058)

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/994371](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/994371)

There are many more reports, google it.

Apparently it's caused by the version #s being the same, workaround is the manually install the drivers.

So my question is should I manuall install fglrx or fglrx-updates package?

---

### Post by deadflowr on 2012-05-07
I Believe the drivers from the repos will get updates bundled with other updates from canonical, where as drivers from ati/amd website aren't. In terms of the differences between the two repo versions, I haven't a clue. 

 So, in other words, if you install from the repos, updates will come as canonical gets them, as opposed to the ati/amd website, where you will need to be proactive to update them yourself, keeping in mind that using the ati/amd version might cause system problems; which is why it is recommended that you install from the repos(unless you really know what you are doing)

The support for all is the same. Proprietry.

---

### Post by clifford junior on 2012-05-07
seriously what are the advantages of using the ATI drivers over the open source ones?

every time ive installed them there are a number of problem including tearing, colour calibration being totally messed up due to catalyst, the plymouth boot screens being completely the wrong dimensions, etc etc

im confused of the advantages. im sure there are some so if somebody could enlighten me.

thanks

EDIT: actually i do remember one advantage was that when my screen turned itself off after idleness for 10 minutes it acually DID go into standby mode with the ATI drivers. With the open source one it goes blank says its going to enter standby but doesnt and then goes blank again and this repeats contiually until my desktop box goes to sleep. anyone know how to solve this without installing the ATI drivers?

---

### Post by ratcheer on 2012-05-07
Another advantage of the proprietary over the open source drivers is supposed to be fan control. Either the fan runs constantly with the open drivers or the card overheats. I have heard it both ways.

I cannot confirm this, but I run fglrx to try to be safe. With the proprietary driver installed, I can check the chipset temp and it is reasonable (usually 45-48 C), but I do not know how to check it with the open source drivers, so I do not know for sure that one driver is better than another.

Tim

---

### Post by jasonwyz98 on 2012-05-07
> **clifford junior said:**
> seriously what are the advantages of using the ATI drivers over the open source ones?

every time ive installed them there are a number of problem including tearing, colour calibration being totally messed up due to catalyst, the plymouth boot screens being completely the wrong dimensions, etc etc

im confused of the advantages. im sure there are some so if somebody could enlighten me.

thanks

EDIT: actually i do remember one advantage was that when my screen turned itself off after idleness for 10 minutes it acually DID go into standby mode with the ATI drivers. With the open source one it goes blank says its going to enter standby but doesnt and then goes blank again and this repeats contiually until my desktop box goes to sleep. anyone know how to solve this without installing the ATI drivers?
Advantages of proprietary drivers over open source ATI are:

uses less power,
better 3d
fan control, etc.
--------------------

Does anyone know if I should manually install fglrx or fglrx-updates package if I want to get driver updates ( 12.5, 12.6, etc. ) from Ubuntu repo (12.04) later?

BTW: We need to do a manual install instead of using "Additional Drivers aka Jockey" to install due to a bug in Jockey:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641)

Thanks

---

### Post by QIII on 2012-05-07
1.  Phoronix has complained about the "incestuous" relationship between Ubuntu and ATI for years.  Every 4th and 10th month, coinciding with an Ubuntu release, Ubuntu gets the new driver before it is released to the public.

2.  The difference between the one in the repo and the one on ATI's website is that the first is development version 8.960 and the one on their website is 8.961, the difference being the latter is the "everyone else" version.

3.  I have always found it better to use the command line to install:

```
sudo apt-get install fglrx fglrx-amdcccle
```
Followed immediately by ```
sudo aticonfig --initial
``` if it is a first time installation.

4.  Benefits over the open source version include at least that you can get hardware acceleration by adding VAAPI and the XvBA back end.  You then have H.264.

5.  If you have a color calibration problem, you should ask for help.  If you have tearing you should ask for help.  Tearing goes away completely per item 4. 

6.  Using the post-release version may make it so you are unable to use the Catalyst Control Center.

---

### Post by clifford junior on 2012-05-07
> **QIII said:**
> 
3.  I have always found it better to use the command line to install:

```
sudo apt-get install fglrx fglrx-amdcccle
```Followed immediately by ```
sudo aticonfig --initial
``` if it is a first time installation.

4.  Benefits over the open source version include at least that you can get hardware acceleration by adding VAAPI and the XvBA back end.  You then have H.264.

5.  If you have a color calibration problem, you should ask for help.  If you have tearing you should ask for help.  Tearing goes away completely per item 4. 

6.  Using the post-release version may make it so you are unable to use the Catalyst Control Center.

thanks for this. while were on it, i calibrate my monitor using dispcalGUI and in the past when ive installed ati and catalyst and opened previously worked on photos in aftershot pro, they are pretty messed up. i put this down to catalyst taking over the colour settings of ubuntu, but i could be wrong. can you shed any light on this?

regarding point 4 can you explain how to add those to the back end (i honestly dont even know what they mean or where to start). if you could then i'll give the drivers a shot again.

my graphics card is only an HD 5450, so i dont know if it can support any of that. i know it doesnt have a fan so i have no problem in that regard.

would i need to unistall the open source drivers first? there used to be an article on wiki ubuntu about this but it has been pulled so i wouldnt know how.

thanks.

---

### Post by QIII on 2012-05-07
All post HD 2xxx versions (at least, maybe some of the previous can) support VAAPI and XvBA.

Install the packages vainfo, xvba-va-driver, libva-egl1, libva-glx1 -- all available in the repos.

To test, you should get something like this:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```Splitted desktop is up to VA-API 0.8.0 in their PPA, but I prefer to keep PPAs to a minimum.

If you get a few lines like this

```
xvba_video: XVBA_CreateContext(): status 11
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```then a symlink to fglrx_drv_video.so is broken, which can be easily fixed.

Uninstall the open source drivers first so you don't have conflicts.  You should be able to uninstall the open source driver by searching through Synaptic.  Look for "ATI".  But install the fglrx package from the terminal.

Catalyst Control Center has color calibration.  I use it to match the colors between multiple monitors.

Edit:  In case you are wondering why NVIDIA users don't have to add anything for hardware acceleration, NVIDIA uses VDPAU, which is proprietary (and nicely convenient!).  ATI doesn't use a proprietary VA method, instead using the open standard VA-API which has to be added.

---

### Post by clifford junior on 2012-05-07
> **QIII said:**
> All post HD 2xxx versions (at least, maybe some of the previous can) support VAAPI and XvBA.

Install the packages vainfo, xvba-va-driver, libva-egl1, libva-glx1 -- all available in the repos.

To test, you should get something like this:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```If you get a few lines like this

```
xvba_video: XVBA_CreateContext(): status 11
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```then a symlink to fglrx_drv_video.so is broken, which can be easily fixed.

Uninstall the open source drivers first so you don't have conflicts.  You should be able to uninstall the open source driver by searching through Synaptic.  Look for "ATI".  But install the fglrx package from the terminal.

thanks for this. just a few questions before i proceed.

what commands do i use to uninstall the open source drivers?

and then i install the ati drivers and then finally those packages you listed in the last post?

thanks

---

### Post by clifford junior on 2012-05-07
> **QIII said:**
> All post HD 2xxx versions (at least, maybe some of the previous can) support VAAPI and XvBA.

Install the packages vainfo, xvba-va-driver, libva-egl1, libva-glx1 -- all available in the repos.

To test, you should get something like this:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```If you get a few lines like this

```
xvba_video: XVBA_CreateContext(): status 11
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```then a symlink to fglrx_drv_video.so is broken, which can be easily fixed.

Uninstall the open source drivers first so you don't have conflicts.  You should be able to uninstall the open source driver by searching through Synaptic.  Look for "ATI".  But install the fglrx package from the terminal.

Catalyst Control Center has color calibration.  I use it to match the colors between multiple monitors.

can i turn catalysts calibration off or ask it to use my profiled icc?

---

### Post by QIII on 2012-05-07
> **clifford junior said:**
> What commands do i use to uninstall the open source drivers?

and then i install the ati drivers and then finally those packages you listed in the last post?

thanks

As I think about it, you probably don't have to uninstall the default driver.   I never have, actually.  Just install the fglrx driver.

Yes, install the ATI driver followed by the packages described.

---

### Post by QIII on 2012-05-07
> **clifford junior said:**
> can i turn catalysts calibration off or ask it to use my profiled icc?

Not as far as I know -- but I've never tried anything like that.

---

### Post by clifford junior on 2012-05-07
> **QIII said:**
> Not as far as I know -- but I've never tried anything like that.

this is my big problem. ive just installed the ati drivers and it has messed up my colours again. i calibrate my monitor as im a photographer and so need to use my profiled icc.

i dont know how to stop catalyst changing my colour.

also this is what i get back when i install the backend files

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```

is there a problem there?

---

### Post by traditionalist on 2012-05-07
I am a new Ubuntu 12.04 user and rather naively expected the ATI proprietary drivers to work.  They don't.  The generic drivers work on my Radeon Sapphire, none of the proprietary drivers worked and all broke my dual monitor setup. I have reinstalled the system new over thirty times in the last few days, and it is finally stable, with the generic drivers.  At least I learned a lot in a comparatively short time!  Good job I am retired and not completely reliant on the system.

Regards....Trad

---

### Post by buzzingrobot on 2012-05-07
> **jasonwyz98 said:**
> Noticed this as well, they are the same, also found a few bug reports stating that currently you can't use Jockey to install proprietary ATI drivers:



In my experience using "Additional Drivers" in 12.04, Jockey incorrectly reported failure to install.  I.e., the driver was installed, in fact. I've seen a few other reports of the same behavior.

---

### Post by jasonwyz98 on 2012-05-07
@QIII

Will Ubuntu update proprietary AMD drivers ( 12.5, 12.6, etc. ) in their repo, once AMD releases them?

If so, should I install "fglrx" or "fglrx-updates" in order to get the driver updates in the future?


Thanks :)

---

### Post by clifford junior on 2012-05-07
success!

all i had to do to override the ATI catalyst colours was to load up dispcalGUI and it reread my profiled .icc

and as i have discalGUi profil to run at start up I can now run the ATI drivers.

my only issue now is the following

```
vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```

does that seem ok to all? im especially referencing this bit:

```
vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0


```

thanks for everyones help here.

---

### Post by QIII on 2012-05-07
> **clifford junior said:**
> 
i dont know how to stop catalyst changing my colour.

also this is what i get back when i install the backend files



I'll have to do some research.

Your hardware acceleration is working fine.  It is standard practice for software to return 0 to signify "OK, I didn't throw an exception."

---

### Post by QIII on 2012-05-07
> **traditionalist said:**
> I am a new Ubuntu 12.04 user and rather naively expected the ATI proprietary drivers to work.  They don't.  The generic drivers work on my Radeon Sapphire, none of the proprietary drivers worked and all broke my dual monitor setup. I have reinstalled the system new over thirty times in the last few days, and it is finally stable, with the generic drivers.  At least I learned a lot in a comparatively short time!  Good job I am retired and not completely reliant on the system.

Regards....Trad. 

What exact card are you using.  Legacy cards will not work with the current ATI driver or X server.

---

### Post by QIII on 2012-05-07
> **jasonwyz98 said:**
> @QIII

Will Ubuntu update proprietary AMD drivers ( 12.5, 12.6, etc. ) in their repo, once AMD releases them?

If so, should I install "fglrx" or "fglrx-updates" in order to get the driver updates in the future?


Thanks :)


I can't speak for Canonical and have no insight into what will or will not be included in the repos.

As for fglrx-updates:  After installing on six of my machines, it rendered me unable to use Catalyst Control Center.  I reinstalled fglrx.

---

### Post by jasonwyz98 on 2012-05-07
> **QIII said:**
> I can't speak for Canonical and have no insight into what will or will not be included in the repos.

As for fglrx-updates:  After installing on six of my machines, it rendered me unable to use Catalyst Control Center.  I reinstalled fglrx.

Thanks for the quick response, I will install "fglrx" when I get home. I sure hope Canonical will provide driver updates.

Btw: I believe the current "fglrx" driver in the 12.04 repo is the same as 12.4 on AMD website.

Anyone has any other ideas?

---

### Post by jasonwyz98 on 2012-05-08
Thanks for the replies :)


Ok, I installed "fglrx" and "fglrx-amdcccle" via Jockey aka "Additional Hardware GUI app".

Everything seems to be working ok.

Packages in the Ubuntu 12.04 repo ( 2012-05-08 ):

fglrx version: 2:8.960-0ubuntu1 size: 118 MB

fglrx-updates: version: 2:8.960-0ubuntu1 size: 118 MB

fglrx-amdcccle: version: 2:8.960-0ubuntu1 size: 11.5 MB

fglrx-amdcccle-updates: version: 2:8.960-0ubuntu1 size: 11.5 MB

So it looks like "fglrx" and "fglrx-updates" are the same thing.

Here are some bug reports about installing AMD/ATI driver via Jockey:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/873058]("https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/873058")

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/994371]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer-updates/+bug/994371")

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/949641")

Hope this helps

---

### Post by u2nTu on 2012-05-08
> **clifford junior said:**
> seriously what are the advantages of using the ATI drivers over the open source ones?...

Didn't see any mention of this so I'll note:

The ATI drivers (fglrx) seamlessly mirror two displays at each one's full resolution (even when different). The open source drivers do not -- on my systems anyway -- dropping the resolutions of both monitors to 'the least common denominator', which distorts the picture.

OTOH, none of the dozen or so things I've tried will make the ATI drivers play sound through HDMI. For that reason, I've given up on them and use only the open source ones.

---

### Post by jasonwyz98 on 2012-05-08
> **u2nTu said:**
> Didn't see any mention of this so I'll note:

The ATI drivers (fglrx) seamlessly mirror two displays at each one's full resolution (even when different). The open source drivers do not -- on my systems anyway -- dropping the resolutions of both monitors to 'the least common denominator', which distorts the picture.

OTOH, none of the dozen or so things I've tried will make the ATI drivers play sound through HDMI. For that reason, I've given up on them and use only the open source ones.

Which ATI card do you have?

Are you able to output video using HDMI?

Thanks

---

### Post by u2nTu on 2012-05-08
> **jasonwyz98 said:**
> Which ATI card do you have?

Are you able to output video using HDMI?

Thanks
Graphics: "ATI RS880 [Radeon HD 4200]" (on MB), which also has VGA output for a second monitor. (Good for me as I don't need high-performance graphics.)

Yes on HDMI video, and painless at that with either driver. (Only trouble is distortion with one and no sound with the other, mentioned earlier.)

Currently looking for dual-seat setup destructions. Planning to continue using the open source video drivers with that. Anyone have a good dual-seat / multi-seat how-to link? (Ya, need to start a new thread...)

---

### Post by Azyx on 2012-05-10
> **ratcheer said:**
> Wow, this is confusing. Examining the actual packages with aptitude shows that both fglrx and fglrx-updates are version "2:8.960-0ubuntu1". So, as near as I can tell, at this point in time, they are exactly the same.

Someone please correct me if I am wrong, and tell me why.

Tim

I created:
fglrx      - Video driver for the AMD graphics accelerators
fglrx-amdcccle - Catalyst Control Center for the AMD graphics accelerators
fglrx-dev  - Video driver for the AMD graphics accelerators (devel files)

from amd-driver-installer-12-4-x86.x86_64.run and get fglrx ([COLOR=Red]**2:8.961-0ubuntu1**[/COLOR]) not 2:8.960-0ubuntu1.

They seems to work fine, but my processors work to 70% for 720p h268-files and I cannot play BlueRay 1080 ISOs. 

/Cheers

---

### Post by ratcheer on 2012-05-10
> **Azyx said:**
> 

from amd-driver-installer-12-4-x86.x86_64.run and get fglrx ([COLOR=Red]**2:8.961-0ubuntu1**[/COLOR]) not 2:8.960-0ubuntu1.




Ok. That was not one of the ones I was comparing. The question I was answering was, "What is the difference between the two choices in the Ubuntu repository?"

Tim

---

### Post by Azyx on 2012-05-10
> **ratcheer said:**
> Ok. That was not one of the ones I was comparing. The question I was answering was, "What is the difference between the two choices in the Ubuntu repository?"

Tim

ok.

---

### Post by Azyx on 2012-05-11
> **ratcheer said:**
> Ok. That was not one of the ones I was comparing. The question I was answering was, "What is the difference between the two choices in the Ubuntu repository?"

Tim

Do you know where I can find the difference between 2:8.961 and 2:8.960? (Can't find anything on google, just find this tread)  I have now get problems to play h264-files in XBMC after I installed xvba-va-driver and libva-egl1. On 11.10 I have watermarks (not fully supported hardware), and not working HDMI-sound when using Ubuntus fglxr-drivers.

I have a E450 processor and HD6320 gfx.

/Cheers

---

### Post by ratcheer on 2012-05-11
> **Azyx said:**
> Do you know where I can find the difference between 2:8.961 and 2:8.960? (Can't find anything on google, just find this tread)  I have now get problems to play h264-files in XBMC after I installed xvba-va-driver and libva-egl1. On 11.10 I have watermarks (not fully supported hardware), and not working HDMI-sound when using Ubuntus fglxr-drivers.

I have a E450 processor and HD6320 gfx.

/Cheers

All I know is one comment I read somewhere, maybe in this thread, which said the one in the Ubuntu repository was an early release for Ubuntu and the one on the AMD website is "the same thing for everybody else". I can neither confirm nor deny that statement.

Tim

---

### Post by Azyx on 2012-05-11
> **ratcheer said:**
> All I know is one comment I read somewhere, maybe in this thread, which said the one in the Ubuntu repository was an early release for Ubuntu and the one on the AMD website is "the same thing for everybody else". I can neither confirm nor deny that statement.

Tim

Thanx. It was in this thread, as I see now. It's so confusing with all version numbers...driver stuff and things...

---

### Post by Azyx on 2012-05-11
> **QIII said:**
> All post HD 2xxx versions (at least, maybe some of the previous can) support VAAPI and XvBA.

Install the packages vainfo, xvba-va-driver, libva-egl1, libva-glx1 -- all available in the repos.

To test, you should get something like this:

```
$ vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD

```Splitted desktop is up to VA-API 0.8.0 in their PPA, but I prefer to keep PPAs to a minimum.

If you get a few lines like this

```
xvba_video: XVBA_CreateContext(): status 11
libva error: /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

```then a symlink to fglrx_drv_video.so is broken, which can be easily fixed.

Uninstall the open source drivers first so you don't have conflicts.  You should be able to uninstall the open source driver by searching through Synaptic.  Look for "ATI".  But install the fglrx package from the terminal.

Catalyst Control Center has color calibration.  I use it to match the colors between multiple monitors.

Edit:  In case you are wondering why NVIDIA users don't have to add anything for hardware acceleration, NVIDIA uses VDPAU, which is proprietary (and nicely convenient!).  ATI doesn't use a proprietary VA method, instead using the open standard VA-API which has to be added.

Hi.
I have the amd-driver-installer-12-4-x86.x86_64.run from the AMD-homepage and get fglrx ([COLOR=Red]**2:8.961-0ubuntu1**[/COLOR]) not 2:8.960-0ubuntu1
But then I install [COLOR=RoyalBlue]**xvba-va-driver**[/COLOR] and [COLOR=RoyalBlue]**libva-egl1**[/COLOR] and get vainfo exacly the same as above, [COLOR=Green]XBMC[/COLOR] cannot play H264-files. It start playing for 3-seconds, then the wole systewm freeze and I have to hard reboot. When I uninstall xvba-va-driver and libva-egl1 I can play movie again, but probably without hardware acceleration :( Any idea why? I have E450 dual core and HD6320 gfx AMD/ATI.

Cheers

---

### Post by jasonwyz98 on 2012-05-11
> **Azyx said:**
> Hi.
I have the amd-driver-installer-12-4-x86.x86_64.run from the AMD-homepage and get fglrx ([COLOR=Red]**2:8.961-0ubuntu1**[/COLOR]) not 2:8.960-0ubuntu1
But then I install [COLOR=RoyalBlue]**xvba-va-driver**[/COLOR] and [COLOR=RoyalBlue]**libva-egl1**[/COLOR] and get vainfo exacly the same as above, [COLOR=Green]XBMC[/COLOR] cannot play H264-files. It start playing for 3-seconds, then the wole systewm freeze and I have to hard reboot. When I uninstall xvba-va-driver and libva-egl1 I can play movie again, but probably without hardware acceleration :( Any idea why? I have E450 dual core and HD6320 gfx AMD/ATI.

Cheers
xvba-va-driver and libva-egl1 are experimental

see here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)
search for "Hardware Video Decode Acceleration (EXPERIMENTAL)"

---

### Post by W00ster on 2012-05-11
> **vVvSHADOWvVv said:**
> If there is a new driver, yes. But it generally takes them (NVIDIA & AMD) a while to update the drivers as Linux versions are not a top priority.

&#7780;&#11367;&#480;&#7430;&#336;&#412;
shadowsgovernment.com

Ahem...

I'm using the ATI drivers on my (still 11.10) system and they are upgraded at least once a month:
-rw-r--r-- 1  72899696 2011-04-09 10:37 ati-driver-installer-11-3-x86.x86_64.run
-rw-r--r-- 1  75754239 2011-08-17 17:43 ati-driver-installer-11-8-x86.x86_64.run
-rw-rw-r-- 1  76564617 2011-10-25 22:02 ati-driver-installer-11-9-x86.x86_64.run
-rw-rw-r-- 1  77926379 2011-11-02 20:54 ati-driver-installer-11-10-x86.x86_64.run
-rw-rw-r-- 1  97090080 2011-11-16 13:07 ati-driver-installer-11-11-x86.x86_64.run
-rw-rw-r-- 1  99618112 2011-12-13 18:29 ati-driver-installer-11-12-x86.x86_64.run
-rwxrwxr-x 1  107213014 2012-03-27 21:41 amd-driver-installer-12-2-x86.x86_64.run
-rw-rw-r-- 1  108360519 2012-04-25 17:14 amd-driver-installer-12-4-x86.x86_64.run

I'm really pleased with the drivers from ATI at the moment, I only have a 5770HD card but the drivers work flawlessly in 1920x1080 resolution and for all tasks I need.

---

### Post by Azyx on 2012-05-12
> **jasonwyz98 said:**
> xvba-va-driver and libva-egl1 are experimental

see here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)
search for "Hardware Video Decode Acceleration (EXPERIMENTAL)"

Thanx! Nice wiki!  But the wiki don list my HD 6300-serie :(. But I think i work becouse vainfo get right. Will e if there could be some conflict with XBMC or maybee I need another PPA...

---

### Post by Azyx on 2012-05-12
@jasonwyz98 Thanx a lot for the link to [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_XBMC_player_.28XvBA.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Using_XBMC_player_.28XvBA.29)

Bring me some clarity to the djungle of drivers and stuff and the PPA to XBMC here work with VA-API. I Can also play big Blue Ray IOS without [email]CPU@100%...it[/email]'s only a few % one one core and someting...  Thanx one more time :)

/Cheers!

---

### Post by promet on 2012-05-21
> **QIII said:**
> 1.  Phoronix has complained about the "incestuous" relationship between Ubuntu and ATI for years.  Every 4th and 10th month, coinciding with an Ubuntu release, Ubuntu gets the new driver before it is released to the public.

2.  The difference between the one in the repo and the one on ATI's website is that the first is development version 8.960 and the one on their website is 8.961, the difference being the latter is the "everyone else" version.

3.  I have always found it better to use the command line to install:

```
sudo apt-get install fglrx fglrx-amdcccle
```Followed immediately by ```
sudo aticonfig --initial
``` if it is a first time installation.

4.  Benefits over the open source version include at least that you can get hardware acceleration by adding VAAPI and the XvBA back end.  You then have H.264.

5.  If you have a color calibration problem, you should ask for help.  If you have tearing you should ask for help.  Tearing goes away completely per item 4. 

6.  Using the post-release version may make it so you are unable to use the Catalyst Control Center.

This worked for me on my Lenovo G555, Thanks a mil! \\:D/

---

