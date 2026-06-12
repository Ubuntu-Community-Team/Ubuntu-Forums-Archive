---
title: "How can I change the ATI driver?"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by The Cog on 2009-04-17
I just installed Jaunty RC on a Dell D600 laptop which has this video adapter:
> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
Although most stuff works fine after I disabled the desktop effects, which crawled. But OpenOffice scrolling is intolerably slow. A single move of the scroll wheel can slam the CPU to 100% for up to 10 seconds while the picture jerks intermittently.

I have never seen this problem with other versions of OOo or Linux (been using Ubuntu on this lappy for around 4 years). I think it must be a video driver issue. I see in synaptic that I have xserver-xorg-video-radeon insalled. I would like to try whatever driver Intrepid was using and see if that's any better. If not, I guess I'll have to revert to Intrepid and hope that Karmic is better. Or I see there is a xorg-driver-fglrx in synaptic that is not installed.

How can I figure out which driver is currently in use, and how can I change which driver gets used? I see that neither Intrepid nor Jaunty have any mention of which driver to use in their xorg.conf files any more.

Edit:
Well, I installed xorg-driver-fglrx and rebooted, just to see what would happen. Aargh! I got a badly torn (unreadable) screen that I couldn't even drop back to a console with. I had to use a rescue disk and rename /etc/init.d/gdm in order to get to a text console and uninstall it again. Now I'm out of ideas.

---

### Post by Cybie257 on 2009-04-17
Is there a proprietary driver listed in the Hardware Drivers options? 

System->Administrator->Hardware Drivers

If it's there, enable it and you will be then using the ATI Proprietary drivers vs. the OpenSource. 

Otherwise, go to the ATI/AMD site and you can download the drivers from there. I prefer to use [www.ati.com](www.ati.com). It'll take you to the ATI portion of the AMD site. 

-Cybie

---

### Post by Reiger on 2009-04-17
If you want a driver from the repositories:
```

xserver-xorg-video-ati
```
should automatically provide the `right one'. Alternatively you can try the propietary drivers from AMD/ATI.

---

### Post by The Cog on 2009-04-17
Hardware Drivers says there are no drivers in use, and doesn't offer any for installing either.

The ATI site makes no mention of that model at all - like they never made them. 

Any otehr ideas would be welcome. It would be nice if I could find out which driver is actually in use, so I can compare my Intrepid driver with the Jaunty driver, and see if it's a change in the driver or if a completely different driver is in use.

---

### Post by Reiger on 2009-04-17
> **The Cog said:**
> Hardware Drivers says there are no drivers in use, and doesn't offer any for installing either.


No *propietary* drivers; hardware drivers only deals with those far as I know. ;)

> The ATI site makes no mention of that model at all - like they never made them.

It doesn't happen to be the All-in-Wonder 9000? Found at: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

> Any otehr ideas would be welcome. It would be nice if I could find out which driver is actually in use, so I can compare my Intrepid driver with the Jaunty driver, and see if it's a change in the driver or if a completely different driver is in use.

A combination of:
```

sudo aptitude search xserver-xorg-video-* | grep ^i #outputs a bunch of driver packages...

```
And 
```

dmesg | grep <insert_driver_name>

```

For instance:
(On my system)
```

sudo aptitude search xserver-xorg-video-* | grep ^i

```
Gives:
```

i   xserver-xorg-video-dummy        - X.Org X server -- dummy display driver
i A xserver-xorg-video-radeon       - X.Org X server -- ATI Radeon display drive
i   xserver-xorg-video-vesa         - X.Org X server -- VESA display driver

```
And:
```

dmesg | grep radeon
[code]
Gives:
[code]
[   41.764247] [drm] Initialized radeon 1.29.0 20080528 on minor 0

```

You will probably see a lot more driver packages (I have manually removed a boatload of 'em, keeping only what I need)...

... And each `miss' at dmesg | grep something-here will not output anything at all; which means the kernel hasn't been doing anything with it (loading it!); meaning you don't use it.

---

### Post by hblaw on 2009-04-17
Cog, I think ATI probably does not support your card any more - i.e. you won't have a workable proprietary driver for Jaunty. My card is X1250 and is not supported any more, and I have to use "radeon" or "radeonhd" driver (both open source) and the video performance is greatly reduced.

---

### Post by The Cog on 2009-04-19
Thanks for the help, folks. I am now certain that I am using the radeon driver, both on Intrepid (that works fine) and Jaunty (which has terrible repaint performance problems). 

I tried installing the fglrx driver from the ATI website, turned the RPM into a .deb with alien and installed it. It wasn't interested in the video adapter though, and the machine kept on using the radeon driver.

Another performance issue, I have noticed, is slow repainting of a page when I switch windows. I have a feeling the origin of the delay is the same as with scrolling in OOo, but that's just gut feeling.

I'll try reinstalling Jaunty when the release comes out, but I have a feeeling I will just remain on Intepid and perhaps chance my luck again with Karmic in 6 months time.

---

### Post by ktp on 2009-04-19
I have noticed big difference in the open source drivers from intrepid to jaunty.  The drivers worked great in intrepid but they seemed to have taken step back in jaunty.  Seeing lots of issues with screen refresh and performance is not good.  Hopefully it gets fixed in next release and new kernel.

---

### Post by krazyd on 2009-04-19
AMD has moved support for older chips completely to the open source driver. This includes the RV250 chip, so your card won't work with fglrx.

There are some reports of the older chips having problems with EXA acceleration which recently became the default with the open source driver.

Try adding this to the Device section of your xorg.conf:
```
Option          "AccelMethod"    "XAA"
```
(There may already be an AccelMethod line in there - if so, edit it so that it says XAA instead of EXA.)

Let us know how this goes.

---

### Post by ktp on 2009-04-19
I have been using EXA in both and jaunty things just seem not right...seeing lots of refresh issues and screen tearing.  Also seeing strip of "garbage" viewing high res images.  I am hoping things improve or at least go back to intrepid where I was so happy that I didn't even want to go back to fglrx.  

I have made thing little better by adding some extra options in xorg, but still not working right...but can live with it.

---

### Post by The Cog on 2009-04-20
> **krazyd said:**
> AMD has moved support for older chips completely to the open source driver. This includes the RV250 chip, so your card won't work with fglrx.

There are some reports of the older chips having problems with EXA acceleration which recently became the default with the open source driver.

Try adding this to the Device section of your xorg.conf:
```
Option          "AccelMethod"    "XAA"
```
(There may already be an AccelMethod line in there - if so, edit it so that it says XAA instead of EXA.)

Let us know how this goes.

krazyd, you are a star!!!

That fixes it for me so it's just as good as it was under Intrepid.
You've really made my day. Thank you.
<Skips off down the road, humming merrily.>

---

### Post by krazyd on 2009-04-20
Glad to be of service ;)

I think as the drivers mature (hopefully by 9.10) the EXA acceleration should improve and this workaround will no longer be necessary.

---

### Post by DougieFresh4U on 2009-04-20
If you don't mind, I would like to 'hijack' this thread now!!!
I have An AMD Athlon with onboard ATI Radeon HD 3200.
What drivers should be installed as there are a couple of them for ATI in 'Synaptic' that are installed, both ATI and Radeon. I am trying to get 'Desktop Effects' to work, but I am using the .30rc2 kernel and 'fglrx' does **NOT** work with that kernel and will seriously 'bork' machine. (fresh install caused from said 'bork')
Thanks for any help and please give any codes for any info you may need to assist.

---

### Post by krazyd on 2009-04-20
The open source drivers don't yet support 3D acceleration for your card, so for desktop effects your only option is to try to get fglrx working.

There is a new version of fglrx (9.4) available from [AMD]("http://support.amd.com/us/gpudownload/Pages/index.aspx"), though you'll have to install it manually because it's not in the repositories. (Edit: just realised you're using a custom kernel. I think you'll have to just wait until after .30 is released - fglrx support for it will probably follow.)

If that fails, you may have to wait for 9.10 for desktop effects (open source should have acceleration for your card by then).

---

### Post by DougieFresh4U on 2009-04-20
> **krazyd said:**
> The open source drivers don't yet support 3D acceleration for your card, so for desktop effects your only option is to try to get fglrx working.

There is a new version of fglrx (9.4) available from [AMD]("http://support.amd.com/us/gpudownload/Pages/index.aspx"), though you'll have to install it manually because it's not in the repositories. (Edit: just realised you're using a custom kernel. I think you'll have to just wait until after .30 is released - fglrx support for it will probably follow.)

If that fails, you may have to wait for 9.10 for desktop effects (open source should have acceleration for your card by then).

Thank you.:D

---

### Post by Adahn on 2009-04-20
What version of fglrx is supposed to install with jaunty?
I upgraded from intrepid and version 8.6 has been retained (Radeon 3850).

---

### Post by DougieFresh4U on 2009-04-20
> **DougieFresh4U said:**
> If you don't mind, I would like to 'hijack' this thread now!!!
I have An AMD Athlon with onboard ATI Radeon HD 3200.
What drivers should be installed as there are a couple of them for ATI in 'Synaptic' that are installed, both ATI and Radeon. I am trying to get 'Desktop Effects' to work, but I am using the .30rc2 kernel and 'fglrx' does **NOT** work with that kernel and will seriously 'bork' machine. (fresh install caused from said 'bork')
Thanks for any help and please give any codes for any info you may need to assist.

Could some one please answer my questions as to which drivers in 'Synaptic' need to be installed as there are a couple and I also getting strange message from terminal
```
dougie@DougiesLeanMachine:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
```
```
dougie@DougiesLeanMachine:~$ glxinfo |grep vendor
unknown chip id 0x9610, can't guess.
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project
```
```
dougie@DougiesLeanMachine:~$  glxinfo | grep "direct rendering"
unknown chip id 0x9610, can't guess.
direct rendering: Yes
```

---

### Post by Reiger on 2009-04-20
> **Adahn said:**
> What version of fglrx is supposed to install with jaunty?
I upgraded from intrepid and version 8.6 has been retained (Radeon 3850).

Get the official AMD 9.4 package -- not the beta from the repositories. The official one works rather better.

That also answers the last question (of the poster below you): if you want fglrx go get the AMD version (*not* from Synaptic). Otherwise the following drivers may be of interest (from Synaptic)
xserver-xorg-video-radeon
xserver-xorg-video-ati
xserver-xorg-video-radeonhd

Make sure to read up on which devices are supported (using aptitude show for instance)

---

