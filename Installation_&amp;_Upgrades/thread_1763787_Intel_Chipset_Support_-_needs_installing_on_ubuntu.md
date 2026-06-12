---
title: "Intel Chipset Support - needs installing on ubuntu?"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-05-20
I recently had to reinstall a Windows 7 installation on a work computer. I used a commercial copy of the Windows 7 DVD. After installing the OS off the DVD though I had to download and install an .exe file gotten from the computer's manufacturer (Lenovo) called "Intel chipset support for Windows 7"

Do users ever have to download chipset support for Ubuntu? I didn't do this when I installed ubuntu on my computers, should I have? I'm wondering why there's a difference here? Ubuntu has this Intel chipset support natively available on the installation CD and Windows 7 did not? Seems like with a DVD Windows could fit everything you'd need for an installation to be complete.

Would my installation of ubuntu run better if I download Intel chipset support for the ubuntu versions I've already installed?

---

### Post by Hedgehog1 on 2011-05-20
Ubuntu install are not motherboard chip set dependent like windows, so there are not drivers for these.

In fact, you can move a disk with Ubuntu from an AMD system to an Intel system and only need to worry about the video driver.

You asked about your Ubuntu running better - are you having performance issues at this time?  Or were you just curious?


***The Hedge***

:KS

p.s. I have a Natty install an a fast USB stick that I keep generic videos drivers on - and I can boot from my home and office machines no matter the processor or chip set.  It really freaks the 'long time windows' folks out.

---

### Post by nrundy on 2011-05-20
I was just trying to understand, just curious :) 

So everything I need for a complete install of ubuntu on a computer that has Intel integrated graphics will be on the ubuntu installation CD? For the most part I don't need to worry about installing any additional drivers or chipsets or anything like that? Do I understand this correctly? 

So having to install Intel Chipset Support has no equivalent on an ubuntu installation?

That is really cool how easy it is to install Ubuntu! Coupled with how you can use Synaptic to install multiple applications at once, a re-installation of the OS is a breeze!

---

### Post by nrundy on 2011-05-20
> **Hedgehog1 said:**
> 

p.s. I have a Natty install an a fast USB stick that I keep generic videos drivers on - and I can boot from my home and office machines no matter the processor or chip set.  It really freaks the 'long time windows' folks out.

How did you amass generic video drivers on the USB? I'm assuming you put an ISO image on the USB and then added video drivers to it so you can "LiveCD" ubuntu on "foreign" computers when you want?

I have tried booting the "LiveCD" feature using a USB but couldn't get it to work. The computer seemed like it was unable to boot from USB. Are some computers unable to boot from USB?

---

### Post by Hedgehog1 on 2011-05-20
I don't amass the generic video driver(s), they are loaded at install.  Instead I never let the 'proprietary drivers' ever load.

If does sometimes mean I don't get the full performance from nVidia cards, but most systems at work have intel on board video or ATI video cards, and both of these work fine from the generic.

I get Unity on most machines from the USB install, but have to use 'classic, no effects' on nVidia based systems.

It still impresses folks, though.


***The Hedge***

:KS

p.s. I keep my hardware reasonably current (I buy at the 'sweet spot' of performance/price), so my systems all boot from USB.  At work all system boot from USB, too.  It is really sweet.

---

### Post by nrundy on 2011-05-20
Hedge do you think the "graphics problems" that Linux faces will ever get better? This article talks about the problems with updating drivers for new hardware  [http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1)

I don't understand it all but it sounds like a good system isn't in place to accommodate graphics driver updates?

---

### Post by Hedgehog1 on 2011-05-20
There is a practical limit to how much any release of any OS can carry 'drivers' (video and otherwise) at release time of the OS.

If you look at Windows and OSX, you can see two different solutions:

Windows is popular enough that MS can tell vendors who write drivers for their there own hardware add-ons "Here is the date, be ready".  Windows releases are also few and far between. 

Apple/OSX limits what hardware is supported, and works closely with those few vendors.

Linux as a desktop is still a small number of users.  We will not get the level of 'fast response' for drivers written by the vendors in most cases (NVidia bing a peasant exception).

Open source drivers are written by volunteers as they have time.  The truth is folks need paying jobs to pay the bills, and these efforts take longer (and many cases) than if 'paid engineers' were working on them 9-5.

I Don't see any real solution to the issue at this time.

***The Hedge***

---

### Post by nrundy on 2011-05-21
Oh, this makes sense. This is what I didn't quite understand. If the same manpower was put into writing the Linux graphics drivers as is put into writing the Windows graphics drivers, then Linux graphics would be has sharp as Windows? So it's prolly safe to assume that if Linux had a much larger user base, proprietary companies would likely devote more resources to writing both proprietary and open source drivers for it?

Thanks for explaining this.

---

