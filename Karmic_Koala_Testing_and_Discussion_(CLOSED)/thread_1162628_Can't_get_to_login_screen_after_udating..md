---
title: "Can't get to login screen after udating."
date: 2009-05-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-05-17
I used the alternate CD to install as the live cd would not boot at all.

Alternate worked great and on booting to the new install everything was slick.  I ran apt-get update.  I installed gparted and startupmanager.  I copied music files from another partition and loaded them into Rhythmbox.  I ran update manager and installed the updates.  I installed the ATI drivers.

Will not reboot.  It starts and gets to where, I think, the login screen should come up and then I just get the funny stuff at the top of the screen like every thing is jammed up there.  This may be due to the ATI drivers that have never worked that well on this box.

I forget what kernal Mint 6.0 is running but the drivers do work, at least somewhat, there.

---

### Post by DougieFresh4U on 2009-05-17
Your no trying the 'fglrx' are you?
That does not work. I had the 'funny' screen as well and had to use recovery from grub and remove 'fglrx'

---

### Post by ranch hand on 2009-05-17
I have only run recovery once and let it run and then tried normal boot.  I am going to try exactly that right now.

I installed the x86 version so when I fool with it I diable 2 of my 4 cpus so that I am running on 32.  I'll try the 64 version one of these days.

---

### Post by ranch hand on 2009-05-17
I am going to have to reinstall.  Can't even get to the root/network setup.  Bsically nothing works now for squat.

I'll try it again without the video driver.

---

### Post by ranch hand on 2009-05-18
Reinstalled the root partition.  NO drivers added.  Am updating and doing everything else that I did (I will transfer 1 more folder to Music as all came through my reinstall fine).

Will reboot when done and see what happens.

---

### Post by ranch hand on 2009-05-18
ATI driver was the problem.  Rebooted just fine.

---

### Post by TerminX on 2009-05-18
> **ranch hand said:**
> I installed the x86 version so when I fool with it I diable 2 of my 4 cpus so that I am running on 32.
Well, that certainly makes no sense whatsoever.

---

### Post by ranch hand on 2009-05-18
No sence running on 64.  When you update you end up with a kind of mixed version as the packages offered are determined by the signature of your box.

You will never get a straight 32bit kernal for instance.

I run both 32 + 64 bit versions on here and try to keep them to there own system.

I learned that with my first installation on this box.  8.04 x86.  It is now running on a 64 bit kernal.

Doesn't seem to make much difference but every once in a while you do run into something.  There will be more differences as time goes on, I believe, and 64 gets more use and more apps written just for it.

Of coarse, it may make no sense what so ever.  I am a rnach hand and Blacksmith.  Not really, probably, a good foundation for playing with computers.

---

