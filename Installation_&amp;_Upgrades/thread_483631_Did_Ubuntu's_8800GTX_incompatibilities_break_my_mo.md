---
title: "Did Ubuntu's 8800GTX incompatibilities break my monitor???"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by michaeljamesjohnson on 2007-06-24
This could be a very unfortunate coincidence, but my Samsung 244T LCD monitor is now broken after a week and a half of trying to get Ubuntu 7.04 installed on my machine!!!

My problems started out with the "...can't access tty..." error (I have one SATA HDD and one SATA optical drive). I fixed this by hooking up an external USB FDD.

I then ran into the black screen upon boot-up problem. I found out this was because of Ubuntu's issues with the nVIDIA 8800GTX card. I tried everything I could find on forums to fix the issue without luck.

The strange thing was that I noticed my monitor's OSD (On Screen Display) was now corrupted/unreadable. When I boot into Vista, I can see weird unstable movement in the screen and faint lines. This got me extremely worried. I started messing with the OSD and started to realize that my monitor is perma-stuck in some sort of weird timings/refresh rates. The OSD seems to report a 20Hz refresh rate. If I make any sort of change in the OSD, the screen freaks out and corrupts. The refresh rate changes to some other weird number and the resolution is totally and completely abnormal...like 1964x1235 @ 15Hz.

I tried everything I could think of....unplugged the monitor from the DVI cable, unplugged the power, tried a VGA to DVI cable, tried a reset, messed with the Service Menu, etc. etc.

The monitor is toast. It worked flawlessly during the past year that I have had it (I bought it brand new). I did not have this problem until I decided to try dual booting Ubuntu.

I am now having Samsung ship me a Factory Refurb since I am still under warranty.

Now I am in fear of Ubuntu on this machine. I was really excited to try it, but now I dont want to chance it breaking my next monitor. Guess I will hold off until Ubuntu supports the 8800GTX. Maybe I will install it on one of my old computers.

Any thoughts?

---

### Post by litemotiv on 2007-06-25
if ubuntu (rather the video driver and/or nvidia card) forced your monitor into a state it can't get out of, it would primarily be a bug in the monitor firmware which should've prevented it from happening (or give you a means to recover from it). 

so yes and no. ;)

---

