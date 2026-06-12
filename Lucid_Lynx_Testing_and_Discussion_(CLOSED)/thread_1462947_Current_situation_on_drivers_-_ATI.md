---
title: "Current situation on drivers - ATI?"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by BrokeMahPC on 2010-04-26
I was going to use Lucid - as it was a LTS - to push the benefits of Ubuntu with family and friends. Most have relatively new laptops or desktops with ATI Radeon HD or Mobility Radeon HD cards:
Newest intel i5 / Mob Radeon HD 5750
Oldest intel P4 / Radeon HD 4550

If I were to start handing out CD's I would not want them to have to start learning how to configure boot perameters, uninstall drivers, configure xorg right from the start as it would put them off, take up hours of my time, possibly make them ex friends / family!
As long as the display is working and doesn't crash I think we can work around other problems. From experience the display not working / crashing puts people off straight away.

So if they were to dual boot with Ubuntu - what is the situation with the ATI drivers at the moment.
Will radeon just work from 1st boot or not?

---

### Post by dino99 on 2010-04-26
if you look at threads asking about ATI problems, you can find a lot and there is no quick and easy solutions: depend on experience of user, chipset and if users request all the eyecandy stuff, well it might be far better if your friend/family ... have patience to wait let say end May, at that time the herd's bugger will slow down and lot of updates should have come.

In fact there is not so much improvements since karmic and if you think like pro whom always wait 1 or 2 months after release to upgrade, your friends and family should thanks you for your experience  :P

note: with recent hardwares, new kernel often bring nice solution with graphic troubles

---

### Post by rajeev1204 on 2010-04-26
> **BrokeMahPC said:**
> I was going to use Lucid - as it was a LTS - to push the benefits of Ubuntu with family and friends. Most have relatively new laptops or desktops with ATI Radeon HD or Mobility Radeon HD cards:
Newest intel i5 / Mob Radeon HD 5750
Oldest intel P4 / Radeon HD 4550

If I were to start handing out CD's I would not want them to have to start learning how to configure boot perameters, uninstall drivers, configure xorg right from the start as it would put them off, take up hours of my time, possibly make them ex friends / family!
As long as the display is working and doesn't crash I think we can work around other problems. From experience the display not working / crashing puts people off straight away.

So if they were to dual boot with Ubuntu - what is the situation with the ATI drivers at the moment.
Will radeon just work from 1st boot or not?


Hi
Yes i have a radeon 4850 and it works from 1st boot .

Try it out.And dont believe all the FUD on the forums about ATI, they are not all true, though some are.

Game performance is good with the proprietary drivers .Right now on lucid we have an early release of the catalyst 10.4 driver but its running good for me.
Compiz is laggy , the open source drivers run them better.
If you have a  laptop with the newer radeons , use the proprietary drivers due to power saver options which dont work well in the open source driver

User handy on this forum will give you a better idea on the current state of ATI open source drivers.Just search for his thread.


regards
rajeev

---

### Post by JCoster on 2010-04-26
I'm running an HD3650 using the *radeon* driver and am (for once) experiencing absolutely no problems with it.  Compiz is fast and smooth and video playback is flawless, even with flash.  Can't say the same for the *fglrx* driver.
JC

---

### Post by zika on 2010-04-26
> **JCoster said:**
> I'm running an HD3650 using the *radeon* driver and am (for once) experiencing absolutely no problems with it.  Compiz is fast and smooth and video playback is flawless, even with flash.  Can't say the same for the *fglrx* driver.
JCKnock on wood! +1 (same card)... (radeon & xorg-edgers)

---

### Post by aceracer24 on 2010-04-26
So with all of the above in mind, I am confused on what would be the better choice to make with a driver. I am running a 4870. I have been activating the proprietary drivers from the hardware menu. I have heard people mention other drivers such as radeon and radean HD as well as the fglrx drivers (proprietary driver??). Which are which and which would be the better driver to install? :confused:

I don't really play many games, at least not since installing Linux. So my goal is for the best driver that will play web content smoother such as videos as well as things on my desktop such as cairo-dock and compiz effects and of course DVDs. Any help would be greatly appreciated.

---

### Post by antenna on 2010-04-26
Sorry I can't help with the cards mentioned, but my HD4200 works perfectly with a default install.  Everything runs great. 

The 5750 in particular I'm not so sure.

---

### Post by antenna on 2010-04-26
> **aceracer24 said:**
> So with all of the above in mind, I am confused on what would be the better choice to make with a driver. I am running a 4870. I have been activating the proprietary drivers from the hardware menu. I have heard people mention other drivers such as radeon and radean HD as well as the fglrx drivers (proprietary driver??). Which are which and which would be the better driver to install? :confused:

I don't really play many games, at least not since installing Linux. So my goal is for the best driver that will play web content smoother such as videos as well as things on my desktop such as cairo-dock and compiz effects and of course DVDs. Any help would be greatly appreciated.

The proprietary drivers generally give you better 3D performance at a cost of often being less stable and not incorporating some of the latest features on Linux - KMS for example, which gives you a smoother boot experience.  If you don't want to play games, I would say you will be better off with the Radeon HD driver as it should be able to do everything you need.  Worth a try anyway, you can always switch back.  If you disable the proprietary drivers from the Hardware Drivers dialog, you should then be using the Radeon HD one.

---

### Post by JCoster on 2010-04-26
> **aceracer24 said:**
> 
I don't really play many games, at least not since installing Linux. So my goal is for the best driver that will play web content smoother such as videos as well as things on my desktop such as cairo-dock and compiz effects and of course DVDs. Any help would be greatly appreciated.

I may be totally wrong in this but the *fglrx* driver is the proprietary one provided by ATI.  The *ati*/*radeon* driver ships with Ubuntu and is open-source and maintained by the community.  The *radeonhd* is (or so my understanding goes) maintained by the X11 community and is open-source but compatibility isn't as good for older cards as the *radeon* driver.

The *xorg-edgers-ppa* provides development (near-nightly) builds of all the above drivers except the *fgrlx* driver which is updated once a month by ATI for Linux as a whole rather than just Ubuntu, so if you want to use an updated version of the *fglrx* driver rather than the one in the Ubuntu repos you have to download and compile that driver from the ATI site yourself.

I hope this explains a bit about the types of ATI drivers available.  For your needs, I'd recommend the *radeon* driver as the *fglrx* driver has a lot of ongoing issues and ATI are renowned around here for lack of support and help, although admittedly they have been getting better recently.

If I've made a mistake, anyone please correct me!

Cheers,
JC

---

### Post by zika on 2010-04-26
> **antenna said:**
> The proprietary drivers generally give you better 3D performance at a cost of often being less stable and not incorporating some of the latest features on Linux - KMS for example, which gives you a smoother boot experience.  If you don't want to play games, I would say you will be better off with the Radeon HD driver as it should be able to do everything you need.  Worth a try anyway, you can always switch back.  If you disable the proprietary drivers from the Hardware Drivers dialog, you should then be using the Radeon HD one.I'm not sure, but I think that radeonhd is, currently, non-KMS... At least in xorg-edgers, in Lucid, for my card, last time I checked, not so long ago, week or less... Why not, just, stick with radeon...?

---

### Post by antenna on 2010-04-26
> **zika said:**
> I'm not sure, but I think that radeonhd is, currently, non-KMS... At least in xorg-edgers, in Lucid, for my card, last time I checked, not so long ago, week or less... Why not, just, stick with radeon...?

Yeah, I think you may be right that Radeon is probably better right now.  I'm not sure about particular cards.

---

### Post by aceracer24 on 2010-04-26
Thanks guys for helping me to understand. So I should be able to just deactivate the proprietary driver which will revert me to the radeon or radeonHD driver? From there, depending on which driver it reverts me to, I can install from synaptic one over the other, preferring the radeon driver it sounds like. Is that correct?

---

### Post by BrokeMahPC on 2010-04-26
Not that simple - once you have installed fglrx there are several steps to uninstall it or it will interfere with radeon or radeonHD.
The radeon page has a section on removing fglrx:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

The radeonHD page that has further steps:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Troubleshooting fglrx interference - steps to nuke it thoroughly!:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I used the steps in the last guide - worked perfectly.
Checked the driver with the steps on the radeon page and its all set up correctly.

---

### Post by Yellow Pasque on 2010-04-26
The open-source drivers don't support any acceleration on RadeonHD 5000's yet, so unless you enjoy moving windows and having it look like an LSD experience (and you very well may), you have to use the proprietary driver.

For the HD4k series, the open-source driver works well unless you want to play some more advanced games through WINE.

---

### Post by BrokeMahPC on 2010-04-27
I have just reverted to the open source driver from fglrx again. The temperature problems are still there. Still can't monitor the GPU temp. Sensors-applet2.2.5 worked with fglrx but not with radeon - do I need to un-install and recompile it?

So to the new ubuntu (particularly laptop) user do we say:
Install and BTW - add  radeon.modeset=0  to your boot,
config ur xorg with ForceLowPowerMode and clockgating options,
or better still - compile yourself a new kernel - 2.6.34 for example.
After that it just works!
It's so simple they should understand that immediately!

I hope something is done about this - anyone got any news on it? Are ATI working on an fglrx that will work with KMS?

---

### Post by clhsharky on 2010-04-27
HI

> or better still - compile yourself a new kernel - 2.6.34 for examp

Not necessary deb right here
v2.6.34-rc5-lucid/
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc5-lucid/)

> Are ATI working on an fglrx that will work with KMS?
NO, proprietary drivers "ATI/NV" are are self contained in user space with everything needed, in UMS. Love it or hate it, thats the blob.

Skarky

---

### Post by Infil on 2010-04-27
I have a HD4570 Mobility, and Fglrx works for me but video playback is awful if Compiz is enabled. I would say the driver situation for modern ATi cards is not good.

clhsharky: Do I only need to install the newer kernel and then the radeon-driver will work, or do I have to use xorg-edgers and/or some boot parameters?

Does the problem exist also with the RadeonHD driver?

---

### Post by clhsharky on 2010-04-27
HI Infil

First off 
> video playback is awful if Compiz is enabled

Thats a known fact, but every now and then people get lucky and it works on there particular HW. So 1 click compiz is off.
I'll come back to this one. There is a lot of "crap" for lack of better description as to this doesn't work right.

>  I would say the driver situation for modern ATi cards is not good.
Lets see,
Intel - GMA500 driver is broken, and only patches to help but not available here yet. No performance chips. OSS drivers  but no docs.

VIA - ask any one with one if they are happy with it.

NVidia  - Do have the best blob drivers, still suffer from tearing and hardware issues. I lost 2 cards my self.

ATI - Has best hardware right now, fglrx blob is a workstation driver that home users swear at, best OSS drivers.

> Do I only need to install the newer kernel and then the radeon-driver will work
YES

>  do I have to use xorg-edgers 
No

> or some boot parameter
Maybe, you may need  radeon.dynpm=1  in the boot string

> Does the problem exist also with the RadeonHD drive
What problem are you talking about? RadeonHD and Radeon are OSS drivers and very similar. 

I'm old and slow so let me get back to you on fglrx&compiz.

Sharky

> video playback is awful if Compiz is enabled
I have no problem with video playback and compositor. Compiz is smooth.
OSS drivers of course

---

### Post by Infil on 2010-04-27
> **clhsharky said:**
> HI Infil

Lets see,
Intel - GMA500 driver is broken, and only patches to help but not available here yet. No performance chips. OSS drivers  but no docs.

VIA - ask any one with one if they are happy with it.

NVidia  - Do have the best blob drivers, still suffer from tearing and hardware issues. I lost 2 cards my self.

ATI - Has best hardware right now, fglrx blob is a workstation driver that home users swear at, best OSS drivers.

Thanks for your answer. I see that maybe it isn't so bad after all. I have been frustrated lately. I bought an expensive laptop this Christmas and have struggled to make it work in Ubuntu this whole time, so maybe the frustration got the best of me :)

> **clhsharky said:**
> 
YES

No

Maybe, you may need  radeon.dynpm=1  in the boot string


What problem are you talking about? RadeonHD and Radeon are OSS drivers and very similar.

The problem I was talking about is the problem with lack of power management and resulting overheating when using the radeon driver with certain chips, especially laptops. Maybe the yes and no answers you have will be different now?> **clhsharky said:**
> 

I'm old and slow so let me get back to you on fglrx&compiz.

Sharky


I have no problem with video playback and compositor. Compiz is smooth.
OSS drivers of course

The radeon drivers works perfetly for me as well, except the power management issue. When using fglrx the fan in my laptops runs less, as in Windows. With the radeon driver it runs at full speed all the time, except when I hit the silent button. I suspect this is the the power management comes in to play, where the fan runs slower but the chip does not.

---

### Post by ProNux on 2010-04-27
> **BrokeMahPC said:**
> I was going to use Lucid - as it was a LTS - to push the benefits of Ubuntu with family and friends. Most have relatively new laptops or desktops with ATI Radeon HD or Mobility Radeon HD cards:
Newest intel i5 / Mob Radeon HD 5750
Oldest intel P4 / Radeon HD 4550

If I were to start handing out CD's I would not want them to have to start learning how to configure boot perameters, uninstall drivers, configure xorg right from the start as it would put them off, take up hours of my time, possibly make them ex friends / family!
As long as the display is working and doesn't crash I think we can work around other problems. From experience the display not working / crashing puts people off straight away.

So if they were to dual boot with Ubuntu - what is the situation with the ATI drivers at the moment.
Will radeon just work from 1st boot or not?
I have Radeon 4850 on my Karmic PC.  At first, I cannot opea ATI Catalyst Control Center (administrative).  But there was a workaround on the ATI CCC properties on the Main menu.  Now I have no problem so far.  I also use Compiz Desktop effects.

---

### Post by Reiger on 2010-04-27
Maybe someone finds it instructive/entertaining:

My old laptop -until yesterday my workhorse- had:

Amd 64 flavour of Kubuntu Lynx, updated system last weekend.
Asus X51RL with an ATI Xpress 1100 motherboard: hence, it has an integrated Radeon 200M chip.

If I wanted to -reliably- boot to a usable system I had to edit /etc/default/grub to configure a timeout (in which to activate the Grub menu if I wanted to test with different boot parameters) and edit the default linux options to either pci=nomsi or radeon.modeset=0 in order to boot to a desktop at all.

If I choose pci=nomsi I get a KMS enabled system. Using VLC on some clips would guarantee a segfault. That particular segfault is hard to pinpoint because it is not contend with simply killing off VLC, it insists on killing off a shared Qt library that drives dbus connections. Which means it crashes my entire desktop session. Great.

If I choose radeon.modeset=0 the segfault does not occur at all. If I choose both options the segfault is back. So it seems to be an IRQ thing that `does' it.

By contrast my new laptop is a Studio 1558 ordered (one day?) before Dell ditched the Radeon 4570; so it has a 4570HD. I do not know what motherboard is inside, but it doesn't matter to me because: booting just works! No boot parameters, no nothing.

Well, except that Plasma/Dolphin crash a lot but that is a different problem and a different thread. That is the fault of the RC, which means plenty of updates to rectify that and create new problems elsewhere.

---

### Post by clhsharky on 2010-04-27
HI Infil

> Maybe the yes and no answers you have will be different now?
Radeon is newer than RadeonHD at the moment.
RadeonHD was made for R500/R600 chips, features were changing rapidly and it helped bridge the gap with out involving all other chips. It will be legacy.
Radeon supports all chips from R100/R700, and now has all the features radeonhd has.

> Quote:
Do I only need to install the newer kernel and then the radeon-driver will work
YES

> Quote:
do I have to use xorg-edgers
No

> Quote:
or some boot parameter
Maybe, you may need radeon.dynpm=1 in the boot string

> The radeon drivers works perfetly for me as well, except the power management issue.
Were you using kernel 2.6.34.rc5? thats where the PM with KMS is.

> With the radeon driver it runs at full speed all the time
Again was that with kernel PM in KMS.
Its reported the fan runs at 1/2 speed with kernelPM.
 
The BIOs control fan speed and CPU volts and many are adjustable.
The kernelPM controls power to video chip and memory.
CPU Frequency Scaling controls the CPU frequency.
Most modern mobiles computers have a separate on-board 'fan speed/temp censer' controller that the BIOs and software use.
fglrx has better PM and they been doing it for a while.
OSS KMS Power Management is just emerging, with tuning and scripting it will get better.

Sharky

If OSS Kernel Power Management isn't enough for you right now,by all means use fglrx.

---

