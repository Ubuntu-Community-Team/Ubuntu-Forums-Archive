---
title: "Radeon KMS + Dual Head = Jitter/Shake/Vibration"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by inportb on 2010-02-15
I only noticed this just now when I tried using an external LCD monitor on my laptop. The video shakes violently from left to right, and tweaking the clock/phase settings doesn't do anything productive. I have tried various window managers, with the same effect. However, the Kubuntu 9.10 live CD works just fine, leading me to believe that this is a KMS'd issue. I can disable the laptop LVDS screen, but the external monitor still displays wobbly imagery.

My hardware is **01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]**

Is this known behavior, or should I lodge a report on Launchpad? Thanks for any leads regarding this issue.

---

### Post by inportb on 2010-02-18
So... I take it that this is a new issue?

---

### Post by inportb on 2010-02-24
I was messing around and found one way to make this configuration work. I have to boot the laptop without the display attached, and plug it in while KDM is displayed. Then, if I configure the display while KDE has loaded, there is no jitter. This is obviously a non-optimal workaround.

The Plymouth splash jitters, as do the KMS'd VT's. If I switch to a KMS'd VT while using the workaround, the graphics are frozen on the external display while the VT is shown on the built-in display. Text mode works fine.

What might be going on?

---

### Post by willjcroz on 2010-04-13
Hi, Not sure exactly what is going on, but same thing is happening for me (Thinkpad T60 laptop with ATI X1400 GPU) it seems to be related to KMS being enabled.

Theres a bug report here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/562138]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/562138")

if you haven't already subscribe to it and maybe add more info.

Adding 'radeon.modeset=0 vga=771' to the kernel command line should get you a normal display.

---

