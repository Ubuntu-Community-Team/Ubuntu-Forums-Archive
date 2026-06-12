---
title: "Intel GMA 4500's pathetic performance in Karmic Koala Beta"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Takehaniyasubiko on 2009-10-19
Hi,

My laptop is Amilo Li 3710: Pentium Dual-Core T3200 (2.0 Ghz), 3 GB of RAM and Mobile Intel Graphics Media Accelerator 4500M (shared memory).

I've installed Ubuntu 9.10 on it few days ago and at first I thought it run pretty good. But today I've noticed that 720p movies run a little choppy and that made me wonder why since the laptop played HD movies great under Windows. Then I've run TORCS as a test and... **Well, it's a disaster. The game runs like crap and the sound is so static that I can't stand it.** :mad:

Is there something I can do about the performance of my laptop under Karmic Koala? Maybe the final version will help? Or am I without luck?

---

### Post by miegiel on 2009-10-19
Up to 720p HD plays fine on my laptop (core 2 duo SU9400 @ 1.4GHz + GMA 4500MHD). Well, there is the occasional stutter, but **nothing pathetic**. For anything beyond 720p I use [_XBMC_]("http://en.wikipedia.org/wiki/Xbmc") in windows. Other players give me the same performance in windows as in ubuntu, though I've heard (to lazy to try) that [_MPC_]("http://en.wikipedia.org/wiki/Media_Player_Classic") with the right codecs should be about as good as XBMC.

---

### Post by Takehaniyasubiko on 2009-10-20
Did you try TORCS or Open Arena? Those apps run **pathetic. **They run better on my old Druon 700 Mhz machine![B] 

:<
[/B]

---

### Post by miegiel on 2009-10-20
> **Takehaniyasubiko said:**
> Did you try TORCS or Open Arena? Those apps run **pathetic. **They run better on my old Druon 700 Mhz machine![B] 

:<
[/B]

Nope, else I would have said so. Playing games on laptops give me a rash. Probably because I can't use [_a real keyboard_]("http://www.steelseries.com/int/products/keyboards/7g/information").

---

### Post by Miguel on 2009-10-20
The truth is that 3D performance of Intel graphics is really pathetic in Linux. I really thought it was going to be better coming from an ATi 9600 (free driver), but it wasn't. My 4500 MHD can get playable framerates in Half Life 2 in Windows7 (OK, not everything at its highest at the native 1440x900), but in linux openarena and, oh my god, world of goo, run soo slowly... And that is in Karmic, which is at least 2x faster than Jaunty when doing 3D.

Truth to be said, there are some bugs in the dual ATi/Intel driver in windows: for example, I had no OpenGL acceleration in certain applications on WinXP (the ATi card didn't work either) ntil a driver update around May. And for some reason, the OpenGL/D3d 2001 game Blade of Darkness runs weird (either slow on the intel or wickedly fast with the ATi, even with vsync turned on).

---

### Post by Takehaniyasubiko on 2009-10-20
So I guess I'm out of luck... It's a real shame that Intel graphics run so crappy under Ubuntu since I really don't want to go back to Windows but I guess I will have to for some apps. 

I really thought that Karmic would get things straight in 3D Intel department. :<

---

### Post by 6205 on 2009-10-20
Hopefully it will not be worst from Jaunty.. On my C2D E8400 @ 3.0GHz + X4500 was Compiz OK and also 720p videos were smooth.

---

### Post by Miguel on 2009-10-20
> **6205 said:**
> Hopefully it will not be worst from Jaunty.. On my C2D E8400 @ 3.0GHz + X4500 was Compiz OK and also 720p videos were smooth.

Don't get me wrong. The current status of Intel drivers (for my laptop at least) is much much better than it was on Jaunty. Video playback seems decent (I don't have much high definition media, so I can't comment on those), 2D accel, although worse than on the Mobility Radeon 3470, is much decent (F-Spot is much more usable) and compiz is fine. So much so that I've actually spent a week with desktop effects enabled, even in KDE 4.3 (I've got a spare partition with Kubuntu Karmic). I might still disable them while on battery, but real usage performance seems mostly adequate.

On the other hand, I feel there's an extra mile of performance to be extracted from this GPU, which is more powerful than an ATi Mobility Radeon 9600 (this was able to play Far Cry, mind you). It is in the performance-oriented 3D arena where the intel drivers currently fail. And for me, that sucks.

---

### Post by Takehaniyasubiko on 2009-10-20
> It is in the performance-oriented 3D arena where the intel drivers currently fail. And for me, that sucksExactly. 3D performance is terrible. I've been trying to play some Saturn games through SSF emu via Wine but the 3D was so choppy I didn't even want to watch it. At first I thought it was becasue of Wine emulation but now I see that it's because of Ubuntu's weak drivers for GMA 4500.

Like I said, if Open Arena plays far worse than on my old Duron 700 Mhz&GeForce 2 MX 400 machine, then something is terribly wrong. :<

---

### Post by paxmark1 on 2009-10-20
[http://ubuntuforums.org/showthread.php?t=1130582&highlight=video-intel](http://ubuntuforums.org/showthread.php?t=1130582&highlight=video-intel)

They have been at it for awhile and are very active presently.  It says jaunty, but much of the discussion presently is about karmic.
peace, mark

---

### Post by Takehaniyasubiko on 2009-10-20
Lucifer, 125 pages! O_O

EDIT: I've checked the last few pages and I didn't find anything helpful about GMA 4500 in Karmic, sadly.

---

### Post by kamaboko on 2009-10-25
Well this is encouraging.  I just got a toshiba laptop with a 4500m. Hmmmmm....

---

### Post by keypox on 2009-10-26
i know 9.04 was horrible with 4500 the beta has been much better.  I hope it gets even better ...

---

### Post by Kareeser on 2009-10-26
I doubt it helps, but I've actually obtained superior performance using **Intrepid**.

But then again, it's only because new xserver-xorg-video-intel packages aren't backported, which is a good thing, since it relies on EXA and the like...

In fact, it all started with Jaunty, and it's just been slowly getting better.

But I have a 855GM, which I believe is an older card.

---

### Post by Miguel on 2009-10-26
> **kamaboko said:**
> Well this is encouraging.  I just got a toshiba laptop with a 4500m. Hmmmmm....

At least it is encouraging to see the performance improvements. Anyway, I have an old Dell Inspiron 8600 lying unused and bored at home, with Hardy installed on it (never got around installing Intrepid). That lappie has an ATi Mobility Radeon 9600 Pro Turbo. It would be nice to compare 2D stuff between that card, and the 4500MHD and the ATi Mobility Radeon 3470 available in my Thinkpad. Then, testing 3D between both the Intel and the 9600 could be done. 

Mmm... I may actually do it once Karmic is released...

---

