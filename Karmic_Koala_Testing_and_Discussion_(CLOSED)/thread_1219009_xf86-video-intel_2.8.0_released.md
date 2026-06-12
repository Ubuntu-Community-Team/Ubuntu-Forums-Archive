---
title: "xf86-video-intel 2.8.0 released"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-07-21
[http://lists.freedesktop.org/archives/xorg/2009-July/046534.html](http://lists.freedesktop.org/archives/xorg/2009-July/046534.html)

So is this in Karmic yet? Will it be incorporated by the alpha 3 release?

Hope to test it out on liveusb sometime :)

Looks like at packages.ubuntu.com it is using nightly or something from yesterday?

[http://packages.ubuntu.com/karmic/xserver-xorg-video-intel](http://packages.ubuntu.com/karmic/xserver-xorg-video-intel)
Package: xserver-xorg-video-intel (2:2.7.99.902+git20090720.bb300738-0ubuntu1)

---

### Post by tjeremiah on 2009-07-21
I think im downloading it now.

---

### Post by rudenko_ruslan on 2009-07-21
[https://lists.ubuntu.com/archives/karmic-changes/2009-July/004552.html](https://lists.ubuntu.com/archives/karmic-changes/2009-July/004552.html)

---

### Post by andrewabc on 2009-07-21
Thanks for the info. Can't wait to test alpha 3 (yes I know about daily images).

---

### Post by zoomy942 on 2009-07-21
im debating on installing this on my 9.04

---

### Post by jerrylamos on 2009-07-22
For two days now, with 2.8.0 Thinkpad R31 i830 video hangs after login with brown screen and cursor.

First had a running karmic and updated which included 2.8.0 which hung.

Now did a fresh install from 20090217 daily build which ran, did an update which included 2.8.0 and it hangs too.

I'm attempting to enter a bug however launchpad keeps timing out on "continue" to enter bug.

Jerry

---

### Post by dentaku65 on 2009-07-24
> **andrewabc said:**
> [http://lists.freedesktop.org/archives/xorg/2009-July/046534.html](http://lists.freedesktop.org/archives/xorg/2009-July/046534.html)

So is this in Karmic yet? Will it be incorporated by the alpha 3 release?

Hope to test it out on liveusb sometime :)

Looks like at packages.ubuntu.com it is using nightly or something from yesterday?

[http://packages.ubuntu.com/karmic/xserver-xorg-video-intel](http://packages.ubuntu.com/karmic/xserver-xorg-video-intel)
Package: xserver-xorg-video-intel (2:2.7.99.902+git20090720.bb300738-0ubuntu1)

Yes it is.
```
apt-cache policy xserver-xorg-video-intel
```
No good performance at all on my side.

---

### Post by psyke83 on 2009-07-24
> **dentaku65 said:**
> Yes it is.
```
apt-cache policy xserver-xorg-video-intel
```
No good performance at all on my side.

You're using 855GM, right? There's a major change that was pushed just after 2.8.0 which dramatically improves text rendering speed.

[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=12c5aeca7a3db92d3522d00f5daf338d522e2176](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=12c5aeca7a3db92d3522d00f5daf338d522e2176)

You'd need to test the latest edgers driver to avail of this.

---

### Post by buzzmandt on 2009-07-24
anyone have any idea when UXA will work itself out and actually be at least as good as exa was?

Also is there anyway to find out for sure if it's the intel driver or has something to do with the kernel?

Definately a regression on intel video. (i945)

---

### Post by psyke83 on 2009-07-24
> **buzzmandt said:**
> anyone have any idea when UXA will work itself out and actually be at least as good as exa was?

Also is there anyway to find out for sure if it's the intel driver or has something to do with the kernel?

Definately a regression on intel video. (i945)

You should file a bug on your performance issue, as these problems are now chipset-specific rather than affecting everyone.

My 855GM chipset has excellent 2D performance (faster than EXA/XAA), but has a 3D regression with the 2.6.31-rcX series kernels. Using the 2.6.30 kernel gives me the best 2D and 3D performance since I installed Ubuntu on this laptop.

---

### Post by dentaku65 on 2009-07-24
> **psyke83 said:**
> You're using 855GM, right? There's a major change that was pushed just after 2.8.0 which dramatically improves text rendering speed.

[http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=12c5aeca7a3db92d3522d00f5daf338d522e2176](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/commit/?id=12c5aeca7a3db92d3522d00f5daf338d522e2176)

You'd need to test the latest edgers driver to avail of this.

Hi psyke83,
yes I have that card.. are you mean to use xorg-edgers repo?
At the moment the system is quite stable, but ppracer it's terrible slow (2fps) and flash stream (youtube etc...) are really impossible to watch.

---

### Post by buzzmandt on 2009-07-24
I finally decided to try the xorg-edgers repo.....

Right now my graphics are AWESOME!!  nexiuz runs smooth, openarena is smooth and super fast.  will try nwn later on, but right now I'm happy

---

### Post by kirawrath on 2009-08-03
I was getting some trouble with my video card and I'm wondering that it might solve the problem, I already downloaded the xf86-video-intel-2.8.0.tar.bz2 file but I don't know what to do with it, what should I do to install it? And please be detailful.

Kind Regards,
Kira.

---

### Post by andrewabc on 2009-08-03
> **kirawrath said:**
> I was getting some trouble with my video card and I'm wondering that it might solve the problem, I already downloaded the xf86-video-intel-2.8.0.tar.bz2 file but I don't know what to do with it, what should I do to install it? And please be detailful.

Kind Regards,
Kira.

If you have updates from system->administration->update manager
You will have latest version. No need to manually download .bz2 files.

This is assuming you are running karmic and not earlier version of ubuntu (jaunty etc).

---

### Post by kirawrath on 2009-08-06
Oh, thanks so.

---

### Post by keypox on 2009-08-07
how is performance on intels 'flagship' lol the 4500?

Im on old 950 and it runs pretty good.  Compiz runs ok. Not to bad :) 

Also how is 3100

---

### Post by andrewabc on 2009-08-08
> **keypox said:**
> how is performance on intels 'flagship' lol the 4500?

Im on old 950 and it runs pretty good.  Compiz runs ok. Not to bad :) 

Also how is 3100

I have x3000 which is almost same as mobile 3100, and when testing liveusb it ran nice. No problems that I can remember.

---

### Post by VMC on 2009-08-08
I have older **i865** and have to revert to older intel driver 2.4.
Nothing else seems to ever work. I wondering if it ever will.

---

