---
title: "Kubuntu Karmic - resume issues [even from hibernation]"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pedrogfrancisco on 2009-09-11
Does anyone here with Kubuntu can tell me if they can resume properly? 

Both with Suspend & Hibernation I've issues, so I need help determining if they're a general problem or something related to my system.

EDIT:
First, a better description:
* I suspend/hibernate
* I turn computer on
* Either
 - kdm doesn't appear (get black screen)
 - it does, I type in password: title bars are gone, Plasma starts getting corrupted; ALT+F2 works but I get a complete hang soon after, for example, typing 'konsole'.

I use kwin with Desktop Effects
I've an Intel GM965:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

Other links which may, or may not, be related:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422669]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422669")
[http://ubuntuforums.org/showthread.php?t=1252138]("http://ubuntuforums.org/showthread.php?t=1252138")



Basically what I want:
* Do you have a Karmic Koala system with KDE and kwin with working suspend/shutdown? If so, or if not, please present the following info:
- Graphics Card
- Desktop Effects?

Thanks :)

EDIT2:

> $ glxinfo  |grep  -i "opengl renderer string\|direct"
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

---

### Post by fifth on 2009-09-11
No issues here, everything works normally after a resume from suspend.

Actually this is the first (k)ubuntu release I've used sleep/suspend exclusively. Very rarely reboot the laptop now. Although I haven't tried hibernate.

What problems you getting?

---

### Post by pedrogfrancisco on 2009-09-11
Edited my post :)
* black screen
OR
* corrupted workspace followed by hang

Which Graphics Card do you have?

---

### Post by fifth on 2009-09-12
> **pedrogfrancisco said:**
> 
Which Graphics Card do you have?

Intel GMA 950 here.

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

```

With desktop effects enabled.

---

### Post by pedrogfrancisco on 2009-09-12
> $ glxinfo  |grep  -i "opengl renderer string\|direct"
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20090712 2009Q2 RC3 x86/MMX/SSE2

Hum and you're using KDM & KDE?

---

### Post by Kokopelli on 2009-09-12
The missing toolbars/etc on resume is a known bug.  If you have desktop effects enabled in kwin with certain Intel cards then on resume it sets all but the focused window to 100% transparency and ... some other problems.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422669](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/422669)

---

### Post by fifth on 2009-09-12
> **pedrogfrancisco said:**
> Hum and you're using KDM & KDE?

Yeah, almost standard install of Kubuntu. Using KDM and Kwin with desktop effects.

Not sure if its what you intended, but you quoted your own specs. Note that I'm on 945GM and your on 965GM so I'm guessing that's where the differences are in the resume experience.

But from the bug Kokopelli mentioned, disabling desktop effects might solve your issue for now.

---

### Post by pedrogfrancisco on 2009-09-13
Indeed it does :)

---

### Post by swined on 2009-10-16
after the last dist-upgrade got the same problem. my video is Radeon Xpress 200M. when it starts it gets stuck for several minutes with a black screen, when it gets up from suspend it stucks in black screen forever. even the magic sysrqs dont work.

---

