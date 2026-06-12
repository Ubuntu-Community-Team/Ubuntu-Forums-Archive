---
title: "Ubuntu power management for HTPC"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by vimfuego on 2012-12-22
Hi All,

Over the years I've tried various installs of Ubuntu, but the one thing that stops me using Ubuntu as my main OS is the lack of (or user error) ability to preserve battery life on laptops. I don't know if the issue is not having manufacturer specific drivers for graphics cards etc, but I've found battery life is generally one third of that of the same laptop running Win.

Which leads me to my next question, I am setting up a Home Theatre PC, I want to run Ubuntu on it, but I need to know from the Ubuntu community if it will be able to manage the computers power drain correctly. I planned on leaving the computer on 24/7 so obviously I don't want to be running the CPU and GPU at full steam if it's just sitting there idle.

So I suppose my two questions are:
1 - Does 12.04 have good power management for CPU & GPU?
2 - If so, only when specific Linux drivers are provided by the manufacturer?

Thanks.

---

### Post by tgalati4 on 2012-12-22
Intel has an active program for power savings and there are several things you can tweak to get close to Windows power performance.  For instance on my thinkpad T43p I compiled my own kernel with voltage tweaks enabled.  This allows undervolting.  I enabled dynamic clocking of the ATI GPU so it declocks during idle and I installed a fan program to vary the fans in a smooth fashion.  These tweaks are not easy for the novice and required a bit of research, but they all work.  I now get equal battery performance between WinXP-Pro and Ubuntu Jaunty.

So, yes, you are correct.  Since Ubuntu doesn't ship with most laptops, it is not tweaked for specific hardware.  But that doesn't stop you from tweaking it.

As far as HTPC, you have incompatible strategies.  You need performance to drive high definition, play games, and stream audio and video.  That does not result in low power.  I use Wake-On-Lan and put a WOL launcher on all of my other PC's if I need a file from a file server or if I want to stream some audio or video.  This requires some setup and doesn't work correctly on all hardware, so you have to experiment and do some research.

---

