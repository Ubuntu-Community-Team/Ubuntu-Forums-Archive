---
title: "Will Lynx achieve the 10s boot time?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Asmodai on 2010-03-20
I figured the boot time budget of 10s wouldn't be met in this release, but the [20100313.1 bootchart]("http://people.canonical.com/%7Escott/daily-bootcharts/") made me wonder. The system boots in 10.4s, but after that it's back to 17s like before.
The bootchart seems okay though. I mean, it's the same hardware and all applications seem to be getting started properly.
Can anyone clear up this mystery?

---

### Post by HoboJ on 2010-03-20
I get 13 second boots with a 3yr old HDD. So I'd wager they'll get their 10 second boot goal with me. Given hardware varies so widely I doubt they'll get =<10 seconds for everyone.

---

### Post by Asmodai on 2010-03-20
That sounds good then.
It leaves me wondering why the desktop manages to start up three times faster than in all the other bootcharts.
But hopefully, it will be just as fast in the final release.

---

### Post by psusi on 2010-03-20
If you have an SSD, sure... 5 seconds seem to be about the norm there.

---

### Post by tgalati4 on 2010-03-20
There may be some kernel boot switches that will speed up boot by not detecting hardware that you don't have.

---

### Post by lean on 2010-03-21
It can't be the kernel. It starts up with the normal amount of time. I would guess it is a gnome session problem, where some dependency is not met, and the programs are waiting for something. This would lead bootchart to believe the system is fully loaded, even when it is not.

---

### Post by MacUntu on 2010-03-21
[http://people.canonical.com/~scott/daily-bootcharts/](http://people.canonical.com/~scott/daily-bootcharts/)

---

### Post by keybuk on 2010-03-22
> **Asmodai said:**
> I figured the boot time budget of 10s wouldn't be met in this release, but the [20100313.1 bootchart]("http://people.canonical.com/%7Escott/daily-bootcharts/") made me wonder. The system boots in 10.4s, but after that it's back to 17s like before.
The bootchart seems okay though. I mean, it's the same hardware and all applications seem to be getting started properly.
Can anyone clear up this mystery?

I'm pretty sure that boot got hit by the "boot to VT1" bug.

But that's very interesting; that bug only causes the boot to end up on the wrong VT, it doesn't actually stop the rest of the boot from completing.  All it means is that X is starting off-screen.

The main difference you'd expect is that since X is not the DRM master, screen updates aren't processed and GL applications won't have a context.

In other words, compiz doesn't do anything until you press Ctrl+Alt+F7 at which point compiz updates the screen.

Looking at the bootchart, indeed you see that compiz is largely idle.

But this, in of itself, is incredibly interesting.  It means that the majority of our boot time is spent with compiz updating the screen.

I actually "knew" this was the case already, but hadn't been able to prove it.  Months ago I asked the compiz upstream folk if they could do a hacky patch to disable screen updates for the login sequence - but they never came up with the goods.  Unwittingly the VT1 bug proved that compiz was the problem after all.

So obviously now that Plymouth is largely working, I'm going to do a bit more boot time work before Beta 2, and one of the things I'll try is hacking compiz to disable screen updates by default and only enable once login is complete.

---

### Post by zika on 2010-03-22
It'll be great, just if the random crashes are solved... I'm still on UMS just because of that... No solution, yet, as far as I know...

---

### Post by zengeos on 2010-03-22
The boot times listed in the boot charts seem to jibe with my boot times.  25-30 seconds on my Acer 6530.

Contrast with appx 40-50 seconds for 9.10.

---

### Post by Schendje on 2010-03-22
> **keybuk said:**
> 
So obviously now that Plymouth is largely working, I'm going to do a bit more boot time work before Beta 2, and one of the things I'll try is hacking compiz to disable screen updates by default and only enable once login is complete.

Awesome. Thanks for all the great work on Lucid, looking forward to how much faster my machine will be after upgrading! :D

Here are some kudos: :KS

---

