---
title: "Strange slow system after installing 8.10"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by gabrie on 2008-10-30
Hi
Last night someone pointed me to a source where I could already download the latest build even before it was finally released. So I went ahead, burned the CD, booted from cd and formatted my XP installation. Ubuntu was allowed to use the whole disk.

I did have some start up problems with my ATI HD2400pro VGA card, so I had to do a Safe mode install. Everything went fine.

Apart from small things I will get fixed later, my biggest issue is that my systems "feels" slow. You know that feeling when you can't just put your finger on it? But starting firefox is slow, switching between firefox tabs is slow, also other apps are slow. I often get a gray screen because an app is taking too long to respond.

Looking at the system monitor:
580MB in use of 1.5Gb available. Swap = 4.9Mb of 4.3Gb
When looking at cpu I notice that cpu1 and cpu2 are reported as being present. Now this is a one cpu machine, but it has hyperthreading active. So I guess the HT part is the cpu2. Both cpu's are around 20% on average, even when no other programs are running.

Running top on the command line, shows Xorg as one of the busiest programs, which is around 80% all the time. Also pulseaudio is constantly in the top of the more busier programs, but it is just around 1%

I have no idea where to look to find my performance killer.

Any tips anyone?

Gabrie

---

