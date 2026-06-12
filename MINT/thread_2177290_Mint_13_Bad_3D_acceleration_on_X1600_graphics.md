---
title: "Mint 13: Bad 3D acceleration on X1600 graphics"
date: 2013-09-28
forum: MINT
---

### Post by danielr2 on 2013-09-28
First of all sorry for posting a question on Mint, but since it is based on Ubuntu I am hoping I might get some help here nevertheless. 

I am pretty new to Linux but nevertheless, I have installed Mint 13, 32bit (12.04) with Mate desktop on my HP nc8430 Laptop (specs: Intel T2500, 4GB RAM, Radeon X1600 graphics, 500GB HDD, Monitor 1680x1050). 

First impression, everything works right out of the box. That is great and I really like it. However, the 3D performance of the x1600 graphics sucks big time. I have already done extensive research on the ATI driver issue with "old" cards and new kernels and tried a few "solutions" found in various places on the net. Alas to no avail. glxgears returns a frame rate of approx. 60 FPS (at least opengl is somehow working, although not at all accelerated). In 2D, scrolling is pretty jerky compared to 2D performance in WinXP on the same laptop. 3D performance is almost not detectable. For example Duke3D, run through eduke32, yields a graphics performance which is worse than running Duke3D on my ancient 386, 8MB, S3, DOS 6.x PC from the early 1990's. The game usually crashes when the graphics load increases. Same experience with some more recent titles under Wine, e.g. S.T.A.L.K.E.R. SOC. I can happily run that game and similarly demanding titles on the same laptop under WinXP. Frame rate is somewhere in the range of a speedy PowerPoint presentation. Surprisingly, a DOS game (Schleichfahrt, aka. Archimedean Dynasty, from Bluebyte) run in DOSBox with DBGL front-end runs reasonably well. 

I'm presently on the open source "Radeon" driver. However, in my searching around I did try to install the fglrx driver (didn't work) and purged it according to the Radeon driver recommendation on this forum. Below some info of my set up:

```

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
....
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
....

```

I also found the following errors in Xorg.0.log:
```

....
[    16.116] (II) LoadModule: "fglrx"
[    16.119] (WW) Warning, couldn't open module fglrx
[    16.119] (II) UnloadModule: "fglrx"
[    16.119] (II) Unloading fglrx
[    16.119] (EE) Failed to load module "fglrx" (module does not exist, 0)
....
[    16.121] (II) LoadModule: "fglrx"
[    16.124] (WW) Warning, couldn't open module fglrx
[    16.125] (II) UnloadModule: "fglrx"
[    16.125] (II) Unloading fglrx
[    16.125] (EE) Failed to load module "fglrx" (module does not exist, 0)
....
[    16.260] [drm] failed to load kernel module "radeon"
[    16.260] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
....

```

Anything serious or just the "normal" behaviour of 12.04 on ATI graphics hardware? 

Is there a way to tweak 3D performance of this set-up? I would be much obliged for any help to increase the 3D performance of the open source driver set up, which supposedly fully supports my x1600 card. If you need more details, please point me to the right directions since my Linux literacy is still in its infancy. 

As it stands, 12.04 doesn't give me any advantages on this laptop and if I can only use 2D graphics I might have to move Linux to one of my even older hardware with some basic Nvidia graphics. 

Thanks

[Solved] = see last post in thread

---

### Post by Mark Phelps on 2013-09-28
Sorry to tell you this, but there are no 3D-accelerated drivers that will work with the X1600 anymore.  AMD dropped Linux driver support for that card YEARS ago.  The default open-source Radeon driver, which is installed by default, is the only one available.

---

### Post by danielr2 on 2013-09-28
Hi Mark, 

Thanks for the answer, after my research so far, I kind of feared that reply. Is there no way to tweak the open-source driver to get at least some 3D acceleration? Or might another distribution, even a commercial one, be better suited to support the x1600 card?

---

### Post by oldos2er on 2013-09-28
Moved to Other OS/Distro Support.

---

### Post by Stinger on 2013-09-28
As Mint 13 is based on Precise you should be able to use the AMD Catalyst Legacy driver from [Tomasz Makarewicz ppa]("https://launchpad.net/~makson96/+archive/fglrx?field.series_filter=precise") :)
I used this ppa with great success on Precise, Quantal and Raring.
Now I'm using EOS Luna ( based on Precise ) and the opensource ATI driver is working flawlessly :D
Running [Flight of the navigator]("http://videos.mozilla.org/uploads/mozhacks/flight-of-the-navigator/") without any jerky movements ( webGL test from Mozilla Firefox ) , just flows 
[ATTACH=CONFIG]246569[/ATTACH]
Ps.
I have a Radeon HD4670 PCI-E graphics card.

---

### Post by danielr2 on 2013-09-28
Stinger, 

thanks for the link, however, I fear my Mobility X1600 card (RV530) might not be supported with this legacy driver. Although the HD 2xxx Mobility Radeon X2500 is based on the X1600 (RV530) but still one generation ahead of my card and the memory clock specs. are a bit different. I could give it a try. Worst case, I have to put in the Mint 13 DVD and start all over ... or give Luna a try ;-)

---

### Post by Stinger on 2013-09-29
> **danielr2 said:**
> I fear my Mobility X1600 card (RV530) might not be supported with this legacy driver. Although the HD 2xxx Mobility Radeon X2500 is based on the X1600 (RV530) but still one generation ahead of my card and the memory clock specs. are a bit different. I could give it a try. Worst case, I have to put in the Mint 13 DVD and start all over ... or give Luna a try ;-)
Yeah, forgot your card is a bit to old even for the legacy driver, you seem to be stuck between a rock and a hard place :-k
If I where you I would try the Legacy driver anyway, I think the worst thing that could happen is that your box would not use the driver and default to the opensource ATI driver instead.
You can always purge the ppa afterwards and no harm is done.
Or even better, try the EOS liveCD / USB and see if that works for you ;)

---

### Post by mastablasta on 2013-09-30
> **Mark Phelps said:**
> Sorry to tell you this, but there are no 3D-accelerated drivers that will work with the X1600 anymore. AMD dropped Linux driver support for that card YEARS ago. The default open-source Radeon driver, which is installed by default, is the only one available.

according to this documentation page: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
> **Fully Supported**

All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list: 

RV530/RV560 Radeon X1600/X1650/X1700


the question here is why is it not working? obviously this was tested on this chip and it seems Open Source driver should work. if it doesn't, then this chip should be removed from the list and get fixed (as it seems it was working at some point since it was put on the list).

to the OP - the only suggestions i have is:
try the x-org edgers PPA (it's latest opensource driver). Make sure you read all the notes before installing the PPA.
option 2 is to install latest kernel. i know AMD fixed and added plenty of opensource driver things in i think 3.11 kernel. again before doing so you might want to check release notes to see if your card/chip was the one that would benefit from that.

also it sounds ridiculous if 2D acceleraiton is not working. i know these mobility chips have bad support but still -2D windows dont' work?!?! basics of desktop dont' work and chip is on list that have good 3D support.

features in opensource driver for r500 series: [http://wiki.x.org/wiki/RadeonFeature/](http://wiki.x.org/wiki/RadeonFeature/)
how to test 3D features: [http://askubuntu.com/questions/31913/how-to-perform-a-detailed-and-quick-3d-performance-test](http://askubuntu.com/questions/31913/how-to-perform-a-detailed-and-quick-3d-performance-test)

---

### Post by danielr2 on 2013-10-18
> **mastablasta said:**
> 
[...]

features in opensource driver for r500 series: [http://wiki.x.org/wiki/RadeonFeature/](http://wiki.x.org/wiki/RadeonFeature/)
how to test 3D features: [http://askubuntu.com/questions/31913/how-to-perform-a-detailed-and-quick-3d-performance-test](http://askubuntu.com/questions/31913/how-to-perform-a-detailed-and-quick-3d-performance-test)

I did try the glmark2 benchmark. Overall performance rating is 18 and none of the individual tests went higher than 25fps. I am pretty sure, my x1600 performs a lot better under WinXP. So either my setup needs urgent optimisation or the Mesa 8.0.4 and Gallium 0.4 driver are plain rubbish with the x1600 card.

---

### Post by Stinger on 2013-10-18
Hi Daniel
I think I know what you trouble is ( I've been there before ), you have installed the fglrx driver and when that did'nt work you purged it in the belive that you would revert back to the radeon driver.
Well, as you can see from your Xorg.0.log, that did'nt happen. Your system still tries to load the fglrx driver ( but can't ), fails to load the radeon kernel module too and then defaults to running 3D through the llvmpipe ( software rendering ), leaving you without 3D accelleration.
> OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
Mine for comparision:
> OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
That explains your poor result from running the glmark2, here is mine for comparision  'glmark2 Score: 1125'

Let's see if we can get your radeon driver working again. 
Did you follow this [guide]("https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx") _to the letter_ when you purged the fglrx driver ?
```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
```
As you can see from the above, not only do you need to purge fglrx but you need to reinstall mesa and xorg, and then reconfigure the xserver ( remember to reboot to activate the driver )

Another reason could be your kernel, I'm using the original 3.2 kernel ( the best one for you too I would think ). if you are using a newer kernel have a look at the [LTS Enablement Stacks page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") , kernel and xserver must both be upgraded.

---

### Post by danielr2 on 2013-10-19
Hi Stinger, 

I did the removal of the fglrx driver, as described in your link, before and I did it again 10 minutes ago. Nevertheless, "OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)" is all I get. Kernel version is 3.2.0-23-generic i686. My Linux version is the 32Bit Mint13 Mate. 

The following Mesa components have been installed: 

> 
dpkg --get-selections|grep libgl1-mesa
libgl1-mesa-dri                    install
libgl1-mesa-glx                    install


According to the X/Troubleshooting Guide there is also the **libgl1-mesa-dri:i386** and **libgl1-mesa-glx:i386**. Those are missing on my system. Should I install them?

Furthermore, I have checked the contend of the linux-firmware package installed on my system. Installed version is 1.79. However, in the radeon section, the rv530 (x1600) seems to be missing. Might the absence of the right firmware the reason for the driver not working properly?

---

### Post by danielr2 on 2013-10-19
Well, I found the problem. After some research I came across the parameter "radeon.modeset=1". According to [http://www.x.org/wiki/radeonBuildHowTo/](http://www.x.org/wiki/radeonBuildHowTo/) it should be added to grub like this: GRUB_CMDLINE_LINUX="radeon.modeset=1" to enable Kernel-based ModeSetting. 

Unfortunately my initial grub showed the following lines: 

> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1"
GRUB_CMDLINE_LINUX=""


There were 2 errors with this. 
1. the "radeon.dpm=1" parameter does not work with my 3.2 kernel (12.04 precise), it is intended for the 3.11 and later kernels. It should enable power management for the video card. But apparently not for 3.2 kernel. 
2. the "radeon.modeset=1" was missing altogether. 

So I modified the two lines in grub: 

> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="radeon.modeset=1"


After update-grub and a reboot, glmark2 shows the following info: 

> 
    OpenGL Information
    GL_VENDOR:     X.Org R300 Project
    GL_RENDERER:   Gallium 0.4 on ATI RV530
    GL_VERSION:    2.1 Mesa 8.0.4


Frame rate of the glmark2 is way above the 100fps mark. The overall glmark2 Score is now 306 (it was 18 before). 

I will now start testing the 3D performance with my games. if all runs well, it's another nail in the coffin for Windows :P

[Edit]
dmesg also gives a lot more info for "radeon": 

> 
dmesg |grep radeon
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=xxxxxxxxxxxxxxxxxxxxxxxxxxx ro radeon.modeset=1 quiet splash vt.handoff=7
[   13.010782] [drm] radeon kernel modesetting enabled.
[   13.010865] radeon 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.010873] radeon 0000:01:00.0: setting latency timer to 64
[   13.014346] radeon 0000:01:00.0: VRAM: 256M 0x0000000000000000 - 0x000000000FFFFFFF (256M used)
[   13.014350] radeon 0000:01:00.0: GTT: 512M 0x0000000010000000 - 0x000000002FFFFFFF
[   13.014417] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
[   13.014424] radeon 0000:01:00.0: radeon: using MSI.
[   13.014455] [drm] radeon: irq initialized.
[   13.025898] [drm] radeon: 256M of VRAM memory ready
[   13.025900] [drm] radeon: 512M of GTT memory ready.
[   13.034838] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[   13.080093] radeon 0000:01:00.0: WB enabled
[   13.843584] [drm] radeon: ring at 0x0000000010001000
[   13.843800] [drm] radeon: ib pool ready.
[   13.845485] [drm] radeon: power management initialized
[   14.740516] fbcon: radeondrmfb (fb0) is primary device
[   14.740757] fb0: radeondrmfb frame buffer device
[   14.740769] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:00.0 on minor 0


---

### Post by Stinger on 2013-10-19
Hi Daniel
Glad you nailed it :D , you've got 3d accelleration now I can tell, I've attaced my 'grub' file for comparision, I have:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
in mine, never had to modify it though, have you been experimenting with never kernels ?

> **danielr2 said:**
> According to the X/Troubleshooting Guide there is also the **libgl1-mesa-dri:i386** and **libgl1-mesa-glx:i386**. Those are missing on my system. Should I install them?
You dont need the i386 libs unless you are running games through Wine or use Steam for gaming ( Steam will install them automatically as I recall )

Thanks for the link to the [radeonBuildHowTo]("http://www.x.org/wiki/radeonBuildHowTo/") it's a keeper.

Her is the output from my 'glxinfo | grep OpenGL'
> OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
OpenGL version string: 2.1 Mesa 8.0.4
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by mörgæs on 2013-10-19
Thanks for an attempt at marking the thread solved. The best however is using 'thread tools'.

---

### Post by danielr2 on 2013-10-19
> **Stinger said:**
> 
[...]
in mine, never had to modify it though, have you been experimenting with newer kernels ?
[...]


No, not really. I have no clue how the "radeon.dpm=1" got in there. 

BTW, Xorg.0.log still shows the errors of fglrx failing to load. What the heck, if my 3D acceleration is working, which is the case now, I can live with the fglrx error. If I have some leisure I might search my system- and config-files if they contain some leftovers.  


> **Stinger said:**
> 
[...]
Thanks for the link to the [radeonBuildHowTo]("http://www.x.org/wiki/radeonBuildHowTo/") it's a keeper.
[...]


I thought so too. It went straight to the bookmarks ... :D


Thanks to all for your help and input.

---

### Post by danielr2 on 2013-10-19
> **mörgæs said:**
> Thanks for an attempt at marking the thread solved. The best however is using 'thread tools'.

I will keep that in mind, thanks for the info.

---

### Post by Stinger on 2013-10-19
> **danielr2 said:**
> 
BTW, Xorg.0.log still shows the errors of fglrx failing to load. What the heck, if my 3D acceleration is working, which is the case now, I can live with the fglrx error..

I'm afraid you'll have to live with that, I have the errors too as you can see:
> [    19.824] (==) Matched fglrx as autoconfigured driver 0
[    19.824] (==) Matched ati as autoconfigured driver 1
[    19.824] (==) Matched vesa as autoconfigured driver 2
[    19.824] (==) Matched fbdev as autoconfigured driver 3
[    19.824] (==) Assigned the driver to the xf86ConfigLayout
[    19.824] (II) LoadModule: "fglrx"
[    19.835] (WW) Warning, couldn't open module fglrx
[    19.835] (II) UnloadModule: "fglrx"
[    19.835] (II) Unloading fglrx
[    19.835] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    19.835] (II) LoadModule: "ati"
[    19.835] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    19.835] (II) Module ati: vendor="X.Org Foundation"
[    19.835] 	compiled for 1.11.3, module version = 6.14.99
[    19.835] 	Module class: X.Org Video Driver
[    19.835] 	ABI class: X.Org Video Driver, version 11.0
[    19.835] (II) LoadModule: "radeon"
[    19.836] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    19.836] (II) Module radeon: vendor="X.Org Foundation"
[    19.836] 	compiled for 1.11.3, module version = 6.14.99
[    19.836] 	Module class: X.Org Video Driver
[    19.836] 	ABI class: X.Org Video Driver, version 11.0
[    19.836] (II) LoadModule: "vesa"
[    19.836] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    19.836] (II) Module vesa: vendor="X.Org Foundation"
[    19.836] 	compiled for 1.11.3, module version = 2.3.0
[    19.836] 	Module class: X.Org Video Driver
[    19.836] 	ABI class: X.Org Video Driver, version 11.0
[    19.836] (II) LoadModule: "fbdev"
[    19.836] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    19.836] (II) Module fbdev: vendor="X.Org Foundation"
[    19.836] 	compiled for 1.11.3, module version = 0.4.2
[    19.836] 	ABI class: X.Org Video Driver, version 11.0
I would think it's because ubuntu is autoconfigured to first try to load fglrx as driver0, then ati as driver1, then vesa and fbdev as driver2 and 3.

---

### Post by danielr2 on 2013-10-19
Stinger, 

If that is the case, I will instantly stop worrying and get on with the more important tasks ... ;)

Thank again for the help. BTW, I had the same question posted in the Linux Mint Forum some weeks ago. I haven't received a single answer or reply until today. Guess which forum I will be using in future ... O:)

---

### Post by Stinger on 2013-10-19
The Elementary forums ? :biggrin: You are really missing out on something here..
Well the first time I had to fight a borked radeon driver was back in early 2004 when Texstar AKA Bill Reynolds borked it on the first PCLinuxOS liveCD.
Gave me quite a headache, has'nt changed much since, only the llvmpipe as a lifeline ensuring that you'll have graphics at some level. Before that you where only left with a black screen and the command line.

---

### Post by danielr2 on 2013-10-19
I know the feeling from way back during my brief excursion into HP-UX on PA-RISC boxes. Lost my command line skills in the mean time. I'm desperately trying to regain them. At least some of the buried knowledge is surfacing bit by bit, the longer I "play" with Linux. So I might just stick around throwing in the occasional "stupid" question ... :D

---

### Post by Stinger on 2013-10-19
Daniel, for the record. I think you did a great job troubleshooting, many just give up or reinstall because the graphical stuff is complicated stuff to understand.
I'm only glad to have been of asistance ;)
Ps.
I've been around on these forums for some time now, you can say a lot about ubuntu as a distro since the switch to Unity, but these forums are one of the most valuable assets for anyone running a ubuntu-based distro.
Take that admins and moderators :biggrin:

---

