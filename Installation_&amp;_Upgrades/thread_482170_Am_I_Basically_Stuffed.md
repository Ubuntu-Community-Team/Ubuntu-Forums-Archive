---
title: "Am I Basically Stuffed?"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by CompactDestruction on 2007-06-23
I have a laptop with a Mobility Radeon X700 and Inprocomm IPN2220 wireless.

It won't boot off the LiveCD, it just brings a blank screen after the progress bar reaches 100% and I can hear the startup noise.

Apparently the only way to fix this requires an internet connection, but my wireless card is not natively supported and my wired connection is non-functional.

Is there any way around this or do I need to come back in four months and hope one of the major graphics manufacturers is supported by the next release?

---

### Post by reiki on 2007-06-23
Just FYI.... it's not UBUNTU that doesn't support ATI... it's ATI that doesn't do well supporting linux.

You should have an option of "Safe Graphic Mode" on the LiveCD when it first starts. See if that works for you and then you can get better drivers after install. I've stopped using liveCds for installs and now only install from alternate CDs.

---

### Post by mpires on 2007-06-23
In regards to the graphic card - I also have a mobility x700 - I insert the following in xorg.conf in the "Device" section:

	Option		"CRT2Position"	"clone"
	Option		"MonitorLayout" "LVDS, CRT"

This is with the open driver. Hope it works for you

---

### Post by CompactDestruction on 2007-06-23
Safe graphics mode worked off the bat. Now I've got to get my wireless working + 3D acceleration.

Sorry for being so abrasive before.

---

### Post by wpshooter on 2007-06-23
> **CompactDestruction said:**
> Safe graphics mode worked off the bat. Now I've got to get my wireless working + 3D acceleration.

Sorry for being so abrasive before.

Didn't seem abrasive to me.  Heck, you don't know, if you don't ask.

---

### Post by CompactDestruction on 2007-06-23
I got 3D acceleration and my wireless working fully.

Wow so I guess I wasn't stuffed... just takes a bit of work :D

---

### Post by Arlanthir on 2007-06-26
How did you manage to get 3d acceleration?
I want to do that on a similar graphics board :S

---

### Post by CompactDestruction on 2007-06-27
You have to be connected to the Internet. Then just go to System > Administration > Restricted Drivers Manager and make sure the Ati one is ticked.

---

### Post by Arlanthir on 2007-06-27
Ohh.. It's not *that* simple on my friend's ATI :S Weird..
That's using the fglrx driver.. Does that step automatically give you Direct Rendering? Or you have to use XGL?

---

### Post by CompactDestruction on 2007-06-27
Yep it gave me direct rendering straight away. Just don't expect to use Desktop Effects or anything- fglrx does not support compositing.

I think you need XGL if you want to use Beryl.

Make sure you have the restricted repository enabled in Software Sources.

---

### Post by Arlanthir on 2007-06-27
Yeah, after a lot of configuring we've got it to work.. Just making some time before trying XGL/other drivers :(

---

### Post by ubukool on 2007-06-27
Hi CompactDestruction,

I'm glad you're not stuffed!  In my experience, it's a steep learning curve at the beginning with Ubuntu as you try and get everything working (getting wireless working can have you pulling your hair out!) but when you do, it's very comfortable unless something comes along to break your system (such as updates of certain compositing window managers...oops, did I say that? ;) ) in which case, it can get difficult again for a little while.

I think it's as you say - it requires effort because it doesn't work right out of the box.  This is going to appeal to someone who wants to learn something new, face a few challenges and then basically triumph (you can do anything if you try).  It's going to appeal to someone who likes fiddling with computers, but for someone who just wants something that works, (sort of :D ) Windows is always going to be more appealing, but  I do believe it's worth the effort because Ubuntu is streets ahead of Windows.

I suppose it's the difference between a computer being your hobby and just being a tool to do things on.  Computer hobbyists like Linux!  The more effort you put in, the more you get back.

---

### Post by CompactDestruction on 2007-06-28
Yeah I understand this now everything's just about how I want it. These forums certainly help with some of those hurdles.

---

