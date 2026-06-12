---
title: "Gallium 3D Driver for ATI Legacy R300-R500"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by clhsharky on 2010-04-10
HI

The Gallium 3D Driver for ATI Legacy R300-R500 cards now has a ppa for those who would like to test . The R300G driver will work on fully updated Lucid with this ppa.

[https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon) 
Please read the whole page before installing.

This drivers only works on R300/R400/R500 Radeon cards.

-DO NOT USE ON ANY OTHER CHIP-

Please If you don't understand something ask.
Remember this is for testing on Lucid.
The R300G is for 3D don't expect it to fix anything else.

More info here
[http://www.phoronix.com/forums/showthread.php?t=23071](http://www.phoronix.com/forums/showthread.php?t=23071)

I have been using R300G for a week, having 1 update today and has been stable for me. Seems to be about = with Mesa classic, some things better some not. Of course you get OpenGL2.1 on R500.

> $ glxinfo | grep OpenGL
OpenGL vendor string: X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on RV530
OpenGL version string: 2.1 Mesa 7.9-devel
OpenGL shading language version string: 1.20
OpenGL extensions:


Sharky

--Newer UPDADED PPA FOR NEWER PACKADES--
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Killigrew on 2010-04-11
I did install it and it works quite well for me, Warcraft 3 with Wine is no Problem on X1400

greetings

---

### Post by Longinus00 on 2010-04-11
Is there a long term plan of migrating radeon to Gallium like was done with nouveau? Is matching Mesa performance a current short term goal or is supporting more cards/features?

---

### Post by Killigrew on 2010-04-11
yes, there is a long term plan to migrate, and the goal ist to support more features like OpenGL 2+ and also to have better performance.

performance is already on par with classic mesa but
for me compiz crashes when resizing windows.
There is still some work to do but it looks already pretty good :)

greetings :)

---

### Post by clhsharky on 2010-04-11
Hi 

Gallium is set to work along side mesa classic. Gallium will be the next radeon driver 'R300G' with mesa classic 'R300C' the fall back. Function first with some optimizing. Once Gallium R600g 'HD2xxx ->' is up and functioning is when I expect most optimizing to happen.

Many believe its already equal, but I have 1 app thats not working right, Goggle Earth. I only test native games so can't tell you about wine.

Sharky

As you might already know compiz has had some problems with the last round of updates.

---

### Post by gowiter on 2010-04-11
I am testing this drivers on R300.

Compiz - [COLOR=Lime]works fine[/COLOR]
GIMP - [COLOR=Lime]works fine 
[/COLOR]
Supertuxkart - [COLOR=Lime]works fine[/COLOR]
glChess (3D) - [COLOR=Lime]works fine[/COLOR]
Secret Maryo Chronicles - [COLOR=Lime]works fine[/COLOR]

0 A.D. - [COLOR=Red]doesn't start[/COLOR]
Heroes of Newerth - [COLOR=Red]doesn't start[/COLOR]
Savage 2 - [COLOR=Red]doesn't start[/COLOR]
UFO: Alien Invasion - [COLOR=Red]start, but very lagging[/COLOR]

Torchlight - [COLOR=Red]doesn't start[/COLOR]
Medal of Honor: Allied Assault - [COLOR=Red]doesn't work[/COLOR]

---

### Post by Killigrew on 2010-04-11
does compiz work for you if you use the resize plugin in "normal" mode?
Do the games work with classic mesa driver?

greetings

---

### Post by gowiter on 2010-04-11
> Do the games work with classic mesa driver?
These games don't work on classic mesa driver, but ufo: alien invasion worked. Now I get a this report:
```
r300: Bad format PIPE_FORMAT_R32G32_SSCALED in r300_translate_vertex_data_type:417
r300: desc->channel[0].size == 32
R_FindImage: Can't find models/geoscape//base (models/geoscape//base)
```

> does compiz work for you if you use the resize plugin in "normal" mode?

I use only these options: [http://img682.imageshack.us/img682/2910/55775208.jpg](http://img682.imageshack.us/img682/2910/55775208.jpg)
and maximization  and minimization windows works.

---

### Post by frogotronic on 2010-04-11
Will these drivers work in Karmic - I doubt it...

---

### Post by clhsharky on 2010-04-11
HI cement_head

No Karmic wont work its UMS, you need KMS/DRI2.

Sharky

Google Earth now working after todays update.

---

### Post by Longinus00 on 2010-04-11
Any idea what the timeframe is for supporting R600/R700 cards?

---

### Post by clhsharky on 2010-04-13
HI Longinus00


Sorry cant help you there. Phornix is thee place for video driver info.

Current Status of Gallium3D Pipes and State Trackers
[http://www.x.org/wiki/GalliumStatus](http://www.x.org/wiki/GalliumStatus)

---

### Post by tormod on 2010-04-13
For news/discussions about the PPA please follow the Phoronix thread as well: [http://www.phoronix.com/forums/showthread.php?t=21708](http://www.phoronix.com/forums/showthread.php?t=21708)

Tormod

---

### Post by Seren on 2010-04-13
> **tormod said:**
> For news/discussions about the PPA please follow the Phoronix thread as well: [http://www.phoronix.com/forums/showthread.php?t=21708](http://www.phoronix.com/forums/showthread.php?t=21708)

Tormod

Thanks for your work Tormod.

I am asking a question here because I don't have a Phoronix account.

In you opinion is there any hope to get r300g included by default (if not default at least "officially" in a separate package) in 10.10, given the stability and/or features supported by r300g ?

Or we will have to wait until r600g is in good shape to get gallium stack in Ubuntu ?

---

### Post by tormod on 2010-04-13
> **Seren said:**
> In you opinion is there any hope to get r300g included by default (if not default at least "officially" in a separate package) in 10.10, given the stability and/or features supported by r300g ?

Or we will have to wait until r600g is in good shape to get gallium stack in Ubuntu ?
We could easily ship an extra r300g for people to test, but we do not want to support two drivers for the same hardware. But I am optimistic r300g is getting fast into shape and soon will be better than r300. I am in fact surprised how fast it got where it is now, almost at feature parity and better in some test cases. Then at some point upstream will start fixing bugs in r300g before r300 and it will be time to switch...

In any case, Ubuntu will probably follow upstream. If r300g ends up as default in mesa 7.9 then we'll get it in Ubuntu 10.10 but that might be too early.

See for instance [http://lists.freedesktop.org/archives/mesa-dev/2010-April/000067.html](http://lists.freedesktop.org/archives/mesa-dev/2010-April/000067.html)

---

### Post by clhsharky on 2010-04-14
HI tormod


Thanks for your Radeon gallium PPA and keeping it updated.
It sure makes it easy for those who don't build manually.

Update
I have tested gallium on default kernel .32-20 + OK.
Have been on .33/nextDRM with good results, now discontinued.
Now testing .34/rc4 OK so far I understand PM has been enabled.


Sharky

---

### Post by BwackNinja on 2010-04-14
While running compiz with a radeon x300 and radeong, my background is just one color unless I have nautilus manage the background and compiz is noticeably slower. It works though, but regular xorg-edgers works much better. I'm looking forward to greater stability and greater speed.

EDIT: actually, when using the classic drivers I have the problem with the background too...

---

### Post by NoVista on 2010-04-21
3D is working.
Compiz is smooth as silk.
Urban Terror won't run.

ATIx800AIW (r420)
No glxgears and I get:
$ glxinfo | grep OpenGL
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (DRI2)
  Minor opcode of failed request:  12 ()
  Serial number of failed request:  25
  Current serial number in output stream:  26

---

### Post by clhsharky on 2010-04-21
HI NoVista

Had that problem when I forgot to purge xorg-edgers drivers to install the Gallium driver. The Gallium driver is built to go on stock Lucid OSS drivers.

Sharky

---

### Post by NoVista on 2010-04-21
Thanks for the heads up clhsharky.
I'm on a laptop now, but I'll purge and give them a re-install tomorrow
when I am back on that system.

---

### Post by NoVista on 2010-04-24
removed srry

---

### Post by Killigrew on 2010-04-24
Hi

Radeon ppa for gallium 3d is now obsolete,
use normal xorg-edgers ppa and install libgl1-mesa-dri-gallium package
to use the gallium 3d driver.
If you want to revert back, just deinstall it :)

greetings

---

### Post by crjackson on 2010-04-24
> **clhsharky said:**
> HI

The Gallium 3D Driver for ATI Legacy R300-R500 cards now has a ppa for those who would like to test . The R300G driver will work on fully updated Lucid with this ppa.

[https://launchpad.net/~xorg-edgers/+archive/radeon](https://launchpad.net/~xorg-edgers/+archive/radeon) 
Please read the whole page before installing.

This drivers only works on R300/R400/R500 Radeon cards.

-DO NOT USE ON ANY OTHER CHIP-

Please If you don't understand something ask.
Remember this is for testing on Lucid.
The R300G is for 3D don't expect it to fix anything else.

More info here
[http://www.phoronix.com/forums/showthread.php?t=23071](http://www.phoronix.com/forums/showthread.php?t=23071)

I have been using R300G for a week, having 1 update today and has been stable for me. Seems to be about = with Mesa classic, some things better some not. Of course you get OpenGL2.1 on R500.



Sharky

Okay, so I have an ATI X800 XL with a R430.  I'm guessing this will work for me too.  Tell me if I'm wrong please.

---

### Post by tgalati4 on 2010-04-24
Anyone with experience using the gallium drivers on an ibm t43p? 

(01:00.0 VGA compatible controller: ATI Technologies Inc M24GL [Mobility FireGL V3200] (rev 80)

I'm currently using the open (ati) driver.  Googleearth works, but I presume it's software-rendered.  I can fly through 3D buildings, but it's sluggish.

tgalati4@tpad-Gloria7 ~ $ glxinfo | grep OpenGL
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:

---

### Post by clhsharky on 2010-04-24
HI tgalati4

The gallium packages was built for Lucid not Jaunty or Karmic.
> == New in Lucid ==

Mesa in this PPA now provides a libgl1-mesa-dri-gallium package containing Gallium DRI drivers. If this package is installed then the Gallium versions will be used by default, they are highly experimental so expect breakage if you use it and please do not report bugs on launchpad.

Your xorg packages are to old.
Please upgrade


crjackson

Yes they will work on your card. Galuim G3D driver is only for 3D, You still need working radeon OSS.


Killigrew
 
Thanks for bringing that update here for latecomers to this post.
I have already Updated original page.

Sharky

---

### Post by tgalati4 on 2010-04-24
I'll try it in Lucid and report back once Lucid settles in a month or so.

---

### Post by lean on 2010-04-25
Anyone have any experience with vsync? Anyone got it working with a r300-500 card?

When I am watching videos they are all teared up. Also glxgears show this:

Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
6046 frames in 5.0 seconds = 1209.196 FPS

So vsyncing is definitely not working for me :(

My card is the following:
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

---

### Post by clhsharky on 2010-04-25
HI lean

Are you getting tearing in full screen with xv enabled?

Are you testing glxgears full screen, that gives you vsync,
divide in half "DOUBLE-BUFFER" should give you refresh rate.

> glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
7754 frames in 5.0 seconds = 1550.736 FPS
7944 frames in 5.0 seconds = 1588.718 FPS
609 frames in 5.0 seconds = 121.720 FPS
609 frames in 5.0 seconds = 121.600 FPS
610 frames in 5.0 seconds = 121.812 FPS
609 frames in 5.0 seconds = 121.679 FPS
609 frames in 5.0 seconds = 121.709 FPS
608 frames in 5.0 seconds = 121.451 FPS
609 frames in 5.0 seconds = 121.654 FPS
609 frames in 5.0 seconds = 121.698 FPS
608 frames in 5.0 seconds = 121.583 FPS


Sharky

1550.x = default  gears window - using composite
121.x = full screan - DOUBLE-BUFFER
60.x = FPS vsync

---

### Post by lean on 2010-04-27
glxgears -fullscreen
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
232 frames in 5.0 seconds = 46.294 FPS
241 frames in 5.0 seconds = 48.058 FPS

this i weird. glxgears run fluently but then about once a second the gears speed up. screen refresh rate is 60hz.

running with dri2 and gallium

---

### Post by clhsharky on 2010-04-27
HI lean

That does sound weird, maybe check cables.
 What compositor are you on?

Sharky

---

