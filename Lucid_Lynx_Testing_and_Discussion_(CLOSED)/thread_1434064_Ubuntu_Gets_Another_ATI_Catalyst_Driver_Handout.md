---
title: "Ubuntu Gets Another ATI Catalyst Driver Handout"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clhsharky on 2010-03-19
HI

Enjoy

[https://launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu1](https://launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu1)
[http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA](http://www.phoronix.com/scan.php?page=news_item&px=ODA4MA)


Sharky

Apr 11 update, an updated fglrx-installer package has entered Lucid respiratory that provides a new upstream release. Fixes an issue with the X.Org Server causing a segmentation fault when certain ATI graphics cards.

---

### Post by tcchris on 2010-03-20
Will this be added to lucid repos ?

---

### Post by andrek on 2010-03-20
Also, installing these packages has made my system unusable. I can't log in any more since it freezes at a purple screen. Recovery mode hangs on a black screen.

---

### Post by tcchris on 2010-03-20
I tried to install the 64 bit debs , but it messed up my desktop , so I uninstalled . Hopefully we will get a ati driver soon . Lucid works great for me , other than that

---

### Post by lavinog on 2010-03-20
I haven't installed it on my current system yet, but how are the open source drivers.  From what I hear, the 3D support is pretty good on newer cards now.

---

### Post by godhika on 2010-03-20
> **lavinog said:**
> I haven't installed it on my current system yet, but how are the open source drivers.  From what I hear, the 3D support is pretty good on newer cards now.

I am not a gamer so I xan not say something about that performance, but for your everyday compiz desktop effect it works flawless. Only thing that bothers me is that my laptop gets quite hot especially when watching flash movies. (Note that this is for a r600 chipset - mobility 3450)

---

### Post by lavinog on 2010-03-20
> **godhika said:**
> I am not a gamer so I xan not say something about that performance, but for your everyday compiz desktop effect it works flawless. Only thing that bothers me is that my laptop gets quite hot especially when watching flash movies. (Note that this is for a r600 chipset - mobility 3450)

In karmic, the power management features in the radeon driver were disabled by default...maybe they need to be turned on in lucid.

---

### Post by emarkay on 2010-03-20
So - do we install this and use it or not - doesn't sound like it's ready.

Facts, please?

---

### Post by HoboJ on 2010-03-20
I tried to install this earlier today but I got a missing dependency error. So I'll assume this isn't ready for testing or there's some obscure way of installing this that I don't know about.

---

### Post by aviramof on 2010-03-20
has anybody tried it on 2.6.33 kernel? and i'm no expert but i think there is a newer versoin:
[https://launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu3]("http://www.mail-archive.com/lucid-changes@lists.ubuntu.com/msg08285.html")

---

### Post by andrek on 2010-03-20
The error with missing /usr/lib/fglrx/ld.so.conf which often interrupted the amd64 package installation was supposedly fixed with the newest fglrx_8.721-0ubuntu**3** version. 
I'm not going to give up - quick re-installation of the system and I'll be trying luck with these drivers again :) It's definitely worth it. FGLRX with proper power management > open-source drivers without proper power management. At least for me, a laptop user.

---

### Post by clhsharky on 2010-03-20
Hi

This is a cat 10.4 not even beta yet, patched for Ubuntu. The fglrx driver that will be used in Ubuntu 10.04.

Is this not Lucid Lynx Testing, this driver is for people who want to help test the fglrx driver before the Lucid release. 

More discusion here. 
[http://www.phoronix.com/forums/showthread.php?t=22651](http://www.phoronix.com/forums/showthread.php?t=22651)


Sharky

---

### Post by emarkay on 2010-03-20
So as of today, it's a "Do Not Bother - It Is Not Ready"?

---

### Post by Kenny_Strawn on 2010-03-20
> **clhsharky said:**
> Hi

This is a cat 10.4 not even beta yet, patched for Ubuntu. The fglrx driver that will be used in Ubuntu 10.04.

Is this not Lucid Lynx Testing, this driver is for people who want to help test the fglrx driver before the Lucid release. 

More discusion here. 
[http://www.phoronix.com/forums/showthread.php?t=22651](http://www.phoronix.com/forums/showthread.php?t=22651)


Sharky

Well isn't this funny: Catalyst 10.4 on Ubuntu 10.04. The driver build corresponds to the Lucid release number!

Looks like Lucid will play really well with ATI cards once the FGLRX driver is out of beta. 8)

Or should I say: :lolflag:

---

### Post by andrek on 2010-03-20
I guess so. I heard someone got it working but only for 2D stuff, others have working it wonderfully with 3D.. And I can't get it to work at all - my system is *wonderfully* borked, cannot boot up anymore.
Looks like it's a matter of luck at this time.

---

### Post by clhsharky on 2010-03-20
Ubuntu dev's and ATI seem to think the fglrx drivers are worth testing, there the ones offering the drivers to the community.
 Lucid is not ready, fglrx is not ready, so what should we do nothing. No one has to do any testing, its voluntary. Not everybody has problems installing Operating Systems or drivers so they test and we are all better for it.
 We all have opinions.

Sharky

---

### Post by tseliot on 2010-03-20
> **andrek said:**
> Also, installing these packages has made my system unusable. I can't log in any more since it freezes at a purple screen. Recovery mode hangs on a black screen.

There was a problem with the packaging that could be reproduced only in buildds (i.e. the packages were built correctly when this was done locally) which caused the lack of certain files in the packages.

Please try again installing the "fglrx" package version 2:8.721-0ubuntu3.

Note: it's no longer called xserver-xorg-video-fglrx.

I'll enable the support for fglrx in Jockey soon so that enabling fglrx is as painless as possible.

---

### Post by jwssr on 2010-03-20
It works GREAT for me...with a small caveat...

First of all, only use the 0unbutu3  (launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu3) link.  

The builds for i386 and amd64 are on this page...download and install.

I spent the better part of today getting unmet dependencies on 0unbuntu1/2..then I tried 0unbuntu3 and it works.

The caveat...is that when configuring Catalyst.

Display Manager /  MultiDisplay tab allows 4 options.
    Disabled Display
    Single Display Desktop(Multi-desktop)
    Cloned display from display(s)2
    Multi-display desktop with display(s)2     

My first (and I think the default) was Single Display Desktop......which allows for both monitors to have gnome panels with the cursor moving between monitors thru the bottom of each screen only.  You can open apps on each monitor but cannot drag them to the other monitor.

This is the CAVEAT....Nautilus goes ape(it fires up on its own)....running constantly...hogging cpu...blinking in lower gnome panel and the inability to run nautilus at all.

When I changed to Muti-display desktop with display(s)2....it works perfectly...

Gnome panel only only monitor 1....drag apps from monitor1 to monitor2 and back...change positions of monitor1 and Monitor2 to left or right...

Catalyst also allowed me to change the size of the display area on each monitor (ie  fillup screen or make smaller....black borders)
Its also nice to have sound again thru HDMI...although Alpha3 without a prop driver also allowed sound thru HDMI

This is beta1...2.6.32-16...xorg 1.7.5....gnome 2.29.92...ati Radeon HD 3200 Graphics tied to 47in Lcd via HDMI cable   and 24 in analog Lcd via 15pinVGA....AMD dual core x64.        

VERY NICE!!!!

---

### Post by andrek on 2010-03-20
> **tseliot said:**
> There was a problem with the packaging that could be reproduced only in buildds (i.e. the packages were built correctly when this was done locally) which caused the lack of certain files in the packages.

Please try again installing the "fglrx" package version 2:8.721-0ubuntu3.

Note: it's no longer called xserver-xorg-video-fglrx.

I'll enable the support for fglrx in Jockey soon so that enabling fglrx is as painless as possible.

Thanks. I'm going to reinstall Lucid now and install the driver. Thanks again, I hope it will be a painless experience this time.

**edit:** Yup, just as expected - it works GREAT. Thank you so much!

---

### Post by Kenny_Strawn on 2010-03-20
> **tseliot said:**
> There was a problem with the packaging that could be reproduced only in buildds (i.e. the packages were built correctly when this was done locally) which caused the lack of certain files in the packages.

Please try again installing the "fglrx" package version 2:8.721-0ubuntu3.

Note: it's no longer called xserver-xorg-video-fglrx.

I'll enable the support for fglrx in Jockey soon so that enabling fglrx is as painless as possible.

[ATTACH]150805[/ATTACH]

See this screenshot? What am I doing wrong?

---

### Post by Cuppa-Chino on 2010-03-20
hmm I am doing something wrong here, followed the caveat advice and went in that order but when I start "hardware drivers" it shows me the new fglrx but claims I have held broken packages, I cannot seem to get any output to tell me what I am doing wrong....

I am using ubuntu3_amd64 version of all the files on amd64

---

### Post by dcstar on 2010-03-20
I have successfully installed - and manually configured - the new drivers/software.

See my post #27 at the end of this:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/494699)

---

### Post by Cuppa-Chino on 2010-03-20
well still no dice for me, not sure what the issue is -- I am now officially in "low graphics mode" , still looks like there is a problem initialising the card:

```
$ lspci -nn | grep ATI
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]

```

jockey still complains about some broken dependencies, but I will leave it til the morrow, any pointers very very welcome!

---

### Post by dcstar on 2010-03-20
> **Cuppa-Chino said:**
> well still no dice for me, not sure what the issue is -- I am now officially in "low graphics mode" , still looks like there is a problem initialising the card:


I manually downloaded and installed the .deb files, doing it via the repositories may not be set up yet.

I am quite satisfied with the new drivers, glxgears went up from 3866 to 16188 (compared to the open-source drivers) and on my 9.04 system it is 10312. I know glxgears is **not** a benchmark, but it does give some indication of how hard your video hardware can be pushed.

I found it was important to do this after manually installing these packages (and then do a reboot):

```
sudo aticonfig --initial
```

---

### Post by tseliot on 2010-03-20
> **Kenny_Strawn said:**
> See this screenshot? What am I doing wrong?

Maybe you should wait for packages to be available on the server that you're using

---

### Post by tseliot on 2010-03-20
> **Cuppa-Chino said:**
> hmm I am doing something wrong here, followed the caveat advice and went in that order but when I start "hardware drivers" it shows me the new fglrx but claims I have held broken packages, I cannot seem to get any output to tell me what I am doing wrong....

I am using ubuntu3_amd64 version of all the files on amd64

That's because "hardware drivers" (aka Jockey) doesn't support fglrx yet. I'll fix it soon.

---

### Post by tcchris on 2010-03-20
This install worked for me , on amd64 with hd4200 on motherboard .

Widelands later in the game was choppy at 5 speed with radeon .
Now I can run it at 30 speed and scroll across map .
Big improvement over open source driver  .
I hope the radeon driver will get there some day

---

### Post by canter690 on 2010-03-20
Have installed the latest drivers 

fglrx_8.721-0ubuntu3_amd64.deb
fglrx-amdcccle_8.721-0ubuntu3_amd64.deb
fglrx-dev_8.721-0ubuntu3_amd64.deb
fglrx-modaliases_8.721-0ubuntu3_amd64.deb

did 

aticonfig --initial

but can't run amdcccle as its not installed

frame rate around 300 on a 5750 card. Note - first time I ran fgl_glxgears I got around 10,000 frames/sec but now its dropped down to 300 - not sure what happened.

Advice / pointers ?

---

### Post by yiit on 2010-03-20
try 

sudo /usr/lib/fglrx/bin/amdccle 

for catalyst control center.

---

### Post by canter690 on 2010-03-20
Nope - not found !

Subsequent testing....

Frame rate of 300 is due to compiz/visual effects-extra, switching to normal gets around 2800 frames/sec.   Guess I was mistake about the 10,000 frames/sec.  

Have noted that some users are getting 10k fps so keen to get to that rate ( which I assume is with compiz off ).

---

### Post by yiit on 2010-03-20
> **canter690 said:**
> Nope - not found !



sorry, did a mistake about that command: here is the correct one

sudo /usr/lib/fglrx/bin/amdcccle 

(note the number of c's in amdcccle.)

---

### Post by lavinog on 2010-03-20
> **canter690 said:**
> Have installed the latest drivers 

fglrx_8.721-0ubuntu3_amd64.deb
fglrx-amdcccle_8.721-0ubuntu3_amd64.deb
fglrx-dev_8.721-0ubuntu3_amd64.deb
fglrx-modaliases_8.721-0ubuntu3_amd64.deb

did 

aticonfig --initial

but can't run amdcccle as its not installed

frame rate around 300 on a 5750 card. Note - first time I ran fgl_glxgears I got around 10,000 frames/sec but now its dropped down to 300 - not sure what happened.

Advice / pointers ?
Are you sure it installed?
try posting your dmesg and Xorg.0.log

---

### Post by jwssr on 2010-03-20
amdcccle is in system/preferences/ati catalys control center administrative...right?  I believe so.

---

### Post by jwssr on 2010-03-20
lavinog,

try this....

go into system/admin/synaptic and remove completely all fglrx items.
reboot
then reinstall all debs in sequence(insure they are from the 0unbuntu3 link....not 0unbuntu1/2).

I left this out of my post at #17...but this is a crital step as DCstar #22 states....  aticonfig --initial  or if you have dual screens or some other special config...do  aticonfig --help and look for aticonfig --(whatever) that suits your needs.

As you probably know....this builds the file  /etc/X11/xorg.conf   which is not used for os drivers....with the ati drivers...this file is necessary...

the sharpness on my big screen is phenom....

I tripleboot with lucid/win7/fedora13.  fedora13 right out of the box came with dual screen setup...I didnt have to do anything.  Win7 also..
Boy was it time for lucid!  

I have 2 other boxes with nvidia cards and just went to 195.36.15...solved the fan problem (overheating)..Im a happy camper tonite.

good luck on you ati confi....it will come around.

---

### Post by dcstar on 2010-03-21
> **yiit said:**
> sorry, did a mistake about that command: here is the correct one

sudo /usr/lib/fglrx/bin/amdcccle 

(note the number of c's in amdcccle.)

C Señor...    :-\"

---

### Post by canter690 on 2010-03-21
> **yiit said:**
> sorry, did a mistake about that command: here is the correct one

sudo /usr/lib/fglrx/bin/amdcccle 

(note the number of c's in amdcccle.)

Thank yiit

That did it.  Now just need to work on getting the fps up....

---

### Post by Kenny_Strawn on 2010-03-21
> **tseliot said:**
> Maybe you should wait for packages to be available on the server that you're using

Yeah, take a look at my sources.list:

```

#deb cdrom:[Ubuntu 10.04 _Lucid Lynx_ - Beta i386 (20100318)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

I am only using system repos.

---

### Post by Kenny_Strawn on 2010-03-21
> **tseliot said:**
> Maybe you should wait for packages to be available on the server that you're using

Also note: Apt-get did find "xorg-driver-fglrx" but wouldn't find just "fglrx". Why?

---

### Post by Cuppa-Chino on 2010-03-21
purged all fglrx packages then installed as described below:

```
fglrx_8.721-0ubuntu3_amd64.deb
fglrx-amdcccle_8.721-0ubuntu3_amd64.deb
fglrx-dev_8.721-0ubuntu3_amd64.deb
fglrx-modaliases_8.721-0ubuntu3_amd64.deb

aticonfig --initial
[/QUOTE]

resulted in this xorg.conf

[CODE]$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```


```
$ lspci -nn | grep Radeon
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]
```

am still getting the dreaded low graphics mode ie failed to get driver and card to talk

```
$ dmesg | grep ATI
[   21.436321] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
$ dmesg | grep fglrx
[   21.436321] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   21.481748] [fglrx] Maximum main memory to use for locked dma buffers: 3658 MBytes.
[   21.481898] [fglrx]   vendor: 1002 device: 68c1 count: 1
[   21.482152] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
[   21.482304] [fglrx] Kernel PAT support is enabled
[   21.482324] [fglrx] module loaded - fglrx 8.72.10 [Mar 11 2010] with 1 minors
[   32.654203] fglrx_pci 0000:01:00.0: irq 37 for MSI/MSI-X
[   32.654682] [fglrx] Firegl kernel thread PID: 1436
[   32.654992] [fglrx] IRQ 37 Enabled
[   32.844149] [fglrx] IRQ 37 Disabled
[   33.120533] fglrx_pci 0000:01:00.0: irq 37 for MSI/MSI-X
[   33.121046] [fglrx] Firegl kernel thread PID: 1454
[   33.121322] [fglrx] IRQ 37 Enabled
[   33.191194] [fglrx] IRQ 37 Disabled
[   33.420306] fglrx_pci 0000:01:00.0: irq 37 for MSI/MSI-X
[   33.420907] [fglrx] Firegl kernel thread PID: 1484
[   33.421206] [fglrx] IRQ 37 Enabled
[   33.490385] [fglrx] IRQ 37 Disabled
[   33.719831] fglrx_pci 0000:01:00.0: irq 37 for MSI/MSI-X
[   33.720305] [fglrx] Firegl kernel thread PID: 1493
[   33.720583] [fglrx] IRQ 37 Enabled
[   33.789324] [fglrx] IRQ 37 Disabled
[   34.019523] fglrx_pci 0000:01:00.0: irq 37 for MSI/MSI-X
[   34.020056] [fglrx] Firegl kernel thread PID: 1501
[   34.020358] [fglrx] IRQ 37 Enabled
[   34.089156] [fglrx] IRQ 37 Disabled
[   34.319227] fglrx_pci 0000:01:00.0: irq 37 for MSI/MSI-X
[   34.319839] [fglrx] Firegl kernel thread PID: 1509
[   34.320140] [fglrx] IRQ 37 Enabled
[   34.388873] [fglrx] IRQ 37 Disabled


```

looking at xorg.0.log:

[http://pastebin.com/vkGTJpr8]("http://pastebin.com/vkGTJpr8")

seems to segfault
```

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a25e8]
1: /usr/bin/X (0x400000+0x6538d) [0x46538d]
2: /lib/libpthread.so.0 (0x7f20ee50a000+0xf920) [0x7f20ee519920]
3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN24DisplayCapabilityService19QuerySinkCapabilityEP21DisplaySinkCapability+0x2c6) [0x7f20eb4005a6]
4: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN15TopologyManager20detectSinkCapabilityEP22TmDisplayPathInterfaceP17TMDetectionStatus+0xc5) [0x7f20eb3d2e45]
5: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN15TopologyManager12detectTargetEP22TmDisplayPathInterfacebP17TMDetectionStatus+0x30) [0x7f20eb3d2af0]
6: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN15TopologyManager17doTargetDetectionEP22TmDisplayPathInterface15DetectionMethodP17TMDetectionStatus+0x108) [0x7f20eb3d2ab8]
7: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN15TopologyManager28detectTargetWithReportOptionEP22TmDisplayPathInterface15DetectionMethodP20TMConnectivityReport+0x42) [0x7f20eb3d27a2]
8: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN15TopologyManager18DoInitialDetectionEv+0x59) [0x7f20eb3cee29]
9: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (_ZN4Dal214EnableInstanceEP14_DAL_INIT_INFO+0x29) [0x7f20eb3a2409]
10: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (DALEnableInstance+0x8d) [0x7f20eb2122ad]
11: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDalDisplayEnableDAL+0x1bb) [0x7f20eb188b3b]
12: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (xilDisplayAdaptorCreate+0x5b) [0x7f20eb18640b]
13: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (atiddxDisplayPreInit+0x561) [0x7f20eb176c31]
14: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (atiddxPreInit+0x7e4) [0x7f20eb154064]
15: /usr/bin/X (InitOutput+0x552) [0x473682]
16: /usr/bin/X (0x400000+0x25f95) [0x425f95]
17: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f20ed203c4d]
18: /usr/bin/X (0x400000+0x25ce9) [0x425ce9]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```



-- all on a sony vaio e-series btw

---

### Post by yaji on 2010-03-21
These drivers doesn't work for me. After installation I'm getting 2D only in native resolution of my screen. But when I'm trying with ```
sudo aticonfig --initial -f
```

I'm ending with low graphics mode. This is how my xorg.conf looks like:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

And this is my Xorg.0.log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.7.99.2
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-26-xen x86_64 Ubuntu
Current Operating System: Linux yaji-desktop 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:12 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-16-generic root=UUID=56fd6fbc-2390-4321-9934-3e80fae3ec1d ro quiet splash
Build Date: 20 December 2009  12:32:38AM
xorg-server 2:1.7.99.2~git20091220.0cb638dc-0ubuntu0tormod (buildd@) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.000000] (--) probed, [    0.000008] (**) from config file, [    0.000014] (==) default setting,
	[    0.000020] (++) from command line, [    0.000047] (!!) notice, [    0.000054] (II) informational,
	[    0.000060] (WW) warning, [    0.000066] (EE) error, [    0.000071] (NI) not implemented, [    0.000077] (??) unknown.
[    0.000129] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar 21 09:46:03 2010
[    0.000164] (==) Using config file: "/etc/X11/xorg.conf"
[    0.000249] (==) ServerLayout "aticonfig Layout"
[    0.000262] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    0.000271] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    0.000487] (**) |   |-->Device "aticonfig-Device[0]-0"
[    0.000510] (==) Automatically adding devices
[    0.000519] (==) Automatically enabling devices
[    0.000545] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.000593] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.000602] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.000611] (II) Cannot locate a core pointer device.
[    0.000617] (II) Cannot locate a core keyboard device.
[    0.000623] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    0.000632] (II) Loader magic: 0x7cb400
[    0.000637] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
[    0.021774] (--) PCI:*(0:1:0:0) 1002:9442:1787:2003 ATI Technologies Inc RV770 [Radeon HD 4850] rev 0, Mem @ 0xd0000000/268435456, 0xf0000000/65536, I/O @ 0x0000a000/256, BIOS @ 0x????????/131072
[    0.021901] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.021911] (II) "extmod" will be loaded by default.
[    0.021919] (II) "dbe" will be loaded by default.
[    0.021926] (II) "glx" will be loaded by default.
[    0.021933] (II) "record" will be loaded by default.
[    0.021939] (II) "dri" will be loaded by default.
[    0.021946] (II) "dri2" will be loaded by default.
[    0.021957] (II) LoadModule: "extmod"
[    0.022401] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    0.022541] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.022577] (II) Loading extension MIT-SCREEN-SAVER
[    0.022582] (II) Loading extension XFree86-VidModeExtension
[    0.022587] (II) Loading extension XFree86-DGA
[    0.022591] (II) Loading extension DPMS
[    0.022595] (II) Loading extension XVideo
[    0.022601] (II) Loading extension XVideo-MotionCompensation
[    0.022606] (II) Loading extension X-Resource
[    0.022611] (II) LoadModule: "dbe"
[    0.022895] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    0.022966] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.022999] (II) Loading extension DOUBLE-BUFFER
[    0.023005] (II) LoadModule: "glx"
[    0.023280] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    0.023413] (II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.023443] (**) AIGLX enabled
[    0.023454] (II) Loading extension GLX
[    0.023463] (II) LoadModule: "record"
[    0.023745] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    0.023812] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.023844] (II) Loading extension RECORD
[    0.023850] (II) LoadModule: "dri"
[    0.024379] (WW) Warning, couldn't open module dri
[    0.024389] (II) UnloadModule: "dri"
[    0.024393] (EE) Failed to load module "dri" (module does not exist, 0)
[    0.024401] (II) LoadModule: "dri2"
[    0.024660] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    0.024809] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.99.2, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
[    0.024850] (II) Loading extension DRI2
[    0.024857] (II) LoadModule: "fglrx"
[    0.024995] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    0.194137] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.7.1, module version = 8.72.10
	Module class: X.Org Video Driver
[atiddxSetup] X version mismatch - detected X.org 7.1.-1.2, required X.org 7.5.1.0
[    0.209510] (II) UnloadModule: "fglrx"
[    0.209516] (II) Unloading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[    0.209526] (EE) Failed to load module "fglrx" (module requirement mismatch, 0)
[    0.209535] (EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

I'm not an expert, but "**[atiddxSetup] X version mismatch - detected X.org 7.1.-1.2, required X.org 7.5.1.0**" looks suspicious. I checked my xorg version and it was 7.5.

---

### Post by jms-ubuntu-en on 2010-03-21
> **canter690 said:**
> 
That did it.  Now just need to work on getting the fps up....
Did you get fps up already? For me the glxgears's fps dropped from ~7400 -> ~4700 when I installed packages:
```
fglrx_8.721-0ubuntu3_amd64.deb           
fglrx-dev_8.721-0ubuntu3_amd64.deb
fglrx-amdcccle_8.721-0ubuntu3_amd64.deb  
fglrx-modaliases_8.721-0ubuntu3_amd64.deb
```
VGA card is:
```
01:00.0 VGA compatible controller: ATI Technologies Inc M97 GL [ATI FirePro M7740]
```

---

### Post by canter690 on 2010-03-21
Frames are at 13000 per 5 second period or around 2500 fps.  Reading that glxgears is not a good indicator I am now loading the phoronix-test-suite which is taking ages.  Will be comparing the results with another machine which has at Nvidia GT230 ( Acer OEM box ).  It confusing when people quote glxgears - some people ( like me ) misread the 5 second number as the fps and you cant compare the fps on nvidia cause I get around 10,000 fps which doesnt make sense.  I also note that the glxgears is different ( runs a different animation ). Will continue testing phoronix-test-suite and see what I get.

---

### Post by yaji on 2010-03-21
I just tried luck with fglrx_8.721-0ubuntu**4_**amd64.deb. Nothing changed except one thing. Now it seems that this driver doesn't work at all, and when I'm trying to turn it on I'm getting this:

```
SystemError: E:Unable to correct problems, you have held broken packages.
```

---

### Post by pulpo69 on 2010-03-21
same here.

---

### Post by emarkay on 2010-03-21
Yea, so we are all testers, ok...  :) 

But I guess I am glad I didn't install ".2" - it's ".4" now, and that appears to be completely broke.

Any ETA on when this will just "pop-up" as a "Restricted Hardware" note? - or at least be fixed for a majority of the posters here?  ;)

---

### Post by GroundZero on 2010-03-21
Anyone here getting blue lines in Ubuntu Lucid.I tried this driver in all version (1/2/3/4) and every single one gives me problems.
Anyway can someone post me(someone who has it working) what commands are U using. THX

---

### Post by andrek on 2010-03-21
I had several problems with this driver but having a freshly installed lucid beta solved all the issues. Installation of -3 version went fine, everything works great. And by 'installation' I mean downloading all the four files from the launchpad page and installing them by using "sudo dpkg -i fglrx*". Afterwards I just had to "sudo aticonfig --initial" and it began working just after a reboot.

---

### Post by GroundZero on 2010-03-21
Thy,Andrek will try later and report back,...hope it works.This is the time when I really like Linux Mint because of the all hassle with codecs all that that's missing from fresh Ubuntu install.

---

### Post by emarkay on 2010-03-21
> **andrek said:**
> I had several problems with this driver but having a freshly installed lucid beta solved all the issues. Installation of -3 version went fine, everything works great. And by 'installation' I mean downloading all the four files from the launchpad page and installing them by using "sudo dpkg -i fglrx*". Afterwards I just had to "sudo aticonfig --initial" and it began working just after a reboot.

What about the -4 version?

---

### Post by GodsMadClown on 2010-03-21
> **andrek said:**
> I had several problems with this driver but having a freshly installed lucid beta solved all the issues. Installation of -3 version went fine, everything works great. And by 'installation' I mean downloading all the four files from the launchpad page and installing them by using "sudo dpkg -i fglrx*". Afterwards I just had to "sudo aticonfig --initial" and it began working just after a reboot.

Indeed.  This works for me on my clean Beta1 Lucid Kubuntu install.  

Here's my working setup after I installed all these packages using dpkg and did the initial aticonfig stuff.

```

bill@Bill-PC:~$ ls fglrx*
fglrx_8.721-0ubuntu4_amd64.deb
fglrx-amdcccle_8.721-0ubuntu4_amd64.deb
fglrx-dev_8.721-0ubuntu4_amd64.deb
fglrx-modaliases_8.721-0ubuntu4_amd64.deb
bill@Bill-PC:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series  
OpenGL version string: 3.2.9737 Compatibility Profile Context

```

---

### Post by andrek on 2010-03-21
> **emarkay said:**
> What about the -4 version?

Haven't tried it yet. I probably won't upgrade until there are some serious changes, I just don't want to break anything :)

---

### Post by emarkay on 2010-03-21
> **andrek said:**
> Haven't tried it yet. I probably won't upgrade until there are some serious changes, I just don't want to break anything :)


Yea, but they released it for whatever reason and we're testers - but "I'm not gonna try it, you try it..."  Where's Mikey when we need him? ;)

Not that I am afraid to test, but I had an horribly frustrating time getting Karmic and ATI playing well; it was the AGP aperture BIOS setting, and a lucky Google search found the only obscure clue.  I am not an expert on "X" nor on Ubuntu Restricted Hardware Drivers, so I hope those that are can try it first.

Since there are posted issues with "-4", I'd prefer to hear at least one - "works for me" before I may end up wasting a few days just to get a display(!), as before.

---

### Post by tcchris on 2010-03-21
Same as Andrek , -3 worked for me  , copying his method

---

### Post by GroundZero on 2010-03-21
Yep -3 version worked for me also.There's still present lag when resizing but only with compositing.Haven't tried suspend or Direct2D,Ill do that later.For now ill leave everything to just be :D .

---

### Post by GroundZero on 2010-03-21
Just tested Direct2D.It works great.Unbelievable actually,resizing sometimes stutters but that's when you have 15+tbas with youtube videos,...transformers in 1080p and HON(heroes of...)in background.And it didn't crash :D :D :D !!!!!!!!
Right now i'm the happiest guy in the world.

---

### Post by andrek on 2010-03-21
> **GroundZero said:**
> Just tested Direct2D.It works great.Unbelievable actually,resizing **sometimes** stutters but that's when you have 15+tbas with youtube videos,...transformers in 1080p and HON(heroes of...)in background.And it didn't crash :D :D :D !!!!!!!!
Right now i'm the happiest guy in the world.

Huh? How did you enable Direct2D? Resizing is always slow as hell here..

---

### Post by GroundZero on 2010-03-21
To activate:
            aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
,the restart X,to deactivate
            aticonfig --del-pcs-key=DDX,Direct2DAccel

---

### Post by andrek on 2010-03-21
> **GroundZero said:**
> To activate:
            aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
,the restart X,to deactivate
            aticonfig --del-pcs-key=DDX,Direct2DAccel

Wow, many things seem to be blazing fast - like opening windows, menus and pop-ups also resizing looks a lot nicer - however, there are some bugs. First of all - maximized windows leave some artefacts near the close/max/min buttons. Also, firefox scrolling seems to be slow.. Any ideas - is it supposed to be like that?

---

### Post by GroundZero on 2010-03-22
Well yes and no,...there are some other things that have to be activated first to take full leverage of new rendering.
Try adding this to xorg.conf:
1)
Section "Extensions"
Option "RENDER" "Enable"
Option "DAMAGE" "Enable"
Option "Composite" "Enable

2)Section "DRI"
Mode 0666

3)Section "Device"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "TexturedXrender" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"

---

### Post by canter690 on 2010-03-22
Tried the above settings and benchmarked with phoronix-test-suite.  Got slightly better performance on some of the tests but overall nothing major.  unigine got slower results.  

Also tried the Direct2D settings mentioned above and it did feel slightly faster but I got corruption on some of the windows - for example Terminal has small rectangles in the background.  

Going back to defaults.  Waiting for more driver updates to test.

---

### Post by tcchris on 2010-03-22
Using the above settings in xorg , the only corruption I get is the titlebar gets little white lines when I wobble the window .
Visual Effects > extra

Did not notice a huge improvement , maybe some

---

### Post by alphacrucis2 on 2010-03-22
Does it fix the slow window restore problem or do you still need the backclear patch?

---

### Post by aviramof on 2010-03-22
doesn't any one here check to see if there are new versions?
[https://launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu5](https://launchpad.net/ubuntu/lucid/+source/fglrx-installer/2:8.721-0ubuntu5)

---

### Post by GroundZero on 2010-03-22
Wow,this version actually could removed my xserver,great f-ing release.
BTW corruption everybody gets can be fixed or at least helps with this:
    aticonfig --set-pcs-val=DDX,OGLFMTA2R10G10B10Enable,1

---

### Post by andrek on 2010-03-22
> **GroundZero said:**
> Wow,this version actually could removed my xserver,great f-ing release.
BTW corruption everybody gets can be fixed or at least helps with this:
    aticonfig --set-pcs-val=DDX,OGLFMTA2R10G10B10Enable,1

Doesn't help at all. I'm back to the classic non-Direct2D mode :)

---

### Post by TrueJournals on 2010-03-22
I just upgraded last night from 9.10 to 10.04.  I also installed the -3 version of the fglrx driver last night, and the -5 version this morning.  Almost everything is working perfectly.  Unfortunately, sleep isn't working, and this is a laptop.  Sleep was working fine with fglrx in 9.10, but while the laptop will go to sleep fine, it refuses to wake up correctly.  It appears that the screen never actually turns on.

I have an ATI Radeon Mobility HD 3650.  I even tried ```
aticonfig --acpi-service=off
``` which was required in 9.10, but it didn't seem to change anything in 10.04.  Looking through logs, the only error I'm seeing is this: ```
[fglrx:fireglAsyncioIntEnableMsgHandler] *ERROR* interrupt source ff000066 is not supported on this hardware (return code = 1)
```

Anyone else having sleep troubles?

---

### Post by andrek on 2010-03-22
Yup, mine Dell Studio 1555 with ATi 4570 doesn't wake up as well.

**edit:** Also, fglrx just got upgraded by sudo apt-get upgrade to -5 version. Everything works well.

---

### Post by aviramof on 2010-03-22
How exceclly do i install it? i have downloaded and installed fglrx_8.721-0ubuntu5_i386.deb and fglrx-amdcccle_8.721-0ubuntu5_i386.deb and i don't see any diffrence is there something more i should download and install?

thanks in advance.

---

### Post by TrueJournals on 2010-03-22
> **aviramof said:**
> How exceclly do i install it? i have downloaded and installed fglrx_8.721-0ubuntu5_i386.deb and fglrx-amdcccle_8.721-0ubuntu5_i386.deb and i don't see any diffrence is there something more i should download and install?

I'm not sure if it's required, but I also installed fglrx-modaliases_8.721-0ubuntu5_amd64.deb.  After that, open a terminal and run:
```
sudo aticonfig --initial
``` then reboot.  To see if it's working, run:
```
fglrxinfo
``` you should get something along the lines of:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3650
OpenGL version string: 3.2.9737 Compatibility Profile Context
```
(Of course, yours will say whatever graphics card you have instead of Mobility Radeon HD 3650)

---

### Post by cheapsaket on 2010-03-22
> **alphacrucis2 said:**
> Does it fix the slow window restore problem or do you still need the backclear patch?

I did have to put in the patch otherwise the performance was just horrible.

---

### Post by aviramof on 2010-03-22
this is what i get when i run the first command

sudo aticonfig --initial
Could not find configuration file, so create an empty one
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-

edit:
ok i think i did it:

sudo aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0

Final conclustion:

it added me some resolutions for display but i don't have catalyst any where or at lease not in applications or system is there a command i can use?

other then this it's no longer recognize my AOC screen and show it as unknown the same go for my two lcd tv's one samsung one toshiba and every mouse scroll is refreshing the entire screen so to speak there is a line crossing the screen despite it something to do with the refresh frequencey but i can't change it from 60hz to anything eles.

i also have this error:

fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  15
  Current serial number in output stream:  15

what can i do now to fix any of this problems?

thanks in advance.

---

### Post by TrueJournals on 2010-03-22
It appears that fglrx isn't activating for you.  Can you post /var/log/Xorg.0.log and /etc/X11/xorg.conf ?  They might have some clues.  The first output of aticonfig --initial you posted is perfectly normal.  It's telling you you hadn't used fglrx before, so it needs to initialize the configuration file.  This is exactly what you told it to do, so all is good.

---

### Post by Madspyman on 2010-03-22
Just installed fglrx in Lucid (from the repo's), and rebooted everything seemed  to be working, fine but then I noticed my desktop effects weren't on so I tried to enable them and it said that "desktop effects could not be enabled." 

I assume that this is just a beta issue, although I worry that support may be being dropped for my ATI Radeon HD 3650 (works great in karmic) gpu.

Anyone have similar issues? Is my card still supported?

---

### Post by cheapsaket on 2010-03-22
> **Madspyman said:**
> Just installed fglrx in Lucid (from the repo's), and rebooted everything seemed  to be working, fine but then I noticed my desktop effects weren't on so I tried to enable them and it said that "desktop effects could not be enabled." 

I assume that this is just a beta issue, although I worry that support may be being dropped for my ATI Radeon HD 3650 (works great in karmic) gpu.

Anyone have similar issues? Is my card still supported?

My DELL uses the 3650 and I was able to use fglrx in Lucid.
I had to go to the hardware drivers and activate it in there and then reboot.

The slow restore issue was still present so I followed instructions to generate the backfill patch for 1.7.5 using this post ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256)) and then everything was working fine.

Make sure to replace the version numbers mentioned in the post with the one you have on your machine.

HTH.

---

### Post by Madspyman on 2010-03-22
> **cheapsaket said:**
> My DELL uses the 3650 and I was able to use fglrx in Lucid.
I had to go to the hardware drivers and activate it in there and then reboot.

Checked the hardware drivers says it's activated, still no compiz though. Do you have the desktop 3650 or the mobility 3650? I have the desktop version.

---

### Post by cheapsaket on 2010-03-22
> **Madspyman said:**
> Checked the hardware drivers says it's activated, still no compiz though. Do you have the desktop 3650 or the mobility 3650? I have the desktop version.

I have the mobility/laptop version

---

### Post by TrueJournals on 2010-03-22
I also have the mobility 3650, and compiz is working just fine.  Although, I did an update from 9.10 where I had desktop effects enabled, and the setting carried over.  Perhaps try doing a compiz --replace in the terminal?  I believe that's the command to replace metacity with compiz.

---

### Post by Cuppa-Chino on 2010-03-22
hi, anyone got it working with a mobility hd5650 ??

I still get sefaults as per here (even with version 5) : [http://ubuntuforums.org/showpost.php?p=9002481&postcount=39]("http://ubuntuforums.org/showpost.php?p=9002481&postcount=39")

---

### Post by screaminj3sus on 2010-03-22
> **lavinog said:**
> I haven't installed it on my current system yet, but how are the open source drivers.  From what I hear, the 3D support is pretty good on newer cards now.

I use them on my mobility 2600. They work well usability wise. Compiz works fine. But there is NO power management. it gets hotter idling then when I am in windows playing mw2. Because of that, basically they suck.

> **cheapsaket said:**
> My DELL uses the 3650 and I was able to use fglrx in Lucid.
I had to go to the hardware drivers and activate it in there and then reboot.

The slow restore issue was still present so I followed instructions to generate the backfill patch for 1.7.5 using this post ([https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256)) and then everything was working fine.

Make sure to replace the version numbers mentioned in the post with the one you have on your machine.

HTH.


God they STILL haven't fixed that bug? What a travesty.

---

### Post by myddewji13 on 2010-03-22
Hi,

I upgraded using the provided drivers and my laptop can finally sleep and wake up :D. The one thing that happened was that the boot-up/shutdown sequence broke. I used to get the logo and nice animation now it just says 'Ubuntu 10.04' in crappy text and has 4 dots underneath. I also get some type of weird error message on shutdown.

Anybody know why/possible fixes?

---

### Post by andrek on 2010-03-22
There's no way to fix that since it is not a bug. The nice Ubuntu logo with glowing dots that you were seeing before you have installed the fglrx driver was being shown because the (default) open-source ati driver supports KMS. And the proprietary fglrx does not. Therefore, plymouth doesn't look so good.

---

### Post by myddewji13 on 2010-03-22
Is it possible to replace it with something else? I know in gutsy startup-manager let me replace the login splashes with text that showed what the system was doing while booting up. Crude but useful...

---

### Post by andrek on 2010-03-22
I'm not really sure about that, but I bet that's possible, yes. You've got to look for 'plymouth theming'.

---

### Post by myddewji13 on 2010-03-22
Sorry I'm a bit confused? I thought the fglrx driver was incompatible with plymouth (or with KMS? What is KMS?). So how will changing the theme help?

---

### Post by tcchris on 2010-03-22
I am using -5 from the repo , installed through jockey .
Everything fine so far , except the plymouth issue

---

### Post by andrek on 2010-03-22
Again, I'm not really sure about that [ you'd better google for it yourself :) ] but plymouth is used even with the drivers that don't support KMS. It's just a matter of how it works, and thus - looks ( KMS enabled = nice plymouth at native resolution ; KMS disabled = ugly plymough at small resolution). I bet someone who knows things better will make it more clear.

---

### Post by emarkay on 2010-03-22
***So, does it work or not?***

I don't give a hairy behind about Plymouth.  I just want my ATI  Lucid to look like my ATI Karmic.

Facts. please... :)

---

### Post by myddewji13 on 2010-03-22
The only difference I have between the default open source drivers and fglrx are the following:

Plymouth broke (no pretty boot)
I can now wake up from sleep

Since I don't game etc... It's kinda hard for me to tell the difference. Compiz worked both before and after with acceptable performance....

---

### Post by aviramof on 2010-03-22
0.log:
```

X.Org X Server 1.7.5
Release Date: 2010-02-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ofir-desktop 2.6.33-020633-generic #020633 SMP Thu Feb 25 10:59:18 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.33-020633-generic root=UUID=57c87754-cea8-47ba-b2b7-9532c7d0d50b ro splash vga=795 quiet splash
Build Date: 12 March 2010  07:37:07AM
xorg-server 2:1.7.5-1ubuntu3 (buildd@) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 23 05:37:40 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81eee80
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 1002:9596:1787:0028 ATI Technologies Inc RV635 PRO AGP [Radeon HD 3650] rev 0, Mem @ 0xe0000000/268435456, 0xfdef0000/65536, I/O @ 0x0000bc00/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/modules/extensions/libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.5.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.10
    Module class: X.Org Video Driver
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.7.1, module version = 8.72.10
(II) ATI Proprietary Linux Driver Version Identifier:8.72.10
(II) ATI Proprietary Linux Driver Release Identifier: 8.72.1                               
(II) ATI Proprietary Linux Driver Build Date: Mar 10 2010 23:41:04
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9596) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) fglrx(0): pEnt->device->identifier=0x9b518a8
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 0.1.0
    ABI class: X.Org Video Driver, version 6.0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB 
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/extra-modules/modules/linux/libfglrxdrm.so
ukiDynamicMajor: failed to open /proc/ati/major
ukiDynamicMajor: failed to open /proc/ati/major
(--) fglrx(0): Chipset: "ATI Radeon HD 3650 AGP" (Chipset = 0x9596)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x0028)
(==) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
(--) fglrx(0): MMIO registers at 0xfdef0000
(--) fglrx(0): I/O port at 0x0000bc00
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(EE) fglrx(0): Hasn't establisted DRM connection
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.1.0
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.78
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: 
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(--) fglrx(0): Video RAM: 524288 kByte, Type: DDR2
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(EE) fglrx(0): Hasn't establisted DRM connection
(WW) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): [FB] MC range(MCFBBase = 0xe0000000, MCFBSize = 0x20000000)
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display0: CRT on primary DAC [crt1]
(II) fglrx(0): Display0 EDID data ---------------------------
(II) fglrx(0): Manufacturer: AOC  Model: f700  Serial#: 16135
(II) fglrx(0): Year: 2006  Week: 17
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) fglrx(0): Sync:  Separate
(II) fglrx(0): Max Image Size [cm]: horiz.: 32  vert.: 24
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: Off; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.631 redY: 0.329   greenX: 0.276 greenY: 0.600
(II) fglrx(0): blueX: 0.143 blueY: 0.057   whiteX: 0.283 whiteY: 0.297
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) fglrx(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) fglrx(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 94.5 MHz   Image Size:  310 x 230 mm
(II) fglrx(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) fglrx(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) fglrx(0): Monitor name: AOC FT7x0
(II) fglrx(0): Monitor name:  Series
(II) fglrx(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 72 kHz, PixClock max 110 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff0005e300f7073f0000
(II) fglrx(0):     11100103682018782a9ea8a154469924
(II) fglrx(0):     0e484ca4420031594559615981800101
(II) fglrx(0):     010101010101ea240060410028303060
(II) fglrx(0):     130036e61000001e000000fc00414f43
(II) fglrx(0):     2046543778300a202020000000fc0020
(II) fglrx(0):     5365726965730a2020202020000000fd
(II) fglrx(0):     0032a01e480b000a20202020202000c8
(II) fglrx(0): End of Display0 EDID data --------------------
(II) fglrx(0): Output DFP1 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output DFP2 has no monitor section
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): Output CRT2 has no monitor section
(II) fglrx(0): Output TV has no monitor section
(II) fglrx(0): Output COMPONENT_VIDEO has no monitor section
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 disconnected
(II) fglrx(0): Output CRT1 connected
(II) fglrx(0): Output CRT2 disconnected
(II) fglrx(0): Output TV disconnected
(II) fglrx(0): Output COMPONENT_VIDEO disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output CRT1 using initial mode 1024x768
(II) fglrx(0): DPI set to (96, 96)
(II) fglrx(0): Adapter ATI Radeon HD 3650 AGP has 2 configurable heads and 1 displays connected.
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(==) fglrx(0): NoDRI = NO
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xe0000000 FBMappedSize: 0x10000000
(II) fglrx(0): FBMM initialized for area (0,0)-(2560,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(2560,1024) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 2560 x 7167
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(**) fglrx(0): DPMS enabled
(II) fglrx(0): Initialized in-driver Xinerama extension
(WW) fglrx(0): Textured Video not supported without DRI enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/extra-modules/modules/glesx.so
(II) Module glesx: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(II) Loading extension GLESX
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 1.2.1
    ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 78
(II) fglrx(0): Acceleration enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
    compiled for 1.7.1, module version = 1.0.0
(EE) fglrx(0): XMM failed to open CMMQS connection.
(II) fglrx(0): XMM failed to initialize!
(II) fglrx(0): Enable composite support successfully
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): Cannot get TV Format. Set all TV geometry value to zero!
(II) fglrx(0): Cannot set TV horizontal size.
(II) fglrx(0): Cannot get TV Format for trying to adjust horizontal position after horizontal size changed. 
(II) fglrx(0): Cannot set TV horizontal position.
(II) fglrx(0): Cannot set TV vertical position.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI capable
[glesx] __glESXExtensionInit: No GL ES2.0 capable screen found!
(II) fglrx(0): Setting screen physical size to 270 x 203
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device "Power Button" (/dev/input/event2)
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.7.5, module version = 2.3.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 7.0
(**) "Power Button": always reports core events
(**) "Power Button": Device: "/dev/input/event2"
(II) "Power Button": Found keys
(II) "Power Button": Configuring as keyboard
(II) XINPUT: Adding extended input device ""Power Button"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) XKB: reuse xkmfile /var/lib/xkb/server-2CE46D2F8CCFAB6C1A4B498F695121C1147485D7.xkm
(II) config/udev: Adding input device "Power Button" (/dev/input/event0)
(**) "Power Button": always reports core events
(**) "Power Button": Device: "/dev/input/event0"
(II) "Power Button": Found keys
(II) "Power Button": Configuring as keyboard
(II) XINPUT: Adding extended input device ""Power Button"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device "Sleep Button" (/dev/input/event1)
(**) "Sleep Button": always reports core events
(**) "Sleep Button": Device: "/dev/input/event1"
(II) "Sleep Button": Found keys
(II) "Sleep Button": Configuring as keyboard
(II) XINPUT: Adding extended input device ""Sleep Button"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device "USB Optical Mouse" (/dev/input/event5)
(**) "USB Optical Mouse": always reports core events
(**) "USB Optical Mouse": Device: "/dev/input/event5"
(II) "USB Optical Mouse": Found 3 mouse buttons
(II) "USB Optical Mouse": Found scroll wheel(s)
(II) "USB Optical Mouse": Found relative axes
(II) "USB Optical Mouse": Found x and y relative axes
(II) "USB Optical Mouse": Found absolute axes
(II) "USB Optical Mouse": Configuring as mouse
(**) "USB Optical Mouse": YAxisMapping: buttons 4 and 5
(**) "USB Optical Mouse": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""USB Optical Mouse"" (type: MOUSE)
(**) "USB Optical Mouse": (accel) keeping acceleration scheme 1
(**) "USB Optical Mouse": (accel) acceleration profile 0
(II) "USB Optical Mouse": initialized for relative axes.
(WW) "USB Optical Mouse": ignoring absolute axes.
(II) config/udev: Adding input device "AT Translated Set 2 keyboard" (/dev/input/event4)
(**) "AT Translated Set 2 keyboard": always reports core events
(**) "AT Translated Set 2 keyboard": Device: "/dev/input/event4"
(II) "AT Translated Set 2 keyboard": Found keys
(II) "AT Translated Set 2 keyboard": Configuring as keyboard
(II) XINPUT: Adding extended input device ""AT Translated Set 2 keyboard"" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us,il"
(**) Option "xkb_variant" ","
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(II) config/udev: Adding input device "Macintosh mouse button emulation" (/dev/input/event3)
(**) "Macintosh mouse button emulation": always reports core events
(**) "Macintosh mouse button emulation": Device: "/dev/input/event3"
(II) "Macintosh mouse button emulation": Found 3 mouse buttons
(II) "Macintosh mouse button emulation": Found relative axes
(II) "Macintosh mouse button emulation": Found x and y relative axes
(II) "Macintosh mouse button emulation": Configuring as mouse
(**) "Macintosh mouse button emulation": YAxisMapping: buttons 4 and 5
(**) "Macintosh mouse button emulation": EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device ""Macintosh mouse button emulation"" (type: MOUSE)
(**) "Macintosh mouse button emulation": (accel) keeping acceleration scheme 1
(**) "Macintosh mouse button emulation": (accel) acceleration profile 0
(II) "Macintosh mouse button emulation": initialized for relative axes.
(II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
(WW) fglrx(0): Cannot get updated TV attributes.
```xorg.conf:
```

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
        Virtual    2560 1024
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

```

i have ATI Radeon HD 3650 AGP 512MB DDR2.

---

### Post by TrueJournals on 2010-03-23
Hmmm... this is interesting, and seems to be the cause of your problems: ```
board vendor info: third party graphics adapter - NOT original ATI
```

Is your graphics card ATI branded, or some third-party brand using the ATI chipset?  It would appear that the fglrx driver doesn't support third-party boards with ATI GPUs.  Did you have fglrx installed and working in a previous version of Ubuntu?

---

### Post by aviramof on 2010-03-23
my card is ati hd3650 agp 512mb ddr2 shappire and yes i had used this card before with ubuntu 8.10 and also 9.04 and 9.10 so i'm guessing that sooner or later they would add support for third-party boards with ATI GPUs.

---

### Post by Madspyman on 2010-03-23
> **aviramof said:**
> my card is ati hd3650 agp 512mb ddr2 shappire and yes i had used this card before with ubuntu 8.10 and also 9.04 and 9.10 so i'm guessing that sooner or later they would add support for third-party boards with ATI GPUs.

I have an ati radeon hd3650 1gb ddr2 from sapphire. It works great in Karmic(so must be supported?), not in Lucid, I get no compiz and plymouths splash looks ugly at boot.

---

### Post by aviramof on 2010-03-23
so it seem that current driver don't support it not yet anyway.

---

### Post by Madspyman on 2010-03-23
> **aviramof said:**
> so it seem that current driver don't support it not yet anyway.

I worry about this, In Ibex on my laptop my Ati Radeon Xpress 200m worked great, but by Jaunty fglrx had dropped support for it, I could still install the fglrx drivers (even in karmic) but I'd get no compiz and a weird flicker at boot up.

So now on my desktop here in Lucid with my 3650 I'm seeing the telltale signs of the same problem I had on my laptop. 

I just hope this time it's just a beta thing.

---

### Post by aviramof on 2010-03-23
it said 
board is an unknown third party board, chipset is supported

so we'll just have to wait and see i guess.

---

### Post by tcchris on 2010-03-23
Code:

board vendor info: third party graphics adapter - NOT original ATI



My 0.log also said this .
I have a onboard hd4200 that seems to be working fine with the new drivers

---

### Post by Nakkar on 2010-03-23
Hi,anyonne got this working with HD4330?
lspci | grep VGA :
```
03:00.0 VGA compatible controller: ATI Technologies Inc M92 LP [Mobility Radeon HD 4300 Series]
```
Installed fglrx from repo after several unsuccessful attempts with the .debs
cat /var/log/Xorg.0.log | grep EE :
```
(EE) Unable to initialize PCS database
(EE)   Missing PCS defaults file /etc/ati/amdpcsdb.default
(EE) No devices detected
```

My /etc/ati folder only contain these files:
amdpcsdb   amdpcsdb.default.dpkg-bak  atiogl.xml.dpkg-bak

Lucid Beta1 on MSI WindBox DE200
Any ideas?

---

### Post by Cillean on 2010-03-23
@ Nakkar: I had the same problem. This should help:
```
sudo mv /etc/ati/amdpcsdb.default.dpkg-bak /etc/ati/amdpcsdb.default
```If you want to go sure, it's not going to hurt to rename the other file as well:
```
sudo mv /etc/ati/atiogl.xml.dpkg-bak /etc/ati/atiogl.xml
```That did the trick for me. The -5 drivers are running well here with my HD4650. However, GL seems to be broken somehow:
```
markus@mana:~$ LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: OpenDriver: trying /usr/lib/fglrx/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/fglrx/dri/swrast_dri.so
Error: couldn't find RGB GLX visual or fbconfig
```But I think this is just some error in my configuration. The second swrast_dri.so exists, so I don't know why it's complaining. I suppose I'll have to do some more investigation...

---

### Post by Nakkar on 2010-03-23
@ Cillean thanks,
but this returned the error from my karmic install with .660, that caused
my upgrade to lucid.
o.log:
```
(EE) fglrx(0): Invalid video BIOS signature!
(EE) fglrx(0): GetBIOSParameter failed
(EE) fglrx(0): PreInitAdatper failed
(EE) fglrx(0): PreInit failed
```

This seems to be a problem on ubuntu for others having dual gpu, one of them the HD4330.
but I only have the 4330...
The driver supposedly supports this chip.

Help appreciated.

---

### Post by TrueJournals on 2010-03-23
aviramof: Did you ever install the fglrx-modaliases package?  Looking through your log more, it appears that the X server can't find the fglrx module.  I have the packages fglrx, fglrx-dev, fglrx-amdcccle, and fglrx-modaliases installed, and everything's working fine.  The -dev package shouldn't be required, but installing it wouldn't hurt.  All these packages appear to be in the repository, so typing this in a terminal should install all of them:
```
sudo apt-get install fglrx fglrx-dev fglrx-amdcccle fglrx-modaliases
```
Once this finishes, run
```
dpkg -l | grep fglrx
``` and make sure all the version numbers are 2:8.721-0ubuntu5 (the latest version).  Finally, run ```
sudo aticonfig --initial -f
``` and reboot.  See if all that fixes your problem.

---

### Post by Cillean on 2010-03-23
@ Nakkar: Google led me to this post:

[http://www.linuxquestions.org/questions/showthread.php?p=3277660#post3277660](http://www.linuxquestions.org/questions/showthread.php?p=3277660#post3277660)

Maybe you could try if adjusting some BIOS settings solves the problem.


My own little problem is still persisting, although I already reinstalled fglrx. It's working if I rename the swrast_dri.so, but then I don't get direct rendering. I did some googling, and it seems that this problem happens rather often to owners of nvidia cards, but only rarely to fglrx users. It was fine in Karmic. Anyone an idea?

---

### Post by Nakkar on 2010-03-23
Unfortunately my BIOS has no graphics options at all...

---

### Post by Cillean on 2010-03-23
Alright, then I guess you're affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518802](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/518802)
I suppose you'll have to wait until it gets fixed...

I don't know if it's of interest to anybody, but I could finally solve my problem. The solution was rather straightforward:
```
sudo rm /usr/lib/libGL.so.1
sudo ln -s /usr/lib/fglrx/libGL.so.1.2 /usr/lib/libGL.so.1
```No idea why the new package didn't replace the libGL. Well never mind, now it's working perfectly :D

---

### Post by zengeos on 2010-03-23
Madspy,

Do you have ATI Catalyst Control center installed?
If you do, try running it.

That and another reboot seemed to get the new drivers functioning properly (perhaps it was my imagination though?)

Since your boot screen is ugly now, I think you have the ATI drivers mostly activated.

---

### Post by Madspyman on 2010-03-23
> **zengeos said:**
> Madspy,

Do you have ATI Catalyst Control center installed?
If you do, try running it.

That and another reboot seemed to get the new drivers functioning properly (perhaps it was my imagination though?)

Since your boot screen is ugly now, I think you have the ATI drivers mostly activated.

Yes I tried running it and it says this > "There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

Yet in hardware drivers it tells me I'm using "ATI Fire GL" and "This driver is activated and currently in use."

---

### Post by aviramof on 2010-03-23
> **TrueJournals said:**
> aviramof: Did you ever install the fglrx-modaliases package?  Looking through your log more, it appears that the X server can't find the fglrx module.  I have the packages fglrx, fglrx-dev, fglrx-amdcccle, and fglrx-modaliases installed, and everything's working fine.  The -dev package shouldn't be required, but installing it wouldn't hurt.  All these packages appear to be in the repository, so typing this in a terminal should install all of them:
```
sudo apt-get install fglrx fglrx-dev fglrx-amdcccle fglrx-modaliases
```Once this finishes, run
```
dpkg -l | grep fglrx
``` and make sure all the version numbers are 2:8.721-0ubuntu5 (the latest version).  Finally, run ```
sudo aticonfig --initial -f
``` and reboot.  See if all that fixes your problem.

i tried all of this and it's still not working well except a few more resolution on display nothing is as it should be i have no compiz every scroll i do refresh the entire screen and even in display all my screens are unknown basicly nothing works i don't even have catalyst in applications and etc.

is there a way to disable fglrx without removing it again?

thanks in advance.

---

### Post by Madspyman on 2010-03-23
Thanks Truejournals.

I just ran ```
dpkg -l | grep fglrx
``` followed by ```
sudo aticonfig --initial -f
``` rebooted and compiz and Catalyst control center work now.

Still have an ugly bootup but I assume that's a common problem.

I'll keep messing around to make sure everything works right.

---

### Post by uBeer on 2010-03-24
I just installed the fglrx driver to see if suspend/wake up would work a little better on my laptop, but I notice that there is still the backfill problem.

I tried looking for a patched xserver but I could not found one. Has anyone a PPA or package with a modified xserver package with the nobackfill patch?

On the side: I notice that my laptop gets a lot cooler with the fglrx driver instead of the open source driver and desktop effects seem smoother, though I get more screen tearing...

---

### Post by aviramof on 2010-03-24
i discoverd a good software today called ubuntu tweak there is a ppa there for xord-edgers fresh x crack does it help you?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by uBeer on 2010-03-24
> **aviramof said:**
> i discoverd a good software today called ubuntu tweak there is a ppa there for xord-edgers fresh x crack does it help you?

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Thanks for the reply and suggestion, but the xorg-edgers don't have a xserver with the patch, because it comes with a security risk apparently...

---

### Post by cheapsaket on 2010-03-24
> **uBeer said:**
> I just installed the fglrx driver to see if suspend/wake up would work a little better on my laptop, but I notice that there is still the backfill problem.

I tried looking for a patched xserver but I could not found one. Has anyone a PPA or package with a modified xserver package with the nobackfill patch?

On the side: I notice that my laptop gets a lot cooler with the fglrx driver instead of the open source driver and desktop effects seem smoother, though I get more screen tearing...

I did this by following this post: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256) 

when you get to this step: *cd xorg-server-1.6.3*

type in *cd xorg-server-*

and press TAB to autocomplete and choose 1.7.5 or the version you have.

Rest of the steps remain the same.

It might give a warning or error in the end (mine did) but its for gpg/pgp signing of the package generated which I did not have.

The package is generated and I was able to dpkg --install

---

### Post by uBeer on 2010-03-24
Dude, it's awesome! It works properly now! Thanks for putting the instructions!

---

### Post by aviramof on 2010-03-24
just to let you know i tried it and it didn't worked for me it has a lot of errors in the process.

---

### Post by aviramof on 2010-03-24
Five minutes ago ati have released ATI Catalyst 10.3 WHQL Display Driver or at least that was the time it was posted in one of my fast updating sites so let's hope that a gflrx driver would be releaed shortly.

---

### Post by cheapsaket on 2010-03-24
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

The X.org compatibility is still not showing 7.5

---

### Post by Cillean on 2010-03-24
The driver in the lucid repos is an early version of Catalyst 10.4, so the official release of 10.3 is of no use for the lucid testers ;)

---

### Post by emarkay on 2010-03-24
So are we ready to go or what?
When will we see it in the "Restricted hardware" install mode?

---

### Post by uBeer on 2010-03-25
> **aviramof said:**
> just to let you know i tried it and it didn't worked for me it has a lot of errors in the process.

You have to do the process from a folder with no spaces in the path. I made a folder "Xserver fix" in which I tried to do all the building, but that gave me an error. So I made renamed the folder to "Xserver" so the path became /home/beer/Xserver/. Then it would build with no problems.

---

### Post by aviramof on 2010-03-25
thanks for the info i would give it a try but in the mean while i need to install ubuntu again all this ati driver games crashed my ubuntu i restarted the computer and got a black screen and hd not running at all to start ubuntu but this time i'm going to install the dvd this might save me some software that i want have to install again.

---

### Post by xzero1 on 2010-03-25
> **lavinog said:**
> I haven't installed it on my current system yet, but how are the open source drivers.  From what I hear, the 3D support is pretty good on newer cards now.

I would suggest you try the default radeon drivers first. As for me, using a hd 4770 card, video playback is fine no obvious tearing, Nexuiz plays ok although not as smooth as before, and so far no lockups. Still, you will probably get more performance with ati's drivers and there is an annoying issue with improper gamma settings or something.

---

### Post by jaoc223 on 2010-03-25
I'm using an iMac 24" with  Radeon HD 2400 XT can I use the new ati catalyst driver? I just reinstalled lucid, and purged the nouveau driver and installed the opensource ati driver. My fonts look bad in chromium browser and firefox, would a new driver resolve font issues with these browsers? before I reinstalled lucid I had the ati open source driver install and it improved the fonts in the browsers, but this time around the improvement is minimal. do video drivers have anything to do with font rendering? or is the font rendering an issue in beta1?

---

### Post by QIII on 2010-03-25
> **cheapsaket said:**
> I did this by following this post: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/256) 


Which is great, but it is a work-around and not a solution.

---

### Post by pfanne on 2010-03-25
is there a "no backfill" ppa for lucid?
im to lazy to compile the xserver myself ;)

---

### Post by KdotJ on 2010-03-25
Without this driver can I still use the desktop effects and compiz? I mean can I still just use the proprietry ATI drivers?

---

### Post by QIII on 2010-03-25
In Lucid, you are likely to have problems with the current proprietary driver from the repos.  Although you can use work-arounds as discussed, this is not satisfactory compared to having the proper drivers.

I am using the open source driver right now with compiz  and the only complaint is that I can't get multiple Xserver sessions going so each one of my monitors is independent.  I just get one big desktop, and all of my monitors rotate when I rotate the cube.

(Oh, and Seamless Mode does not work in VirtualBox when you use multiple monitors as one large desktop.  But that is already a known issue with the folks at VirtualBox and they are working on it.)

Other than that, the open source driver is very good.  If not for that one thing, I'd just bag the proprietary driver all together.

---

### Post by myddewji13 on 2010-03-25
This might be a stupid question but I'm really not sure where to get the answer. How do I uninstall the proprietary drivers? Do I just remove the packages (which packages?) and reboot? And then does the system automatically use the open source drivers?

Reason I'm asking is because I really hate the boot up and the open source drivers are pretty good. The only thing I can't get going with the open source drivers is my resume from suspend. I'm guessing this might be fixed later on (since this is just the beta). If it is I'd much rather just use the open source drivers...

---

### Post by agaida on 2010-03-25
> **alphacrucis2 said:**
> Does it fix the slow window restore problem or do you still need the backclear patch?
No. You'll need the patch. But the patch is not available for lucid or i'm to dumb to apply it.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

---

### Post by svaens on 2010-03-25
> **agaida said:**
> No. You'll need the patch. But the patch is not available for lucid or i'm to dumb to apply it.[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]

aahhhhrrggh... I was so hoping that slow maximize/memory leak problem for ATI would be fixed by lucid ..  

Are all my hopes dashed ? 

Are the open source drivers a viable alternative for a laptop?

---

### Post by QIII on 2010-03-26
> **myddewji13 said:**
> This might be a stupid question but I'm really not sure where to get the answer. How do I uninstall the proprietary drivers? Do I just remove the packages (which packages?) and reboot? And then does the system automatically use the open source drivers?

The only stupid question is the one not asked.

On this forum you will find those who have much to learn and those who to learn much.

All of us still have much to learn.

To uninstall the proprietary driver, you can do a search in Synaptic for "fglrx" and "amdcccle" (no quotes of course) and mark them for removal.  It is possible that simply removing one or the other will take the second with it as a dependency.

When I had issues before I reported my bug on this, I simply used the terminal

```
sudo apt-get remove fglrx
```

Since I had also installed the Catalyst Control Center, I actually used

```
sudo apt-get remove fglrx fglrx-amdcccle
```

but you won't need the second if you did not install the Control Center.

---

### Post by svaens on 2010-03-26
and would that leave you with a working gui ? Or do you then need to do something to tell ubuntu to use the open source driver ? 

(sorry to butt in... )

---

### Post by myddewji13 on 2010-03-26
Removing the drivers resulted in the following:

- After restart I was presented with a dialogue which let me reconfigure X
- The fan is really loud (I'm installing fglrx again...)
- The boot is nice again (dammit why can't I have this with fglrx @#$@#$@$#@)
- I cannot resume from suspend....

---

### Post by bk109 on 2010-03-26
> **myddewji13 said:**
> Removing the drivers resulted in the following:

- After restart I was presented with a dialogue which let me reconfigure X
- The fan is really loud (I'm installing fglrx again...)
- The boot is nice again (dammit why can't I have this with fglrx @#$@#$@$#@)
- I cannot resume from suspend....
Yep,I had the same experience with the open-source drivers. When in doubt(or on a laptop), sadly, FGLRX is without a viable alternative. In normal usage it gives me twice the battery lifetime + a cool system when on AC when not in serious use. The flashy starting screen is a small price to pay.

Oh,yeah,and you're right,the whole Suspend/Hibernate thing didn't really work with the radeonhd drivers for me. I think only once I saw it resume from suspend, but that brought me a rather pleasant Kernel OOPS warning.

---

### Post by QIII on 2010-03-26
> **svaens said:**
> and would that leave you with a working gui ? Or do you then need to do something to tell ubuntu to use the open source driver ? 

(sorry to butt in... )

This should result in the use of the default open-source driver.  It's not perfect.

---

### Post by QIII on 2010-03-26
> **myddewji13 said:**
> Removing the drivers resulted in the following:

- After restart I was presented with a dialogue which let me reconfigure X
- The fan is really loud (I'm installing fglrx again...)
- The boot is nice again (dammit why can't I have this with fglrx @#$@#$@$#@)
- I cannot resume from suspend....

Except for the first, which is unusual but apparently you were able to fix it, that sounds reasonable.

Unfortunately, the fglrx proprietary driver seems to be a bit problematic right now.  There are work-arounds, but that is not the same as "fixed".  The same occurred leading up to Karmic, and was resolved by the final release.

Remember that a proprietary driver is just that.  Canonical has no control over it (and you are warned of that when you install it from Synaptic.)

But AMD/ATI has busted back side the last few releases to make sure that a working version of their latest driver is included in the Ubuntu repos.

Users of other distros just have to wait.

---

### Post by uBeer on 2010-03-26
> **pfanne said:**
> is there a "no backfill" ppa for lucid?
im to lazy to compile the xserver myself ;)

I'm too lazy to wait for my windows to appear, so I made a real simple script. If you do first all the sudo apt-get installs by hand, then you could use a script like mine and that will build and install a package for the xserver.

I first made a folder (with no spaces in it!) in which I put the patch file and my script. My script will then make another folder and download and process all the needed files in that folder. The next time you run the script it just removes that folder and creates it again. That way old stuff gets removed. 

Here's how it goes:
```

#!/bin/bash
# removes old folder and files and creates it again
rm -rf folder/
mkdir folder

# go into that folder and download the source of the latest xorg-server package
cd folder
apt-get source xorg-server
# enter the newly downloaded source
cd xorg-server-1.*
# copy patch for easy handling
cp ../../xserver-xorg-backclear.patch ./xserver-xorg-backclear.patch
# apply patch and build packages of the modified source
patch -p1 < xserver-xorg-backclear.patch
debuild
# go back one folder
cd ..
# and install the core packages
sudo dpkg --install xserver-xorg-core*.deb
# We're done!
echo done!
exit

```

You only have to put this in some text file with the extension .sh and make it executable by right-clicking it, click Properties. Then go to Permission tab and click Allow executing file as program.
Then double click it and click: "Run in terminal".

There you have it! Only remember to not let the update manager overwrite the packages that you've just created with the ones from the repository. Otherwise you're fine!

---

### Post by myddewji13 on 2010-03-26
I'm a bit confused. What is this patch that everyones talking about? I haven't had any problems just installing fglrx and amdcccle from the repos...

---

### Post by uBeer on 2010-03-26
> **myddewji13 said:**
> I'm a bit confused. What is this patch that everyones talking about? I haven't had any problems just installing fglrx and amdcccle from the repos...

Try to minimize and restore a window, try to open a big window like Firefox, try to resize a window, open (large) menus.

You should now see that these actions take a lot of your cpu and take a while to complete. That is because something in the fglrx driver doesn't work yet (I don't know the details). There is talk about it in the Phoronix forums that they're working on it, so a fix is maybe in the pipeline for the next driver update. Let's hope so!

---

### Post by ViperScull on 2010-03-27
Do they (fglrx pre 10.4 drivers) support kernels .33 and .34, or just .32?

---

### Post by aviramof on 2010-03-27
they worked for me on 33 but not so good.

---

### Post by myddewji13 on 2010-03-27
> **uBeer said:**
> Try to minimize and restore a window, try to open a big window like Firefox, try to resize a window, open (large) menus.

You should now see that these actions take a lot of your cpu and take a while to complete. That is because something in the fglrx driver doesn't work yet (I don't know the details). There is talk about it in the Phoronix forums that they're working on it, so a fix is maybe in the pipeline for the next driver update. Let's hope so!


It doesn't seem to be any different then usual. Nothing is so slow that I've noticed windows min/max etc taking its time and cranking the cpu...

---

### Post by autumnraine on 2010-03-27
I have a Radeon X1200 in my AMD netbook. Would this card be supported by the new proprietary driver, or does it only work for newer cards? (Sorry if this should be obvious.)

---

### Post by Cuppa-Chino on 2010-03-27
hi, has anyone got the new driver working with a mobility hd 5 series card? 

I am on an amd64 beta1 (fresh install last weekend) and fglrx driver segfaults with versions -1 to -5 . card I have is a mobility hd 5650 in a sony vaio laptop.

thanks for any pointers...

(before you ask it segfaults during boot and I did use aticonfig --initial) ;)

---

### Post by svaens on 2010-03-27
> **myddewji13 said:**
> It doesn't seem to be any different then usual. Nothing is so slow that I've noticed windows min/max etc taking its time and cranking the cpu...

you lucky ... lucky ... lucky ******* ... you .. lucky ...

---

### Post by AClark on 2010-03-27
@autumnraine
There is a list of supported hardware here:
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

Not sure how up to date it is.

Or you could install fglrx  with synaptic and then run 

```
sudo aticonfig --initial=check
```

in a terminal. If it's not supported you will get the dreaded "no supported adapters found" message 

Sadly the have dropped support for both of my Lucid machines and neither will resume from suspend.

Of course I am not sure that the suspend issue is caused by the graphics driver but in the past using fglrx has solved the suspend problem.

---

### Post by kommi on 2010-03-27
@Cuppa-Chino:
> hi, has anyone got the new driver working with a mobility hd 5 series card? 

I am on an amd64 beta1 (fresh install last weekend) and fglrx driver segfaults with versions -1 to -5 . card I have is a mobility hd 5650 in a sony vaio laptop.

thanks for any pointers...

(before you ask it segfaults during boot and I did use aticonfig --initial) :wink:I am on an amd64 beta 1 (with latest updates), acer laptop, mobility hd 5650 and have no problems with the fglrx -5 version. At least no segfaults during boot.

---

### Post by Cuppa-Chino on 2010-03-28
> **kommi said:**
> @Cuppa-Chino:
I am on an amd64 beta 1 (with latest updates), acer laptop, mobility hd 5650 and have no problems with the fglrx -5 version. At least no segfaults during boot.

ok great -- could you do me a favour and post the following:
* lspci -nn | grep Radeon
* xorg.conf

and let me know if you did anything special during installation - I do not think I have any odd software on my vaio (except the possible daft bios that sony might have inadvertently left on it)

---

### Post by myddewji13 on 2010-03-28
> **AClark said:**
> @autumnraine
There is a list of supported hardware here:
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

Not sure how up to date it is.

Or you could install fglrx  with synaptic and then run 

```
sudo aticonfig --initial=check
```

in a terminal. If it's not supported you will get the dreaded "no supported adapters found" message 

Sadly the have dropped support for both of my Lucid machines and neither will resume from suspend.

Of course I am not sure that the suspend issue is caused by the graphics driver but in the past using fglrx has solved the suspend problem.

Resuming from suspend was a problem for me too until I installed the fglrx drivers...so I'm assuming that it's graphics driver related....

---

### Post by yaji on 2010-03-29
Anyone tried to run some 3D games under Wine using this driver ? I did and every time I'm ending with something like that:

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  315
  Current serial number in output stream:  315

```

---

### Post by cheapsaket on 2010-03-29
Is it possible to use KMS with fglrx?

or alternatively:

Is there anyway to set the resolution that plymouth uses? Right now with fglrx, the splash screen showing UBUNTU 10.04 is using a very low resolution and I want to change that.

---

### Post by kommi on 2010-03-29
> **Cuppa-Chino said:**
> ok great -- could you do me a favour and post the following:
* lspci -nn | grep Radeon
* xorg.conf


lspci -nn | grep Radeon:
> 
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
02:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]xorg.conf:

> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2646 796
        Depth     24
    EndSubSection
EndSectionI did nothing special during installation. Only installed it via synaptic and then did aticonfig --initial.

---

### Post by myddewji13 on 2010-03-29
> **cheapsaket said:**
> Is it possible to use KMS with fglrx?

or alternatively:

Is there anyway to set the resolution that plymouth uses? Right now with fglrx, the splash screen showing UBUNTU 10.04 is using a very low resolution and I want to change that.

+1 I would like to know the answers to these questions too.

---

### Post by amano on 2010-03-29
> **cheapsaket said:**
> Is it possible to use KMS with fglrx?

or alternatively:

Is there anyway to set the resolution that plymouth uses? Right now with fglrx, the splash screen showing UBUNTU 10.04 is using a very low resolution and I want to change that.

No. Thats not possible. Currently fglrx doesn't support KMS and chances are that this will remain so in the future.

---

### Post by aviramof on 2010-03-30
i have just downloaded and installed 8.721-0ubuntu7 and it still not working fine with my HD3650 AGP 512 MB DDR2 SHAPPIRE card i'm starting to wonder if i would ever be able to work with linux with this card my problem is that one i don't have catalyst and two every mouse scroll refresh the entire screen and third all my screens are recognize as unknown in display any ideas as to what i can do?

thanks in advance.

---

### Post by littlesatan on 2010-03-30
I have HD3650 Mobility (512Mb) on my Acer 5920G, and if take no notice to a little overheating (60.0°C after boot up), the driver works quite well.

p.s. and of course, backfill problem still spoil my life.

---

### Post by swm5126 on 2010-03-31
I'm also having trouble getting games in Wine to work. If I run them from the terminal I get a similar message as to one of the previous posters. But when I actually double click a game exe (Borderlands for example) it will actually start to run but very distorted with what looks to be multicolored pyramids all over the screen?

---

### Post by ppp0 on 2010-03-31
ATI RADEON HD3240 - fglrx failed (

---

### Post by littlesatan on 2010-03-31
```
$ acpi -t
Thermal 0: ok, 81.0 degrees C
```
At idle system.

---

### Post by jngrim on 2010-04-01
> **ppp0 said:**
> ATI RADEON HD3240 - fglrx failed (

i couldn't get it to work either for HD3200  so did the following:

1. sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
2. reboot
3. sudo rm -r /etc/ati
4. sudo rm /etc/X11/xorg.conf*
5. Opened synaptics,  ad installed fglrx(it will reinstall dkms,and amdcccle)
6. Immediately after, open terminal: sudo aticonfig --initial
7. Reboot

---

### Post by jou770d on 2010-04-04
This is working fine for me on Asus M51va with HD3650 Mobility [512MBs]. Obviously after applying the backfill patch
I don't like the fact that we need to use such a workaround and that we seem to lose the ability to have an elegant splashscreen. But I can live with it I guess...

---

### Post by emarkay on 2010-04-04
Beta 2 almost here - what's the latest?  Anyone here still having problems with AMD/ATI hardware?

As I noted, I am waiting for the "Restricted Hardware" dialog to notify me that there is a driver available - 3D items not essential and I want to see that work flawlessly before release.

Will this be "activated" in Beta 2?

---

### Post by Autie on 2010-04-04
I get this with latest version:
```
E: /var/cache/apt/archives/fglrx_2%3a8.721-0ubuntu7_amd64.deb: subprocess new pre-installation script returned error exit status 2

```

---

### Post by grelbar on 2010-04-07
> **jngrim said:**
> i couldn't get it to work either for HD3200  so did the following:

1. sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
2. reboot
3. sudo rm -r /etc/ati
4. sudo rm /etc/X11/xorg.conf*
5. Opened synaptics,  ad installed fglrx(it will reinstall dkms,and amdcccle)
6. Immediately after, open terminal: sudo aticonfig --initial
7. Reboot

I can confirm this works. If i installed with apt-get, following the same steps, i'd get the "no compatible card found"-message, but with these instructions it works fine. Thanks

Using 32-bit Lucid Lynx Beta 1, with latest updates, 2.6.32-19 kernel.

---

### Post by Revord on 2010-04-07
@grelbar
I followed those steps, but still get no compatible card found with a x1650 card

---

### Post by NatePiercy on 2010-04-08
I've got the same issue, but jngrim's solution doesn't work for me. Whenever I get to the process of reinstalling fglrx (whether from synaptic or apt-get) I end up with the same error as Autie. Any ideas?

---

### Post by clhsharky on 2010-04-08
HI Revord

ATI X1650 is a legacy card, use 'Open Source Stack' radeon driver. Its the defalt install driver in Lucid for your card. Lucid+fglrx will not work on you chip.

Sharky

---

### Post by Revord on 2010-04-08
So, nothing short of getting a new card is going to work with this I assume. Thank you for the info :)

---

### Post by Seren on 2010-04-08
> **Revord said:**
> So, nothing short of getting a new card is going to work with this I assume. Thank you for the info :)

There is still hope. The open source driver is getting better over time.

Kernel 2.6.34 will include power management, there is a rewrite of the drivers going on currently using the Gallium stack, which could lead to improvements.

But if you want an ATI card using the fglrx driver now, you need to upgrade your card, or go back to the last Ubuntu version where you card was supported. (It is probably Intrepid or Hardy).

---

### Post by szoller on 2010-04-08
Tried the installation, too.
Used the drivers from repositories... installation ran fine,
inserted driver into xorg.conf, reboot...

No supported hardware :-/

My Notebook's got a ATI Radeon Xpress 1150 which ATI moved to legacy...

Now... i am also waiting for a working legacy driver...:confused:

---

### Post by monraaf on 2010-04-08
> **szoller said:**
> Tried the installation, too.
Used the drivers from repositories... installation ran fine,
inserted driver into xorg.conf, reboot...

No supported hardware :-/

My Notebook's got a ATI Radeon Xpress 1150 which ATI moved to legacy...

Now... i am also waiting for a working legacy driver...:confused:


Good luck waiting, but this just ain't gonna happen. Either use the open source drivers or downgrade to something like Ubuntu 8.10 and use an old version of Catalyst which does support your hardware.

---

### Post by aviramof on 2010-04-09
2:8.721-0ubuntu8 was released let's hope he's better then the previous one with my shappire card.

---

### Post by Cillean on 2010-04-09
@ aviramof: I've got a Sapphire card as well and the driver is working for me since -ubuntu5, so that's not a problem. I've had a look at your xorg.log and the driver is working for you, the only problem you have is that you don't have Direct Rendering enabled because there seems to be some problem with drm. You could try and remove **everything** related to fglrx from your machine and then installing it again via Restricted Hardware Manager.

---

### Post by aviramof on 2010-04-09
as far as i know i have nothing of gflrx still installed and yet i have nothing in Restricted Hardware Manager if i did i would have tried to install it from there long ago.  maybe later today i would try to download the dvd version of beta 2  and format and reinstall everything maybe then something would appear  in Restricted Hardware Manager but at the moment I'm only waiting for  ubuntu8 to appear in the synaptic repositories and see if it works.  do you have any idea why it said failed to build i386 in the ubuntu8 page?  and by the way in previous version ubuntu7 and before catalyst also didn't work for me.

---

### Post by Cillean on 2010-04-09
The Restricted Manager was updated quite a while ago, so usually, you should see the driver in there; the HD3650 is still supported.
Do you have all updates installed? You should do
```
sudo apt-get update
sudo apt-get upgrade
```and check whether you have jockey 0.5.8-0ubuntu6 installed.

---

### Post by aviramof on 2010-04-09
i do have  jockey 0.5.8-0ubuntu6 installed and all updates and i still can't see anything but once the dvd version of beta2 would be releasd i would format ubuntu and install everything again then will see.

---

### Post by ViperScull on 2010-04-10
Version 8.721-0ubuntu10 is in the repos.

But it requires to install also lib32gcc1 and libc6-i386. If i have a 64-bit system why do i need to install them?

---

### Post by clhsharky on 2010-04-11
HI


APR 11

> As a Sunday morning update, an updated fglrx-installer package has entered Lucid that provides a new upstream release. As is shared by this mailing list message, fglrx 8.723.1 fixes an issue with the X.Org Server causing a segmentation fault when certain ATI graphics cards are installed. There may be other changes too "under the hood" with this driver release, but that's all that is officially mentioned. 
[http://www.phoronix.com/scan.php?page=news_item&px=ODE0MQ](http://www.phoronix.com/scan.php?page=news_item&px=ODE0MQ)

> New upstream release:
     - Prevent the driver from causing X to segfault with
       certain cards (LP: #554191).
[https://lists.ubuntu.com/archives/lucid-changes/2010-April/010166.html](https://lists.ubuntu.com/archives/lucid-changes/2010-April/010166.html)


Sharky

---

### Post by aviramof on 2010-04-11
i have a problem with the latest gflrx driver and kernel 2.6.33:
[https://bugs.launchpad.net/bugs/560759](https://bugs.launchpad.net/bugs/560759)

---

### Post by clhsharky on 2010-04-11
HI aviramof

Cat 10.04 doesn't support kernel 2.6.33. Only supported releases. 'Lucid = kernel 2.6.32'

---

### Post by aviramof on 2010-04-11
so what all 2.6.33 kernel users would have to get bie with no ati driver?

and by the way it doesn't work so well in 2.6.32 compiz constantly freeze and movies 
don't play smoothly.

---

### Post by jymbob on 2010-04-11
> **NatePiercy said:**
> I've got the same issue, but jngrim's solution doesn't work for me. Whenever I get to the process of reinstalling fglrx (whether from synaptic or apt-get) I end up with the same error as Autie. Any ideas?

I too had this error. 64bit, Radeon HD 4870. **However:**

If you do the following:
```
sudo rm -r /usr/lib/fglrx
sudo rm -r /usr/lib32/fglrx
sudo rm /etc/default/xorg-driver-fglrx
sudo rm -r /var/lib/dkms/fglrx
sudo rm -r /bar/lib/dpkg/info/xorg-driver-fglrx.list
sudo apt-get clean
```
...it may work. Not exhaustively tested, you understand, but I at least have the driver working now. I can confirm that these are all recreated by a successful install.

I had also tried to install from the ati....run package. This can be uninstalled by running:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

Oh, also before reinstalling fglrx, completely remove fglrx-amdcccle, which will have partially installed when the fglrx install failed.

HTH

---

### Post by aviramof on 2010-04-11
now it doesn't work in 32 maybe because i have 33 installed.

---

### Post by Gi0tis on 2010-04-16
> **jngrim said:**
> i couldn't get it to work either for HD3200  so did the following:

1. sudo apt-get purge fglrx-modaliases fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx xorg-driver-fglrx-dev
2. reboot
3. sudo rm -r /etc/ati
4. sudo rm /etc/X11/xorg.conf*
5. Opened synaptics,  ad installed fglrx(it will reinstall dkms,and amdcccle)
6. Immediately after, open terminal: sudo aticonfig --initial
7. Reboot

Worked like a charm on 10.04.Thank you sir!

---

### Post by quini on 2010-04-16
@jngrim: it also worked for me... thanks!! :popcorn:

---

### Post by Kalibur on 2010-04-16
Hello 

Has anyone got it working on a Dell latitude xt?

---

### Post by blazemore on 2010-04-19
So what's the current state of affairs? All I want to do is play Runescape in high detail...

---

### Post by andrek on 2010-04-19
Speaking of the proprietary Catalyst driver, it just works as intended. I've set up Lucid beta 2 yesterday and used the 'Hardware drivers' to install the driver - no problems at all. I didn't really have to do anything specific - just one click [ 'Activate' ] and reboot.

And about the open-source driver - kernel 2.6.34 brings the power management, which is essential for me (laptop user). I'm eagerly waiting for the updates. If it comes out that it works just as good as the proprietary one, I'll switch to open-source -ati driver. If not, I'll stick with Catalyst.

---

### Post by blazemore on 2010-04-19
> **andrek said:**
> Speaking of the proprietary Catalyst driver, it just works as intended. I've set up Lucid beta 2 yesterday and used the 'Hardware drivers' to install the driver - no problems at all. I didn't really have to do anything specific - just one click [ 'Activate' ] and reboot.

Yes that works now. Used to crash at purple screen.
Performance actually seems worse than open-source -ati driver though. Surely this can't be right?

---

### Post by aviramof on 2010-04-19
i have a problem with that driver now my problem is that i can't run movies and compiz at the same time the movies jumps 
and freeze and even without movies compiz itself get a little stuck and freeze in animation i don't think i had that problem with 
Ubuntu 8.10 and it's fglrx driver. [FONT=Arial][SIZE=2][COLOR=#000099]

[/COLOR][/SIZE][/FONT]

---

### Post by blazemore on 2010-04-19
to be honest I've always had nothing but trouble with ati cards on Linux. I could never get vsync to work and always got tearing.

Anyone want to buy a Radeon 4700?

---

### Post by Dilutu on 2010-04-19
Works so so for me with an ati 2600 pro card. Performance is good but I get some tearing on fullscreen flash (youtube).Also when opening a vdo, screen goes black for a couple of seconds...
Th.

---

### Post by cottfcfan on 2010-04-20
Does anyone else get the flickering when opening Wine programs with catalyst 10.4, and at boot, and is there any workaround for this??

---

### Post by kjdixo on 2010-04-20
Has anyone succeeded getting ATI Catalyst 10.4 working with 3 or 4 screens in Lucid?
I have tried on Ubuntu Netbook and Xubuntu 10.04 Beta 2, without much success.
The best I can get is dual-head with two screens, both screens are connected to the Motherboard (Sapphire PI-AM2RS780G).
The plugin HD3450 has a 3rd screen connected and ready.
I had this hardware working perfectly with Xubuntu 8.10 and Catalyst 9.6.

On my new Xubuntu 10.04, after getting 2 screens working, I then tried to set up a 3rd screen by enabling surround view in the BIOS.
Okay so far, the 3rd screen can be positioned relative to Displays 1 and 2 in Catalyst.
Rebooting results in blank screens and the onboard cpu temperature display starts rising abnormally.

During my endless experimentations the following effects also occured.
1. The mouse cursor sat at the edge of both screens (where they meet) and flickered and didn't respond.
2. Displays locked with vertical green and blue stripes in front of a red speckled pattern on one display.
3. In Xubuntu when I repositioned a vertical XFCE panel across to the other monitor - the repositioned XFCE panel flashed and flickered.

To get out of these unresponsive situations I usually had to reboot and reconfigure the BIOS or do aticonfig in console mode, then go to Catalyst, then reboot etc etc.
After nearly a day of this I gave up trying.

My September 2009 posts [http://www.phoronix.com/forums/showthread.php?t=18180&page=2](http://www.phoronix.com/forums/showthread.php?t=18180&page=2) show that I can at least get it all working in Intrepid with Catalyst 9.6.

I am wondering whether I should wait until the new Linux 10.04 (29th April) and ATI Graphics Drivers are stable and officially released?

So now I have two working screens with windows draggable across the two screens.
The displays are set up as a Multi-Display with xinerama off (Catalyst says only one desktop is enabled so it has grayed-out the Xinerama option).

I would be interested to hear from anyone who has got the new version working with 4 screens.
Thanks.
Kevin Dixon

---

### Post by aviramof on 2010-04-20
the current fglrx driver is not the final one because officially ati 10.04 driver have not been released at all soon the driver would be released and then everything should work better.

---

### Post by RambJoe on 2010-04-20
Sorry if it's already been posted but where do I get these new drivers?

Thanks. :)

---

### Post by aviramof on 2010-04-20
once they would be released and the fglrx driver would be updated you would found
in jockey in system administrator.

---

### Post by kjdixo on 2010-04-20
Thanks for the information aviramof, that is what I thought.
I also tried uninstalling and reinstalling as described in other people's posts.
The reinstallations worked but did not fix my problems.
So I am happy to wait for the official releases.

RambJoe
This is the driver I have been using.
It is available from Synaptic Package Manager.
package             fglrx-amdcccle
installed version   2:8.723.1-0ubuntu2
description         Catalyst Control Centre for the ATI Radeon and FireGL graphics accelerators

As aviramof points out you will also find the driver in jockey in system adminstrator (Hardware Drivers in System menu in Xubuntu).
It will search for available drivers and allow you to install them.
Good Luck with that.

---

### Post by RambJoe on 2010-04-20
Thanks. :)

edit: Ah it finds the driver now when I open that hardware drivers thing, didn't before so they must have released it since. :)

---

### Post by scottiw2000 on 2010-04-21
The fglrx driver is installed and working for me with my hd4870 card, but the frame-rates are terrible (around 50 fps with glxgears). Docky, which is usually crisp and responsive is choppy and very sluggish. But my diagnostics show that the driver is working, direct rendering is enabled, etc. It's not my system, because I'm running an AMD Phenom quad-core with 8G of memory. Any idea what could be killing my frame-rates?

---

### Post by RambJoe on 2010-04-21
Hmm tessellation doesn't work either. :(

the 10.3 drivers are meant to have OpenGL 4, anyone know where Lucid Lynx get's drivers with that?

---

### Post by Chupalav on 2010-04-21
Hi

Have an "install archives() failed " error on my mobility radeon HD 5650 card. I`ve tried both to activate trough the hardware-drivers and to download package from ati website, but i didn`t succeed. Is there any known card-specific bug or it also happens due to unreleased driver and best solution is to wait a little bit?

---

### Post by aceracer24 on 2010-04-21
> **scottiw2000 said:**
> The fglrx driver is installed and working for me with my hd4870 card, but the frame-rates are terrible (around 50 fps with glxgears). Docky, which is usually crisp and responsive is choppy and very sluggish. But my diagnostics show that the driver is working, direct rendering is enabled, etc. It's not my system, because I'm running an AMD Phenom quad-core with 8G of memory. Any idea what could be killing my frame-rates?

I had the same issue when I installed the latest driver from ATI. I noticed the sluggishness right off the bat. Moving a window around was painfully sluggish.

---

### Post by RambJoe on 2010-04-21
Download fglrx-amdcccle from package manager. You then can also activate it in the hardware drivers as well once you've done that, not sure if you have to as I did that before I restarted.

---

### Post by aceracer24 on 2010-04-21
> **RambJoe said:**
> Download fglrx-amdcccle from package manager. You then can also activate it in the hardware drivers as well once you've done that, not sure if you have to as I did that before I restarted.

That was already installed but wouldn't work with the latest driver. It would come up saying that the device wasn't installed or properly configured....something to that effect. Nothing I did worked so I just removed it and the new driver and went back to the one that you activate on a stock setup.

---

### Post by Yellow Pasque on 2010-04-21
> **blazemore said:**
> Performance actually seems worse than open-source -ati driver though. Surely this can't be right?
The open-source drivers are significantly better at 2D (they use EXA) and run compiz very smoothly. The proprietary driver has much better 3D performance and more OpenGL features. ATI used to use XAA (old) for 2D, but now they're working on using a Direct2D-like system, which is better, but not as fast as EXA (yet).

---

### Post by scottiw2000 on 2010-04-22
Alright. But 50 fps on the glxgears test? That's not a 2d issue, and it's horribly slow on a card that should be doing much more. I have amdcccle installed, but I can't see any settings there that are the culprit. I've poked around a bit in aticonfig but, again, can't see anything that's obviously slowing me down. Are there some xorg.conf settings or something that are needed in addition to what aticonfig produces automatically (running aticonfig --initial)?

---

### Post by Yellow Pasque on 2010-04-22
What is output of:
```
fglrxinfo
```

---

### Post by scottiw2000 on 2010-04-22
fglrxinfo outputs this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series 
OpenGL version string: 3.2.9756 Compatibility Profile Context

If it's helpful, here's my xorg.conf:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "OpenGLOverlay" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by blazemore on 2010-04-24
Does anyone know why with the ATi driver installed, the Ubuntu logo in Plymouth is massive?

---

### Post by moviemaniac on 2010-04-24
> **blazemore said:**
> Does anyone know why with the ATi driver installed, the Ubuntu logo in Plymouth is massive?
Yes, fglrx doesn't support KMS thus Plymouth looks like sh**

---

### Post by aviramof on 2010-04-24
i had that problem too and then i didn't because the logo decided to disappear for no dapperness reason completely:lolflag:

now all i have is a purple background at startup.

---

### Post by screaminj3sus on 2010-04-24
> **scottiw2000 said:**
> Alright. But 50 fps on the glxgears test? That's not a 2d issue, and it's horribly slow on a card that should be doing much more. I have amdcccle installed, but I can't see any settings there that are the culprit. I've poked around a bit in aticonfig but, again, can't see anything that's obviously slowing me down. Are there some xorg.conf settings or something that are needed in addition to what aticonfig produces automatically (running aticonfig --initial)?

I get ~9800 on my mobility 2600 (with compiz enabled too)
9703 frames in 5.0 seconds
9741 frames in 5.0 seconds
9761 frames in 5.0 seconds
9877 frames in 5.0 seconds

Compiz, Docky, and awn are all smooth too.

And I havent configured anything with fglrx. I didnt even do an atconfig --initial and I haven't touched ccc.

---

### Post by Miguel on 2010-04-24
> **scottiw2000 said:**
> Alright. But 50 fps on the glxgears test? That's not a 2d issue, and it's horribly slow on a card that should be doing much more. 

If you see 50 or 60 fps in glxgears, chances are that somehow or somewhere vsync is enabled.

---

### Post by aviramof on 2010-04-24
I'm guessing that is not a very good result or is it? i'v used glxgears -fullscreen with compiz enable.

3464 frames in 5.0 seconds
3512 frames in 5.0 seconds
3534 frames in 5.0 seconds
3549 frames in 5.0 seconds
3560 frames in 5.0 seconds
3553 frames in 5.0 seconds

My card is HD3650 AGP 512MB DDR2 SHAPPIRE and i'm using fglrx driver from jockey.

---

### Post by splicerr on 2010-04-24
> **aviramof said:**
> I'm guessing that is not a very good result or is it? i'v used glxgears -fullscreen with compiz enable.

3464 frames in 5.0 seconds
3512 frames in 5.0 seconds
3534 frames in 5.0 seconds
3549 frames in 5.0 seconds
3560 frames in 5.0 seconds
3553 frames in 5.0 seconds

My card is HD3650 AGP 512MB DDR2 SHAPPIRE and i'm using fglrx driver from jockey.

If you've bought your video card for the sole reason of getting a very high frame rate printed in the terminal while watching some gears spin, then I suppose it's not a very good result.  Other people use their video card for other purposes. There are more realistic benchmarks to measure the graphics cards performance for these purposes, glxgears is certainly not one of them.

---

### Post by Yellow Pasque on 2010-04-24
> **Miguel said:**
> If you see 50 or 60 fps in glxgears, chances are that somehow or somewhere vsync is enabled.

Good call. This setting is controlled through Catalyst Control Center.

---

### Post by aviramof on 2010-04-25
> **splicerr said:**
> If you've bought your video card for the sole reason of getting a very high frame rate printed in the terminal while watching some gears spin, then I suppose it's not a very good result.  Other people use their video card for other purposes. There are more realistic benchmarks to measure the graphics cards performance for these purposes, glxgears is certainly not one of them.

any ideas on how i can do it here in linux?any software names and etc?
the point is to check my card in linux i already know that he works better with
windows and it's official ati drivers.

---

### Post by tokyobadger on 2010-04-25
[have you tried searching?](http://lmgtfy.com/?q=%22linux+benchmark+tools%22)

---

### Post by aviramof on 2010-04-25
nice trick thanks for the help.:)

---

### Post by Tuchkata on 2010-04-25
Hi. Some ideas about my problem : [http://ubuntuforums.org/showthread.php?t=1455586&highlight=2600+tearing](http://ubuntuforums.org/showthread.php?t=1455586&highlight=2600+tearing) ? It's annoying. When I watch streams or youtube I just have this tearing. I will update with 10.04 on Thursday. I hope you have some nice suggestions :)

---

