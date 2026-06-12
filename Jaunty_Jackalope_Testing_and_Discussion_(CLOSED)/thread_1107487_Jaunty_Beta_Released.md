---
title: "Jaunty Beta Released"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-03-26
[http://releases.ubuntu.com/jaunty/](http://releases.ubuntu.com/jaunty/)
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)

---

### Post by matthew.ball on 2009-03-26
Congratulations Ubuntu!

I feel I should be updating very soon!

---

### Post by screaminj3sus on 2009-03-26
I get nothing when I check for updates in 9.04 alhpa 6.

---

### Post by ktp on 2009-03-26
> **screaminj3sus said:**
> I get nothing when I check for updates in 9.04 alhpa 6.

Me too, seems like we got the updates two days ago.

---

### Post by jfernyhough on 2009-03-26
Beta freeze.

Do people not read other threads? :P

---

### Post by andrewabc on 2009-03-26
As is mentioned in about every thread. There is no "update" to get to a new alpha/beta/rc/final. As long as you kept up to date with updates (you know, when you check for updates and it shows an update for say gimp) you have the latest version.

---

### Post by Ewingo401 on 2009-03-26
I installed last nights daily build and must say that I'm very impressed with Jaunty so far.  I have an ATI card and haven't had a suitable fglrx driver since Hardy.  With Jaunty the ATI open source driver seems to have matured to a level where the closed source driver is no longer needed (at least in my opinion).  I'm also loving the new notification system, when I first read about it, it seemed like such a small upgrade that it wouldn't make much of a difference but its still nice to have.

I've only had two (very minor) problems with it so far.  I had to reinstall the b43-fwcutter to get my wireless working (had to do the same thing in Intrepid) and for some reason I couldn't install filezilla through add/remove, but it worked fine when I installed it through synaptic...weird.  But like I said those are very minor problems and if they're the only ones I have, I will be VERY pleased with this release.

---

### Post by mervinb on 2009-03-26
For some reason I had the following problems on upgrade with my systems, and this may help others:

On 3 out of 4 systems, after the updates that came two days ago, I hit the "Error 13:  Invalid or unsupported executable format" problem on booting 2.6.28-11 kernel. After some sense of panic and searching, I found that booting 2.6.28-9, and "$ sudo grub-install /dev/sda --recheck" would consistently fix the problem.

I also read about a special release of ATI Catalyst Control Centre for Jaunty, and downloaded it for my Dell Studio 15 (HD 3400 graphics). Big mistake! Ended up booting a recovery o/s, and used apt-get to remove flgrx. Even after removal, the modified kernel will not provide drm on the updated radeon or radeonhd drivers, so the check that all flgrx bits are removed, reinstall 2.6.28-11 kernel and headers, and check that drm does start up via "dmesg | grep drm".

PS: other good stuff about the beta is consistent with what I'm seeing, and the updated xubuntu login screen is stunningly attractive. Check it out!

---

