---
title: "Lucid does not support Poulsbo at all"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by war@rsb.at on 2010-03-13
Installing Lucid Lynx on a MSI 320 does not bring up the network, the screen defaults to 1024x768 (instead of 1300x800), wireless not recognised, SMC-device brings a constant flow of errors and timeouts (rendering the machine practically useless).

There is no way to report bugs any more (apport reports connection problems with crash database, web interface does not allow for adding bugs).

---

### Post by Keyper7 on 2010-03-13
Calm down, just wait until he apport issues are sorted, probably won't take long.

And you can still file bugs directly from Launchpad with +filebug.

---

### Post by slowpoke115 on 2010-03-17
Dont bother, the final thing on the bug listed [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-psb/+bug/330906") is 'won't fix' if you own a laptop with this driver, it's a lost cause - back to windows.

---

### Post by BrandonG777 on 2010-03-20
I know after all the nonsense of Quake @1080P on this chipset IN Linux it makes me seriously not want to EVER buy another Intel product again. The ultimate bait and switch.

---

### Post by oneguynick on 2010-03-22
> **BrandonG777 said:**
> I know after all the nonsense of Quake @1080P on this chipset IN Linux it makes me seriously not want to EVER buy another Intel product again. The ultimate bait and switch.

It will do that all day along...in Karmic :) I feel a sense of defeat as I wipe Linux from the drive and load the OEM Windows 7

---

### Post by Zorael on 2010-03-23
I think the problem here is that it's sort of out of the hands of the Intel linux crew. From [the Wikipedia entry](http://en.wikipedia.org/wiki/Poulsbo_%28chipset%29);
> [SIZE="4"]Graphics core[/SIZE]
The Poulsbo chipset contains a graphics core developed by Imagination Technologies. Intel has licensed the PowerVR SGX as a graphics core and the PowerVR VXD for H.264/MPEG-4 AVC playback. The video core is able to process 720p as well as 1080i resolutions.

[SIZE="4"]Linux support[/SIZE]
Although several netbooks using the Poulsbo chipset are shipped with some distribution of Linux (notably the Sony Vaio P and Dell Inspiron Mini 12, among others), Poulsbo's graphics core GMA 500 is currently not well supported by Intel for the Linux platform.

A proprietary driver was shipped with Dell's adaptation of Ubuntu 8.04.1 Netbook Remix, which provides 2D hardware acceleration (although users reported serious stability issues) under Linux kernel 2.6.24. A work in progress free driver is currently available, however the proprietary driver does not work with current Linux kernels and current versions of X. Work is under way to provide at least 2D support in current Linux kernels, although this will still rely on proprietary binary code for the 3D part of the driver. The current status of this driver runs on Fedora 10 and allows for 2D. 3D acceleration, however, is still broken.

Fedora 11 has a working driver developed.
So while it carries the Intel brand it's a PowerVR product, and the Intel linux guys' hands are as tied as anyone else's. They get one binary blob for linux and are told to work with it.

Now, the Intel management dudes who made the decision to license that proprietary graphics chipset, *them* I have a beef with. And obviously to a greater extent Imagination Tech. for not providing support to their customers.

---

### Post by argor on 2010-03-23
> **Zorael said:**
> I think the problem here is that it's sort of out of the hands of the Intel linux crew. From [the Wikipedia entry](http://en.wikipedia.org/wiki/Poulsbo_%28chipset%29);

So while it carries the Intel brand it's a PowerVR product, and the Intel linux guys' hands are as tied as anyone else's. They get one binary blob for linux and are told to work with it.

Now, the Intel management dudes who made the decision to license that proprietary graphics chipset, *them* I have a beef with. And obviously to a greater extent Imagination Tech. for not providing support to their customers.

:popcorn:
[http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux](http://en.wikipedia.org/wiki/Intel_GMA#GMA_500_on_Linux)
GMA 500 support on Linux is not optimal. The driver is developed by Tungsten Graphics, not by Intel, and the graphic core is not an Intel one, but is licensed from PowerVR. This has led to an uncertain mix of open and closed source 3d accelerated drivers, instability and lack of support.

Ubuntu is the Linux distribution that best supports GMA500 (Poulsbo), through the use of the ubuntu-mobile repository on Launchpad. Support is present for 8.04, 8.10, 9.04 and in an experimental way for 9.10, but the installation procedure is not as simple as other drivers and can lead to many bugs.[74]

Jolicloud, a linux based OS optimized for netbooks, has a driver for the GMA500 built in.

Intel releases official Linux drivers through the IEGD (Intel Embedded Graphic Driver) supporting some Linux distributions dedicated to the embedded market.

GMA500 is capable of running well in Ubuntu with Compiz visual effects activated[citation needed], and is the only Intel chipset supporting hardware accelerated video decoding (including h264) through libva-api.

In November 2009, the Linux Foundation released the details of a new, rewritten Linux driver that would support this chipset and Intel's other upcoming chipsets. The Direct Rendering Manager and X.org parts would be open source, but the 3D component (using Gallium3D) will still be closed.[75]

---

### Post by descendent87 on 2010-03-23
Tired installing lucid netbook edition beta 1 on my dell mini 10 but the gui is really slow and resolution won't set properly, shame as it works perfectly out the box on Jolicloud which is based on ubuntu

---

### Post by Cifra on 2010-03-23
The Poulsbo driver is a disgrace

---

### Post by descendent87 on 2010-03-23
Even good 2D & video performance would be better than nothing but as it is lucid is unusable with my mini 10, moblin is also a no-go which is a shame. Looks like I'll have to stick with Jolicloud for now, hopefully by the time lucid comes out there will be some improvement

---

### Post by SushiR on 2010-03-23
If it is helpful...Jolicloud (based on Jaunty) has full support for Poulsbo.

---

### Post by descendent87 on 2010-03-23
Seems mandriva 2010 (and 2010.1 which is currently in development) have out the box support for poulsbo so looks like that might be the best option at the moment.

---

### Post by penguin10916 on 2010-03-29
Jolicloud is pretty good.... but they need to make it far more stable than what it is... also, someone needs to create a common driver from the IEGD driver and perhaps the UNR team should consult and work with the Jolicloud developers to come up with a common fix for this problem... and yeah... I am never buying another Intel product... The computer I'm buying for college for next fall will use an AMD Phenom x4 at a bare minimum...

---

### Post by PendragonUK on 2010-04-14
Jolicloud works on my Aspire One AO751h out of the box, surely Lucid could do the same given that Jolicloud is a Ubuntu derived distro.

---

### Post by mikewhatever on 2010-04-14
> **PendragonUK said:**
> Jolicloud works on my Aspire One AO751h out of the box, surely Lucid could do the same given that Jolicloud is a Ubuntu derived distro.

Can you post the output of the following commands to verify your version of xorg:

dpkg -l | grep "xserver-xorg-core"

EDIT: Never mind. I've run Jolicloud from a usb stick, and the result is - 1.6.0. Do you know of any distro that supports the combination of 1.7.x and gma500?

---

### Post by luca.cappelletta on 2010-04-27
> **penguin10916 said:**
> Jolicloud is pretty good.... but they need to make it far more stable than what it is... also, someone needs to create a common driver from the IEGD driver and perhaps the UNR team should consult and work with the Jolicloud developers to come up with a common fix for this problem... and yeah... I am never buying another Intel product... The computer I'm buying for college for next fall will use an AMD Phenom x4 at a bare minimum...

Jolicloud is nice and GMA500 woks pretty well, but it's ****ing unstable !
so far it can't be a realistic substitute for ubuntu.

---

