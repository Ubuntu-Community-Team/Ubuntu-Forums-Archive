---
title: "Has Alpha6 improved the Intel i965 video setup?  Also: AIRPRIME.KO update?"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jim March on 2008-09-22
My biggest issues with Alpha 6 involved video.  With minor tweaking I got Compiz working (don't recall what the tweak was, dammit, but it was minor).  However, GLXGears speeds sucked wind and some 3D games hard-locked - including very standard Linux stuff out of the Ubuntu repos such as Warzone2100.

VirtualBox did some video-related glitches too.

Has anyone noticed improved Intel (generally) or i965-specific improvements in Alpha6?

Plus there was a FREAKY sound issue with my Intel laptop sound: plug in a headphone and sound would fade to nothing until the next boot.  Was that sorted out??

On the plus side: Intepid A5's NM7 worked great; my Dell lappy long ago had it's Broadcom (puke) WiFi card yanked out and an Intel 4965AGN sweetness crammed in there, and NM7 loved it.  NM7 also worked with my Verizon USB-based cellmodem (USB720) to perfection.

Well unfortunately I just lost that USB cellmodem, and Verizon wants over $200 for another.  Screw that.  I found a used Kyocera KPC680 Expresscard which uses the airprime.ko driver.  By modprobing that driver and doing some other tricks I got it working at a somewhat crippled speed (maybe 1/4 of it's potential, but usable) BUT it dies after a small amount of data transfer or timeout.  This is a known issue with this critter and it has something to do with the airprime kernel module from what I gather so far.  

I'm back on Hardy at this moment.

What are the odds NM7 and/or the Intrepid 2.6.27x kernel will include support for the Kyocera 680 device and help unglitch that connection?

---

### Post by Nullack on 2008-09-22
The beauty of open source is that you can get involved to make a difference rather than rely on some company to do it. You can help drive what it does and how it works by contributing :)

---

### Post by Jim March on 2008-09-22
Bumping for an answer a bit more useful to a non-coder...?

Seriously, has there been any improvements to the i965 video drivers in Alpha6?  Does anyone know if that bizarre sound glitch is fixed?

I'll probably just have to test-drive the NM7 stuff...

---

### Post by andrewabc on 2008-09-22
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)

When running hardy xorg uses a lot more CPU which makes it unusable (there is lag when scrolling in firefox etc).
I tried alpha 6 livecd and compiz works great. Hardy uses around 90% CPU when firefox scrolling and it lags. With intrepid livecd it appears to only use 50-60% and not much lag. Which means if this continues I might be able to leave compiz on.

Intel g965 x3000

---

### Post by Nullack on 2008-09-22
> **Jim March said:**
> Bumping for an answer a bit more useful to a non-coder...?

Seriously, has there been any improvements to the i965 video drivers in Alpha6?  Does anyone know if that bizarre sound glitch is fixed?

I'll probably just have to test-drive the NM7 stuff...

You dont need to be a coder to install the Alpha, test it, and help report / work with bugs :)

Theres been quite a few intel video driver updates and other X related changes in the course of the alpha. These are listed in the commit logs for Intrepid.

---

### Post by lefthand on 2008-09-23
It looks like they've solved the bugs, at least from my end. glxgears runs normally for me again (450fps), the screen saver doesn't cause lock ups and there was a bug with boot up locking up which was also fixed.

Right now Alpha 6 is more stable for me that Hardy ever was.

---

### Post by Jim March on 2008-09-24
Well they've improved things...

GLXGears is now around 500 for me, used to be 900.  Warzone2100 crashed, but at least CTRL-ALT-F1 gets me a console prompt and I can do a "sudo shutdown -h now"... 

I'm going to try some of the xorg.conf hacks listed at:

[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)

...and see if I can tune it any better.  Failing that, it basically works (including Compiz) and they'll likely get it sorted by release time.

I'm also seeing random lockups that appear connected to the Verizon cellmodem connection.  I'll post on that separately.

Nullack: I do know how to file a bug report, and will be doing so on the Verizon KPC680 issue.

The Intel sound and video issues already had bug reports; I was just trying to get a fast answer on those issues as I need NM7 to get my cellmodem up.  Your first response was just...I'll be polite and leave it at "less than useful".

---

