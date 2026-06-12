---
title: "does ubuntu 8.10 ibex will have newer ati proprietary drivers?"
date: 2008-09-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by syms on 2008-09-13
hi,
ati's proprietary driver compiz performance is worse than open source drivers. so does ubuntu 8.10 will have better ati opensource and proprietary driver version? and do ati have their driver schedule? if so then please give me link
thanks.

---

### Post by overdrank on 2008-09-13
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by Bramkaandorp on 2008-09-13
If so, will there be better support for ati radeon AEX1650 pro? Because I don't want to have to buy a new video card for this release(not even for this release).

In the end I eventually WILL buy a new video card, but only because this one I am using will wear.

Cheers,

Bram

---

### Post by Ub1476 on 2008-09-13
Every new release has newer open/closed-source drivers. Check out phoronix.com for Linux and hardware (=drivers).

I'm not sure if they're better with Compiz though, but gameing performance has surely improved I think.

---

### Post by olskar on 2008-09-13
Check this thread out.
[http://ubuntuforums.org/showthread.php?t=918029](http://ubuntuforums.org/showthread.php?t=918029)

The situation now is that we have to downgrade Xorg just to get fglrx working. So we can only hope that ATI fixes this soon, and no there is no release schedule for fglrx but once a month around 20:th I think :)

---

### Post by syms on 2008-09-13
thank you for answers, how about ati driver schedule :D

---

### Post by Bramkaandorp on 2008-09-13
Sadly though, my graphics card is not mentioned. I just want to be able to watch videos in full screen, without a hitch, and games are no priority to me(I do understand those who do want to game).

For now, I am planning to install win xp again, simply to watch DVDs and other videos. As soon as the drivers in Linux are taken care of, I will switch to Ubuntu completely.

Cheers,

Bram

---

### Post by inportb on 2008-09-13
You can watch fullscreen videos using the opensource drivers, right? ;p

---

### Post by MALEADt on 2008-09-13
Indeed, you'll have to downgrade Xorg if you want to use the fglrx proprietary driver. It might still take quite a time before ati releases a new one, as the Xorg version we're using is still a beta, and in development. I guess ATI will wait for the final release before they release a new catalyst.
Hopefully Ubuntu devs ease the downgrading process, because [the fedora way](http://forums.fedoraforum.org/showthread.php?t=155503&page=1&pp=10) to accomplish it isn't quite user-friendly...

@inportb: you can without any problem watch video's using the open source driver, either windowed or fullscreen. You might experience some problems though, when combining 3D (e.g. Compiz) with video playback. As this is a commonly used combination, I've filed [a bug](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269357) to make the EXA accelerator default (which supports video playback). However, since the recent xserver-xorg-video-radeon update, that EXA accelerator [is broken too](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/269357). I don't know if these bug are specific to me, but if not I consider them quite serious :s

@Bramkaandorp: your card is based on the same chip as mine (a Sapphire X1650 PRO), so all things I've described in the previous block of text might also apply to you :)

---

### Post by inportb on 2008-09-13
Hm... combining 3D with video playback has always been slightly troublesome, perhaps more so with the opensource drivers. DRI2 or similar might be needed to address these issues?

---

### Post by olskar on 2008-09-13
Yep and DRI2 is not in xorg 7.4 but it is now a feature for X.Org 7.5

---

### Post by MALEADt on 2008-09-13
> **inportb said:**
> Hm... combining 3D with video playback has always been slightly troublesome, perhaps more so with the opensource drivers. DRI2 or similar might be needed to address these issues?

Doesn't need to, switching to the new EXA accelerator seems sufficient.
Anyhow, we won't see DRI2 very soon (has been pushed back to Xorg 7.5), as the project has kinda been restarted now Intel switched to another memory manager.

---

### Post by inportb on 2008-09-13
That's true; use of EXA does alleviate some of these problems. Thanks for the detailed information. :)

---

### Post by Bramkaandorp on 2008-09-13
> importb: You can watch fullscreen videos using the opensource drivers, right? ;p

Yes I can, but it doesn't look pretty. It doesn't look fluent.

@MALEADt: I have just installed Xubuntu, to see whether compiz was part of the problem. I just watched a video, and found that it was the same as in regular Ubuntu.

If I understand well, people are considering the problem. That gives me at least some comfort.

Cheers,

Bram

---

### Post by 0vermind on 2008-09-14
Okay so then why did we make a new XOrg that doesn't support ATI x1650 Pro.

As my card is an ATI x1650 Pro Sapphire chip and I got the card about a year ago so I am not planning on upgrading it anytime soon. What makes me upset is when you go to the driver page for ATI, then you select Linux it doesn't should x1650 it shows x1600 and x1800 but not x1600.

So I'm stuck with what I have? I'm sorry but I'm going to be the first one to say that Compiz runs slower than a herd of turtles stampeding through peanut butter without those proprietary drivers. Like I drag my mouse and it takes like 2-4 seconds for Compiz to follow out these pretty little animations or whatever that I turned on. Where as in previous releases of Ubuntu everything worked just fine.

Thanks!
-Mike

---

### Post by inportb on 2008-09-14
> **0vermind said:**
> As my card is an ATI x1650 Pro Sapphire chip and I got the card about a year ago so I am not planning on upgrading it anytime soon. What makes me upset is when you go to the driver page for ATI, then you select Linux it doesn't should x1650 it shows x1600 and x1800 but not x1600.

That sounds like an AMD issue that existed prior to the new Xorg. If that's the case, you would not have proprietary driver support even if you were using a compatible Xorg. Instead, you can have reasonable functionality using opensource drivers. Complain to AMD instead?

---

### Post by Bramkaandorp on 2008-10-04
Hi again. Any progress on the ati drivers front?

---

### Post by bpl07 on 2008-10-04
Watch this site for X.Org 7.4 support:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by ktp on 2008-10-04
> **inportb said:**
> That's true; use of EXA does alleviate some of these problems. Thanks for the detailed information. :)

I am loving the open source driver with EXA mode.  It is going to be hard to go back to ATI driver when they support new XOrg.

---

### Post by inportb on 2008-10-04
Until this event, I had never used the radeon driver for an extended time. I'd always gone for fglrx because I'd assumed it to be better (okay, radeon didn't always support my chipset, but now it works very well). Choice is good, eh? :)

---

