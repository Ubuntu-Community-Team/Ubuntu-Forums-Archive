---
title: "Radeon 9550 driver"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by Zirts on 2010-08-05
Hi,

I'm currently using ATI Radeon 9550 with a non proprietary driver.
Ubuntu 10.04

Typing glxgears in Terminal gives me this:
3918 frames in 5.0 seconds  #With the little screen
966 frames in 5.0 seconds   #Full screen

So basicly this shows allready that something is pretty wrong.
I have searched the AMD website for some proprietary drivers too and I found some also, but their last release was around 2009.

Also when I got the driver downloaded and did a 
sh ./ati-driver-installer-9-3-x86.x86_64.run --listpkg
I discovered that it doesen't list Ubuntu 10.04, the latest one is the 09 one. There are some other choices there too but I'm not sure about them.
```

Package Maintainer(s): Mario Limonciello <superm1@gmail.com>
                      Aric Cyr <aric.cyr@gmail.com>
Status: *UNVERIFIED*
Ubuntu Packages:
	Ubuntu/7.10
	Ubuntu/8.04
	Ubuntu/8.10
	Ubuntu/9.04
	Ubuntu/gutsy
	Ubuntu/hardy
	Ubuntu/intrepid
	Ubuntu/jaunty
	Ubuntu/source


```

The problem for me righ now is that I cant even play a simple game like Runescape normally. I have to run it on the lowest settings and even then the speed of the game is not satisfying. Also I'm not able to switch out of the "Safe Mode" in the grapics option.
I understand that if I want to play a game like DotA, I have to face it that it's not possible to play it on a competitive level anymore as WINE takes it's share on FPS.

But really, something is very wrong with the drivers I think when even Runescape is slow, also flash videos run slow and youtube videos too, wich are flash too I guess but I still mentioned it.

My java is on it's latest version too.

Is there any point to continue trying to install the proprietary driver? Also if I tyred to install it, the 6 packages ran into some "Broken package" problems.

Also glxinfo output:
```
kaspar@kaspar-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

I hope someone can give me some advice.
Tell, if some more info about my configs or machine is needed.

Zirts

---

### Post by gordintoronto on 2010-08-05
What is your CPU? The speed of Flash is almost entirely a result of your CPU, not your video card.

---

### Post by Icarus315 on 2010-08-05
Zirts,

Here is the situation.  Ati discontinued driver support for pre-HD 2000 series hardware.  They left the legacy driver for anything older than HD 2000 series hardware.  Your hardware falls into this legacy category.  The issue is that in Ubuntu 10.04 other things such as the X windows system has changed enough that that legacy driver no longer operates with it.  This means you have to use the Open-Source Ati driver for your hardware.  The Open-Source driver is a work in progress.  While more than adequate for desktop tasks like compiz it does not work well for games yet.  To use the proprietary driver with your hardware, you need to go to an older distribution of Ubuntu, you've seen the output with "listpkg" of what is supported.

In addition, you say you have no option but to boot into X's safe mode?  This indicates that the Open-Source Ati driver is not properly configured as well, someone else will have to help you with that - sorry.

---

### Post by Zirts on 2010-08-05
My CPU is a AMD Sempron 3000+ 
Cache size: 128kb
Frequency: 1808.00GHz

Also I have 1024 MB of RAM

With only Google Chrome opened I'm having a constant stream of 8% CPU usage.

What Icarus315 say'd is very intresting, I indeed have never touched thoes open-source-driver s my self, the drivers were automaticly installed and configured too I guess by Ubuntu.

If someone could tell me how to get to thoes open-source drivers and play around with them I would be more than pleased.

Zirts

---

### Post by Icarus315 on 2010-08-05
If you are using the drivers that Ubuntu 10.04 set-up on install then you are already using the Open-Source drivers.  Because your hardware is pre-HD 2000 series you will not be able to use the proprietary drivers with Ubuntu 10.04.

For logging into the graphical desktop, what do you mean by "safe mode", do you get a message saying "Low Graphics Mode" or something similar?  Or do you just go to a graphical desktop beginning with the log-on (you may have set it up so that the log-on is automatic) with no messages displayed?

---

### Post by Zirts on 2010-08-05
I'm sorry, I think there was a little miss understanding here now.

The g desktop safe mode is fixed long time now, but I was talking about Runescapes graphics settings. There you can choose to use OpenGL, DirectX, Safe mode. I'm only able to use safe mode, but now it really seems to me that theres really nothing to do about it then.
Just have to hope that maybe on one day the open-source driver will get a bit better for my card.

Thanks for the help anyway.

Zirts

---

### Post by gordintoronto on 2010-08-05
> **Zirts said:**
> My CPU is a AMD Sempron 3000+ 
Cache size: 128kb
Frequency: 1808.00GHz

With only Google Chrome opened I'm having a constant stream of 8% CPU usage.


What is the CPU usage when you are watching a video on youtube? I'm betting it's above 50%, if you go for the HD version.

---

### Post by Zirts on 2010-08-18
Yes, pretty much so. It ranges from like 50%-60%

---

