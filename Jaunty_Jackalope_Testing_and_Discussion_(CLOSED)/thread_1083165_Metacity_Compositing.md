---
title: "Metacity Compositing"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by talkingwires on 2009-02-28
Has anybody given Metacity's compositor a spin in Jaunty? Are the Gnome developers even still working on it, or has it been abandoned due to its obscurity in the face of Compiz?

Last time I tried it, I liked that windows still worked the same (Compiz adds some strange quirks to window behavior), but it was a little slow and pretty bare-bones.

**Edit -** On a related note, I forgot how to disable Compiz's video chipset blacklist. Can anybody refresh my memory? (My chipset was disabled due to suspend/resume issues, but my laptop [can't resume from suspend]("https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/34155") anyway.)

---

### Post by andrewabc on 2009-02-28
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

Is what I used for gutsy when my intel g965 was blacklisted.

---

### Post by autocrosser on 2009-02-28
Hmmm--I just tried it with my system--nvidia 9500GT. It is working, I didn't try anything other that normal desktop--no games, etc........Looks OK to me :D.

---

### Post by ad_267 on 2009-02-28
I think this bug is still a big issue when using metacity compositing: [https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/240062](https://bugs.launchpad.net/ubuntu/+source/desktop-effects/+bug/240062)

---

### Post by Yashiro on 2009-03-01
Metacity Compositing works but it's dog slow. 
It usually crashes when you disable it too.

---

### Post by Starks on 2009-03-01
AFAIK, Metacity compositing is enabled by default now. The border shadows are proof enough.

---

### Post by CoolGoose on 2009-03-01
I've used Metacity compositing since 8.10 and it's neither slow nor buggy (at least for me @8600GT proprietary nvidia drivers).
It works pretty nice on 9.04 as well. Wanted to switch to compiz for the scale effect but it's way too weird (expose in mac os x has a better algorithm imho) so i switched back to Metacity + compositing for gnome-do (docky).

---

### Post by taavikko on 2009-03-01
> **Starks said:**
> AFAIK, Metacity compositing is enabled by default now. The border shadows are proof enough.

Don't think so, I've had to manually set it on.
```
gconftool-2 /apps/metacity/general/compositing_manager -s -t bool true
```

Performance, better than compiz ;) worse than without both of them.

IMHO compiz only provides few usability improvement, for that argument only, it should be only enabled on very few cards (that'll work with it)
stricter blacklisting. And definitely not enabled by default.

---

### Post by Yashiro on 2009-03-01
If Metacity is faster than Compiz for you then your video driver must be borked.

---

### Post by taavikko on 2009-03-02
> **Yashiro said:**
> If Metacity is faster than Compiz for you then your video driver must be borked.

Whou...
First one, with metacity composite
Second, without any effects
Third, with compiz (normal visual effects)

```
devil@elite:~$ glxgears 
15374 frames in 5.0 seconds = 3072.041 FPS
19759 frames in 5.0 seconds = 3951.433 FPS
19902 frames in 5.0 seconds = 3980.312 FPS
19900 frames in 5.0 seconds = 3979.959 FPS
19903 frames in 5.0 seconds = 3973.991 FPS
devil@elite:~$ gconftool-2 -s /apps/metacity/general/compositing_manager -t bool false
devil@elite:~$ glxgears 
53368 frames in 5.0 seconds = 10673.574 FPS
53956 frames in 5.0 seconds = 10786.599 FPS
53803 frames in 5.0 seconds = 10760.539 FPS
53766 frames in 5.0 seconds = 10745.960 FPS
53769 frames in 5.0 seconds = 10753.768 FPS
devil@elite:~$ glxgears 
31941 frames in 5.0 seconds = 6388.195 FPS
29949 frames in 5.0 seconds = 5989.777 FPS
29908 frames in 5.0 seconds = 5981.502 FPS
31979 frames in 5.0 seconds = 6395.728 FPS
34227 frames in 5.0 seconds = 6836.893 FPS

```

Didn't use to be this way, but heck, last time I tried compiz was with
hardy alpha*(something) Never really cared about too much bling bling.
But let's give it a try for a few days...

---

### Post by plun on 2009-03-02
> **taavikko said:**
> Whou...
Didn't use to be this way, but heck, last time I tried compiz was with
hardy alpha*(something) Never really cared about too much bling bling.
But let's give it a try for a few days...

OK....

I installed Jaunty within a notebook which has a **SiS graphic chip**.

Metacity compositing works just fine and its mainly for using Gnome-do and Docky.  Bling-bling...):P

---

### Post by taavikko on 2009-03-02
> **plun said:**
> OK....

I installed Jaunty within a notebook which has a **SiS graphic chip**.

Metacity compositing works just fine and its mainly for using Gnome-do and Docky.  Bling-bling...):P

Tried compiz for five minutes, And with a wave of my magic wand, it's long gone.

Not my thing, when metacity is working and gives me enough of bling bling i need.
Transparent gnome-terminal for starters...

9800gtx+ here, so drivers always a bit mess...

---

### Post by avb on 2009-03-02
compositor works good, but windows switching on Alt-tab is terribly slow. Id love to use composite but with a 'classic' windows switcher

---

### Post by muecker on 2009-03-06
Does anybody else have issues with the new metacity compositing constantly locking up the menu?  I use Tilda and quite often when I try to activate it, it refuses to open.  When it does that Avant Window Navigator goes blank (icons are there and work but you cannot see them), the menu refuses to open and other things like dragging windows don't work right.  If I kill metacity it works again for a while.

I'm not sure if this is a problem with Metacity or interaction with Evolution, or both, but it happens on a regular basis for me.

Other than that, I like the effects from enabling compositing.  Avant window navigator's dock is a lot better than gnome-do's current dock, although gnome-do is better for other things.

---

### Post by cszikszoy on 2009-03-06
I'm not sure why people are quoting what video card they are using when talking about enabling metacity compositing.  Metacity compositing is all software (ie no opengl), so it wouldn't make any difference at all what video card you're using.  Is this correct or am I mistaken?

---

### Post by jpeddicord on 2009-03-06
> **cszikszoy said:**
> I'm not sure why people are quoting what video card they are using when talking about enabling metacity compositing.  Metacity compositing is all software (ie no opengl), so it wouldn't make any difference at all what video card you're using.  Is this correct or am I mistaken?

The metacity compositor does in fact use video hardware, just as Compiz does. If it didn't it wouldn't be a compositor. :)

---

### Post by mejy on 2009-03-06
> **jacobmp92 said:**
> The metacity compositor does in fact use video hardware, just as Compiz does. If it didn't it wouldn't be a compositor. :)
I don't think that's quite correct - it's possible to composite in software and metacity does that when there's no hardware texture-from-pixmap support i believe.  There's no real slowdown either way on a modern PC, but using 3D hardware should result in a slightly more responsive interface.

In reply to the glxgears results posted earlier, compiz slows down the performance of other 3D applications and should typically be shut off when running performance-intensive rendering, but otherwise should take load off the CPU and make the interface more responsive.

---

### Post by cszikszoy on 2009-03-06
> **jacobmp92 said:**
> The metacity compositor does in fact use video hardware, just as Compiz does. If it didn't it wouldn't be a compositor. :)

Compositors do not require video hardware.  It just happens that all other compositors required video hardware.  Actually, I think the compositor in OSX 10.0 (Quartz? I think) didn't require video hardware.  But I was wrong in my statement earlier.  Apparently, metacity CAN use video hardware, but in the absence of video hardware, all rendering is done in software.

---

### Post by Darkshade on 2009-03-06
Metacity's compositing seems to be actually slower than Compiz on my machine. Here's what happens when I run glxgears:

Metacity without compositing:
20697 frames in 5.0 seconds = 4139.292 FPS
20683 frames in 5.0 seconds = 4136.474 FPS
20990 frames in 5.0 seconds = 4197.941 FPS

Metacity with compositing:
1516 frames in 5.0 seconds = 303.032 FPS
1407 frames in 5.0 seconds = 281.229 FPS
1216 frames in 5.0 seconds = 242.951 FPS

Compiz:
5312 frames in 5.0 seconds = 1062.313 FPS
5419 frames in 5.0 seconds = 1083.729 FPS
5148 frames in 5.0 seconds = 1027.130 FPS

Not sure if it actually means something but I get about 3 times more fps with compiz than metacity compositing, which is still 4 times less than metacity without compositing. :-k

---

### Post by cb951303 on 2009-03-06
> **cszikszoy said:**
> Compositors do not require video hardware.  It just happens that all other compositors required video hardware.  Actually, I think the compositor in OSX 10.0 (Quartz? I think) didn't require video hardware.  But I was wrong in my statement earlier.  Apparently, metacity CAN use video hardware, but in the absence of video hardware, all rendering is done in software.

+1, AFAIK XFCE and e17 don't require hardware acceleration for composite.

---

### Post by pferraro on 2009-03-06
> **Darkshade said:**
> Metacity's compositing seems to be actually slower than Compiz on my machine. Here's what happens when I run glxgears:

Metacity without compositing:
20697 frames in 5.0 seconds = 4139.292 FPS
20683 frames in 5.0 seconds = 4136.474 FPS
20990 frames in 5.0 seconds = 4197.941 FPS

Metacity with compositing:
1516 frames in 5.0 seconds = 303.032 FPS
1407 frames in 5.0 seconds = 281.229 FPS
1216 frames in 5.0 seconds = 242.951 FPS

Compiz:
5312 frames in 5.0 seconds = 1062.313 FPS
5419 frames in 5.0 seconds = 1083.729 FPS
5148 frames in 5.0 seconds = 1027.130 FPS

Not sure if it actually means something but I get about 3 times more fps with compiz than metacity compositing, which is still 4 times less than metacity without compositing. :-k

This just means that the performance of 3D applications are affected - not that your desktop rendering itself is worse.  Try running gtkperf using metacity both with and w/out composite, and again with compiz.  You will likely find that the compiz and metacity+composite performance numbers are comparable.  This is the case with my NVIDIA Quadro NVS 140M.  My metacity+composite numbers are actually a little better than compiz, thanks to the NVIDIA binary driver's recently improved XRender acceleration.

---

### Post by RAOF on 2009-03-06
> **cb951303 said:**
> +1, AFAIK XFCE and e17 don't require hardware acceleration for composite.

Technically, they don't *require* hardware acceleration.  They will, however, be dog slow.  What you probably mean is that they don't require *OpenGL* acceleration, which is true.  Metacity's compositor uses the XRender extensions, which for most drivers are accelerated through EXA or XAA.  2D acceleration - which is, in many cases, implemented with the card's 3D engine anyway, since cards don't tend to have 2D acceleration hardware anymore.  See the nouveau drivers for an example :).

> **pferraro said:**
> This just means that the performance of 3D applications are affected - not that your desktop rendering itself is worse.  Try running gtkperf using metacity both with and w/out composite, and again with compiz.  You will likely find that the compiz and metacity+composite performance numbers are comparable.  This is the case with my NVIDIA Quadro NVS 140M.  My metacity+composite numbers are actually a little better than compiz, thanks to the NVIDIA binary driver's recently improved XRender acceleration.

Actually, it doesn't even mean that.  It means that *copying a rendered scene to the frontbuffer* is affected.  This is generally the bottleneck hit by glxgears.  For all but the most trivial of applications, this overhead is negligible - the card spends much, much more time actually rendering the scene than it does copying that to the screen.

This is why Ubuntu's glxgears used to not show FPS numbers unless you passed --iacknowledgethisisnotabenchmark.  glxgears is not a benchmark, and the numbers that come out of it are almost meaningless! :)

---

### Post by ikus060 on 2009-03-22
Hi,

I'm having big trouble with Metacity Compositing. Are reproducible without problem, but it's get impossible to determine the root cause.

I attach some screenshots.

I have Ubuntu Alpha6.

---

### Post by ikus060 on 2009-03-22
I notice that I have this corruption problem only if I use resolution higher than 1680 x 1050.

---

### Post by melalcoolique on 2009-03-23
You have not enough video memory (driver memory leak?)

---

### Post by ikus060 on 2009-03-23
Hi melalcoolique,
I don't think it's hardware related since I only have the problem with Alpha 6 and not Alpha 5.

My graphics card is a Radeon Mobility X300 with 256Mb or 512Mb (I don't remember).
The Maximum resolution for this card is 2048x1536.
[http://ati.amd.com/products/mobilityradeonx300/specs.html](http://ati.amd.com/products/mobilityradeonx300/specs.html)

Thanks

Edit: I'dont have the problem using Compiz.

---

