---
title: "Kubuntu 9.10 is slow after package updates"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Jota37 on 2009-12-18
Hi,

My install of Kubuntu was quite irritating after a while. It kept freezing for a few seconds, then going back to work for a few seconds, then slow again, etc. This system had been updated from previous versions of Kubuntu. But I suspected some software update in the previous couple of weeks was to blame.

Anyway, I decided to do a fresh install of 9.10. It went very well and the system was back to normal, nice and responsive.

Then, the update manager told me there where some 170 or so packages to update. So I did it. And the computer became unusable again.

So clearly something in the updates is breaking my (old) machine. The problem is finding out WHICH package is doing it.

Has anyone experienced this problem? And what is the solution? I would hate to have to update one package at a time to see which one screws everything up... What would a better way to do this be, if any?

My setup, basically:
Kubuntu 9.10
1.8 GHz generic machine with 1 GB RAM and 40 GB HD.
Nvidia video

Thanks galore
J

---

### Post by andrew4558 on 2009-12-18
It's exactly the problem I'm having right now after a clean installation and update bunch of softwares and the system becomes slow.

---

### Post by Jota37 on 2009-12-19
Following a hunch, I decided to inactivate the proprietary Nvidia video driver, and the computer went back to normal. Working perfectly now, for more than one hour -- before, it was bad just after booting. 

I can't be sure of what is actually causing the trouble, but I would guess that some interaction between the new kernels installed after package updates and the video driver is causing this. I've seen some threads about such a problem with the ATI drivers, and the solution seems to be, at least in that case, installing the .32 kernel. I don't want to go that far, so I just inactivated the proprietary driver.

Now I can't use the cool desktop effects anymore, but that's a very small price to pay for a computer that actually works.

I don't know if this will be the problem for you, but here's what I have done:

1) Go to the Kickoff App Launcher on the bottom left.
2) Go to Applications -> System
3) Start "Hardware Drivers"
4) Click on the active proprietary video driver, if any, and click the "Inactivate" (or was it "Disable"?) button. In my case it as the one labeled "NVIDIA accelerated graphics driver (version 185) [Recommended]".
5) Restart the computer (it was still bad until I restarted; maybe just restarting Xorg would be enough)

I hope this works for you too.

Cheers
J

---

### Post by Jota37 on 2010-01-12
New development, sigh...

The problems described above soon came back. So I decided to try Live CDs, but the problem remained -- "random" crashes, apparently happening when I demanded more from the display.

I tried live CDs for Kubuntu 8.10 and 9.04, and Ubuntu 9.04. All of them with the same results.

So I started thinking hardware was the problem.

Opened the case, removed the video card and... hm, two of those little cylinders (capacitors) were broken on top and with some powder coming out... Not good. Seems like a smoking gun, almost literally.

Plugged in a spare video card that was in an old, inactive computer, and all has been working flawlessly ever since, proprietary drivers included.

I hope this was just a fluke from the power or something, and not that I have a bad PSU (very old computer, 7 or 8 yrs-old at least) or things might go bad again.

Cheers
J

---

