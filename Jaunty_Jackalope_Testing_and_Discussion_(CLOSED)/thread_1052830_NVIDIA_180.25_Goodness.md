---
title: "NVIDIA 180.25 Goodness"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-01-28
So, I compiled 180.25's module and had the celebratory beer during the ritual.......all seems good :) Mostly GPU decoder fixes with vdpau but theres soom other fixes too.

---

### Post by plun on 2009-01-28
Yup... excellent driver  !  ;)

---

### Post by olskar on 2009-01-28
How does this with graphicsdrivers work? What version will be in final januty? The last one released before featurefreeze?


Edit: Btw plun, regarding the "You can fly"-video in your signature; "This video is no longer available due to a copyright claim by BBC Worldwide Ltd.. " :(

---

### Post by plun on 2009-01-28
> **olskar said:**
> How does this with graphicsdrivers work? What version will be in final januty? The last one released before featurefreeze?


Edit: Btw plun, regarding the "You can fly"-video in your signature; "This video is no longer available due to a copyright claim by BBC Worldwide Ltd.. " :(

Well...this driver is just great and after my infraction I am never going to lift a finger about file a bug about it.  

Compared with Intel and ATIs crappy drivers this is just excellent !  even more crappier for the open source variants !

--------------------

Thanks for the hint about BBC.....   Moonlight URL with DRM protection next step maybe ...:twisted:

---

### Post by mirhciulica on 2009-01-28
Great driver. It makes my laptop very smooth and fast, also! :X

---

### Post by Nullack on 2009-01-28
.27s out allready

---

### Post by Starks on 2009-01-28
Will the legacy drivers be fixed for xserver 1.6?

---

### Post by caryb on 2009-01-28
Just installed .27 on my laptop, It took 3 installs to get it to go! (don't read anything into that as my machine has been a pig since I rebuilt it & complains of broken symlinks on NV install) but now it's going all is good. My cube screen works again:D


Cary

---

### Post by cl333r on 2009-01-29
imo VDPAU is a critical step towards broader Linux desktop adoption.
A VDPAU enabled Linux box without significant glitches - is one of Microsoft's worst nightmares. Those who understand the desktop market know the big (positive) impact it can have on Linux.
IMHO top three must-have issues which the desktop Linux currently doesn't provide were "games, certain rich apps, hi-def video", now the list shrinks to just "games, certain rich apps".

---

### Post by JohnJackson on 2009-01-29
> **Starks said:**
> Will the legacy drivers be fixed for xserver 1.6?

According to this [Phoronix article]("http://www.phoronix.com/scan.php?page=article&item=nvidia_18025&num=1"), they have initial support for 1.6.

---

### Post by forcecore on 2009-01-29
does that fixes horrible slow 2d rendering?

---

### Post by mirhciulica on 2009-01-29
Fresh install of 9.04 and 180.27 NVidia driver... Great :KS
As **JohnJackson** is saying, 180.27 has support for XServer 1.6! :popcorn:

---

### Post by plun on 2009-01-29
The mplayer/ffmpeg/VDPAU script including patches was also updated.

[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

Note  !  **Download within last message !**

Just to run the build script.

---

### Post by punischdude on 2009-01-29
> **mirhciulica said:**
> Fresh install of 9.04 and 180.27 NVidia driver... Great :KS
As **JohnJackson** is saying, 180.27 has support for XServer 1.6! :popcorn:

It's the legacy driver he's talking about, 180.25 and 27 do not have any official 1.6 support, if I'm not completely mistaken.

---

### Post by mirhciulica on 2009-01-29
> **punischdude said:**
> It's the legacy driver he's talking about, 180.25 and 27 do not have any official 1.6 support, if I'm not completely mistaken.

Noo! I have downloaded 180.27 from NVidia ftp and installed. I didn't have to edit my xorg.conf in order to make use of the driver. Give a try, without ignoreABI ;)

---

### Post by Vaun on 2009-01-29
Very nice.  I forgot about that IgnoreABI option in my /etc/X11/xorg.conf as it's been there for some time.  Very true it's no longer needed with 180.27.  Good catch.

---

### Post by tseliot on 2009-01-29
All the new NVIDIA drivers (180.27 and the legacy drivers) will be available soon. Don't worry ;)

---

### Post by Gourgi on 2009-01-29
thanks alberto :-D
good to know

---

### Post by punischdude on 2009-01-29
> **mirhciulica said:**
> Noo! I have downloaded 180.27 from NVidia ftp and installed. I didn't have to edit my xorg.conf in order to make use of the driver. Give a try, without ignoreABI ;)

Indeed, but that's why I said there's no _official_ support.

Even [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=nvidia_18025&num=1") says: > What the NVIDIA 180.25 Linux driver lacks, however, is official support for X Server 1.6.

Sry for splitting hairs ;)

---

### Post by plun on 2009-01-29
> **punischdude said:**
> Indeed, but that's why I said there's no _official_ support.

Even [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=nvidia_18025&num=1") says: 

Sry for splitting hairs ;)

Well... its difficult to officially support something which isn't released.

Phoronix about Xserver 1.6

***The State of X Server 1.6: Still Missing***

[http://www.phoronix.com/scan.php?page=news_item&px=NzAxOA](http://www.phoronix.com/scan.php?page=news_item&px=NzAxOA)

---

### Post by afv on 2009-01-29
180.27 already in the repositories :)

*Rebooting*

---

### Post by mgsfan on 2009-01-29
just updated to .27 and I still need ignoreabi

---

### Post by thonuz on 2009-01-29
I am wondering how this new driver does on laptop battery life and CPU usage. I have a Vaio with choice of Intel or Nvidia. For me the Intel always worked smoother. Less fan rpms , better battery life and so forth.
Switching between the 2 modes is not easy and requires 2 xorg.conf and some editing. Also fonts have always looked better using the Intel driver. Is that 2D? I don't know.

---

### Post by mirhciulica on 2009-01-30
> **punischdude said:**
> Indeed, but that's why I said there's no _official_ support.

Even [Phoronix]("http://www.phoronix.com/scan.php?page=article&item=nvidia_18025&num=1") says


You're right! I'm a moron#-o

---

### Post by Branimir on 2009-01-30
Well, Ive installed 180.27 as usual when nvidia puts new
driver in [ftp://download.nvidia.com/XFree86/](ftp://download.nvidia.com/XFree86/)

Cleaned my systm from proprietary drivers from ubuntu repository.
It now says I don;t use any proprietary drivers in system.
Yeeeey!

Greetsa, Branimir.

---

### Post by lamborghiniwang on 2009-01-30
The 180.27 driver works really well in my system. Now only if I could find a working (s)mplayer that supports vdpau...

---

### Post by gmclachl on 2009-01-31
> **afv said:**
> 180.27 already in the repositories :)

*Rebooting*

Not for me, I seem to be stuck with 180.22. I would have thought it would have made it's way to the UK server by now

---

### Post by MacUntu on 2009-01-31
> **gmclachl said:**
> Not for me, I seem to be stuck with 180.22. I would have thought it would have made it's way to the UK server by now

It isn't in the repositories yet: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180)

---

### Post by jfernyhough on 2009-01-31
It's not in the /official/ repos yet. It's in Anders' PPA:

```
## nvidia
deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
```

Needless to say, don't file bug reports on this one.

Oh, plus with using 180.27 I don't need IgnoreABI. :D

---

### Post by AaronP_ on 2009-01-31
> **jfernyhough said:**
> It's not in the /official/ repos yet. It's in Anders' PPA:

```
## nvidia
deb http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
# deb-src http://ppa.launchpad.net/anders-kaseorg/ubuntu jaunty main
```

Needless to say, don't file bug reports on this one.

Oh, plus with using 180.27 I don't need IgnoreABI. :D
That's right, it is supported without ignoreABI, I just forgot to mention it in the release notes.

---

### Post by taavikko on 2009-01-31
> **AaronP_ said:**
> That's right, it is supported without ignoreABI, I just forgot to mention it in the release notes.

Isn't it supposed to support new Xorg, instead of just one option?

I'll presume your the AaronP_ from Nvidia?

---

### Post by AaronP_ on 2009-01-31
> **taavikko said:**
> Isn't it supposed to support new Xorg, instead of just one option?

I'll presume your the AaronP_ from Nvidia?
I'm not sure what you mean.  The X server ABI for what will eventually be xserver 1.6 is frozen, and 180.25 and 180.27 both officially support it without any special options.

Yes, I'm the AaronP from NVIDIA.  "AaronP" without the underscore was already taken here.

---

### Post by Gina on 2009-01-31
> **AaronP_ said:**
> Yes, I'm the AaronP from NVIDIA.  "AaronP" without the underscore was already taken here.It's great to see someone from NVIDIA reading and posting here :) Thank you :) :)

---

### Post by ronacc on 2009-01-31
> **AaronP_ said:**
> I'm not sure what you mean.  The X server ABI for what will eventually be xserver 1.6 is frozen, and 180.25 and 180.27 both officially support it without any special options.

Yes, I'm the AaronP from NVIDIA.  "AaronP" without the underscore was already taken here.

And thankyou for the linux drivers you at Nvidia keep providing despite the bashing you get from some for not open sourcing .Your work is appreciated , not all of us are "idealogicly pure" .

---

### Post by Gina on 2009-01-31
I second all of that.

---

### Post by IanW on 2009-02-01
> **ronacc said:**
> and thankyou for the linux drivers you at nvidia keep providing despite the bashing you get from some for not open sourcing .your work is appreciated , not all of us are "idealogicly pure" .

+1

---

### Post by Asraniel on 2009-02-01
i really hope by the way that the older drivers get in with support for the new xserver. Because my computer has a geforce4, and currently has no 3d support. and nouveau does not seem to work (the version in jaunty)

---

### Post by AaronP_ on 2009-02-01
> **Asraniel said:**
> i really hope by the way that the older drivers get in with support for the new xserver. Because my computer has a geforce4, and currently has no 3d support. and nouveau does not seem to work (the version in jaunty)
GeForce 4s are supported in 96.43.10, which also supports the new X server.  See [Appendix A]("ftp://download.nvidia.com/XFree86/Linux-x86/180.27/README/appendix-a.html") in the README for the complete list of what's supported where.

---

### Post by plun on 2009-02-01
Thanks Alberto !!!  ;)


[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004264.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004264.html)


> nvidia-graphics-drivers-180 (**_180.27-0ubuntu1_**) jaunty; urgency=low

  * New upstream release. Supports the new X.org ABI (LP: #308410, #322416)
    * Added support for the following GPUs:
       o GeForce GTX 295
       o GeForce GTX 285
       o GeForce 9300 GE
       o Quadro NVS 420
    * Fixed a bug that caused VDPAU to display a green screen when using the
      overlay-based presentation queue with interlaced modes.
    * Fixed a bug that prevented VDPAU from working correctly after X server
      restarts on some GPUs.
    * Improved VDPAU's handling of mode switches; eliminated a crash in its
      mode switch recovery code and a hang in the blit-based presentation queue.
    * Fixed a bug that caused VDPAU to crash when using DisplayPort devices.
    * Fixed a potential hang in VDPAU when using the blit-based presentation
      queue on systems with multiple GPUs not in SLI mode.
    * Implemented missing error checking of layer data in VDPAU's VdpVideoMixerRender
      function.
    * Improved VDPAU's handling of setups with multiple GPUs, if a subset of the
      GPUs cannot be supported due to resource limitations.
    * Improved GPU video memory management coordination between the NVIDIA X driver
      and VDPAU.
    * Fix potential hang in VDPAU when the overlay is already in use.
    * Improved workstation OpenGL performance.
    * Fixed an X driver acceleration bug that resulted in Xid errors on GeForce 6 and
      7 series GPUs.
    * Updated the X driver to consider GPUs it does not recognize supported, allowing
      it to drive some GPUs it previously ignored.
    * Added the ability to run distribution provided pre- and post- installation hooks
      to 'nvidia-installer'; please see the 'nvidia-installer' manual page for details.
    * Updated the X driver's metamode parser to allow mode names with periods (i.e. '.'s).
    * Fixed a problem with hotkey switching on some recent mobile GPUs.
    * worked around a power management regression in and improved compatibility with
      recent Linux 2.6 kernels.
    * Added support for OpenGL 3.0 for GeForce 8 series and newer GPUs.
  * debian/nvidia-glx-180.preinst:
    - Correct typo in the removal of diversions of /usr/lib/xorg/modules/extensions/libglx.so
  * debian/nvidia-glx-180.postrm.in
    - Do not remove libGL.so (LP: #309116)
  * debian/nvidia-glx-180-dev.preinst.in:
    - Add diversion on /usr/lib/libGL.so since (the postrm tries to remove it already)
  * debian/scriptremove.sh:
    - Remove from source.




Also 

> # [ubuntu/jaunty] nvidia-graphics-drivers-96 96.43.10-0ubuntu1 (Accepted)   Alberto Milone (tseliot)
# [ubuntu/jaunty] nvidia-graphics-drivers-71 71.86.08-0ubuntu1 (Accepted)   Alberto Milone (tseliot)
# [ubuntu/jaunty] nvidia-graphics-drivers-173 173.14.16-0ubuntu1 (Accepted)   Alberto Milone (tseliot) 

[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/thread.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/thread.html)


Just Jockey left.....:D  EDIT and the "DontZap"...:twisted:

---

### Post by mgsfan on 2009-02-01
still need ignoreabi for me..don't know why lol..running on a 8600 gt

---

### Post by minisori on 2009-02-03
Odd, since this last update of the drivers i'm not able to change the resolution of an external monitor, attached to the laptop, beyond the max one of the laptop, resulting in an  error saying that the mode is not valid. Before i was able to do so using nvidia settings. Now as much i can setup it to a lower or the same resolution as the laptop.

Anyone checked this?

---

