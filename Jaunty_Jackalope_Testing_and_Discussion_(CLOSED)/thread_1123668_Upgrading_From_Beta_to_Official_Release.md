---
title: "Upgrading From Beta to Official Release"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Lazy-buntu on 2009-04-12
I can't wait for Jaunty to be released, I really want to try out 64 bit Ubuntu (I'm using 8.10 32-bit now) and ext4 file system.

First off: if I download the current build of 9.04, will I have to reinstall the official version when it is released? Or is it as simple as keeping my system up to date by using the update manager?


Second: should I just be patient and wait for the official release? I.E. are Ubuntu betas pretty solid during the month of the release? 

I've never tried Ubuntu betas, so if it's a solid beta that I can update after the official release, I might just try it now. I'm being cautious because that would mean formatting my 32bit Ubuntu install, which is running fine.

Thanks ;)

Edit: I should mention additional repositories. Is it safe to install repositories like Medibuntu, WINE, OpenOffice, etc.?

---

### Post by SuperSonic4 on 2009-04-12
You can update from a beta to stable release via the upgrade system if I recall correctly.

If you want native ext4 and 64bit then a clean install now is what you need.

---

### Post by Lazy-buntu on 2009-04-12
> **SuperSonic4 said:**
> You can update from a beta to stable release via the upgrade system if I recall correctly.

If you want native ext4 and 64bit then a clean install now is what you need.

Right, that's why I mentioned I'm being cautious. I'd have to format my 32 bit install, which is running fine.

I could probably have it up and running my the end of today, given there are no problems.

How about extra repos?

---

### Post by jmmL on 2009-04-12
I've run into no trouble with additional repos; right now I have medibuntu, banshee, mozilla-daily, chromium-daily, wine and some other miscellaneous ones related to vdpau, compiz and pulseaudio fixes. I've run into no hitches with them.

Obviously, it's going to depend which ones you use, but the ones you listed will be fine I'm sure.

---

### Post by Lazy-buntu on 2009-04-12
> **jmmL said:**
> I've run into no trouble with additional repos; right now I have medibuntu, banshee, mozilla-daily, chromium-daily, wine and some other miscellaneous ones related to vdpau, compiz and pulseaudio fixes. I've run into no hitches with them.

Obviously, it's going to depend which ones you use, but the ones you listed will be fine I'm sure.

Sounds great. What do you think? Should I take the plunge and go right for a 64 bit install and ext4?

Is there any preliminary tests I should do? E.G. burn a jaunty 64 bit live cd and see if it runs no problem?

---

### Post by blackened on 2009-04-12
> **Lazy-buntu said:**
> Right, that's why I mentioned I'm being cautious. I'd have to format my 32 bit install, which is running fine.

I could probably have it up and running my the end of today, given there are no problems.

How about extra repos?

I haven't run into any show-stoppers since around Alpha 3 or 4. That said, it *is* a Beta, so YMMV.

Are you not in a position to dual-boot 8.10/32 with 9.04/64? That seems like the sane thing to do if you don't want to lose your working install. Granted, there's always a risk.

---

### Post by Lazy-buntu on 2009-04-12
I'm dualbooting Vista and Ubuntu 8.10 32-bit, so I don't have any room to work with on this laptop hard drive.

If Ubuntu is down, I'll still have Vista, but I won't be happy :P

---

### Post by andrewabc on 2009-04-12
You should wait until thursday/Friday this week and use/install the RC. downloading beta now and installing is a bad idea. Or download daily live cd. But RC is safest bet.

---

### Post by go7Ul1ai on 2009-04-12
> **andrewabc said:**
> You should wait until thursday/Friday this week and use/install the RC. downloading beta now and installing is a bad idea. Or download daily live cd. But RC is safest bet.

Nothing wrong with the ol'upgrade. I've been updating mine since the early alphas, sure I had a few hitches now and then but there's not many bumps in the road left now we're nearing the RC.

---

### Post by andrewabc on 2009-04-12
> **lee.jarratt said:**
> Nothing wrong with the ol'upgrade. I've been updating mine since the early alphas, sure I had a few hitches now and then but there's not many bumps in the road left now we're nearing the RC.

Yes I just meant download/installing beta will result in having to download 200-300mb and hundreds of updates which could introduce problems.

Either try a [daily live cd](http://cdimage.ubuntu.com/daily-live/), or wait for RC. If daily live cd make sure it is not oversized if you plan on putting on CD

---

### Post by Talon2 on 2009-04-12
> **Lazy-buntu said:**
> I can't wait for Jaunty to be released, I really want to try out 64 bit Ubuntu (I'm using 8.10 32-bit now) and ext4 file system.



I wouldn't get too excited about ext4 yet.  It is a non-starter on this particular system I'm using to post this reply.  Repeated problems followed by manual fsck's over testing from alpha 4 through the beta.  I finally gave up and am using ext3.  ext3 is solid, no problems.  ext4 is not ready for prime time in my opinion.

---

### Post by SuperSonic4 on 2009-04-12
ext4 has been working without any issues on my PC for both / and /home (/var is still reiser)

---

### Post by blackened on 2009-04-13
So far ext4 has been nothing short of outstanding on every system I've used it on. I think it is more than ready for primetime, considering that none but a small minority are experiencing any problems actually linked to the filesystem type.

---

### Post by raymondh on 2009-04-13
> **blackened said:**
> So far ext4 has been nothing short of outstanding on every system I've used it on. I think it is more than ready for primetime, considering that none but a small minority are experiencing any problems actually linked to the filesystem type.

Same here ... no problems.

---

### Post by tollboy on 2009-04-23
now official release of 9.04 is available
and i am on beta.
so how to upgrade it without re-formatting my system......

---

