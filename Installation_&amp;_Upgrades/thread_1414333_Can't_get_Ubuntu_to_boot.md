---
title: "Can't get Ubuntu to boot"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by ImTheBatman on 2010-02-23
Hi, I recently downloaded Ubuntu 9.1 and burned it to a CD. However, I can't seem to get it to boot. I got to the main menu and selected to run it directly from CD, and the Ubuntu symbol showed up saying it was loading things, but then the screen went black and nothing happened even if I waited over 15 minutes. During this time the HDD light was flashing every second or two, and I could see about three white pixels at the top most row of the screen.  Does anybody know what is causing this problem and\or how to solve it? I am kind of new to this business.

---

### Post by darkod on 2010-02-23
It might be graphics driver related. At the main menu, hit F4 for advanced options, select Safe Graphics. Not sure if it goes back to the main menu to select Try Ubuntu again. Anyway, safe graphics should work, check it out.

---

### Post by ImTheBatman on 2010-02-23
> **darkod said:**
> It might be graphics driver related. At the main menu, hit F4 for advanced options, select Safe Graphics. Not sure if it goes back to the main menu to select Try Ubuntu again. Anyway, safe graphics should work, check it out.EDIT: I see what you mean.  Anyway, now I got to a command prompt like screen, but I can barely read what it says because it keeps flashing.

---

### Post by nanohead on 2010-02-23
Weird, I'm getting exactly the same thing.   Tons of "buffer I/O errors" and then black screen.

Never had a problem installing Ubuntu before.   Have 9.04 running great, but figured I'd try 9.10.   So far, not too impressed.  Taint working....

Its the exact machine that runs 9.04 perfectly, just put in another hard disk.  9.10 is a dud so far

:confused:

I've swapped Optical drives, cables, CPUs, hard disks, etc, and still nada

---

### Post by darkod on 2010-02-23
You are burning the CDs at low speed right? And when I say low, because todays CDs are about 56x, I mean no more than 8x. Even better 4x.

It could also be corrupt image, during download.

Usually you would expect the safe mode to work. Another alternative is to try booting from usb stick. It also saves CDs while trying if the burn was bad.

---

### Post by ImTheBatman on 2010-02-23
> **darkod said:**
> You are burning the CDs at low speed right? And when I say low, because todays CDs are about 56x, I mean no more than 8x. Even better 4x.

It could also be corrupt image, during download.

Usually you would expect the safe mode to work. Another alternative is to try booting from usb stick. It also saves CDs while trying if the burn was bad.

Running it from a USB stick is what caused the problem with F4 not doing anything that I edited out in my previous post.  I tried everything, doesn't seem to work :\

---

### Post by darkod on 2010-02-23
> **ImTheBatman said:**
> Running it from a USB stick is what caused the problem with F4 not doing anything that I edited out in my previous post.  I tried everything, doesn't seem to work :\

Sorry, but I'm out of ideas. Maybe using the Alternate Install CD can help. It has text based installer but you end up with the same system as with the live cd.

---

### Post by ImTheBatman on 2010-02-23
Heres what I managed to find so far: 1.When loading through CD: a.If I just try to boot Ubuntu normally the screen turns black and nothing happens  b.If I set my monitor to VGA (it's usually on DVI) I can see a bunch of colorful lines all over my screen, shaking  c.If I use safe graphics I get to a command prompt but the whole screen is flashing   2.When loading through USB:  a.same as 1.a  b.same as 1.b  c.I cannot find how to do safe graphics, F4 doesn't do anything and the advanced options menu is empty.  any help will be appreciated

---

### Post by nanohead on 2010-02-23
Yeah, the installer is pretty flaky on my gear at least.  It took me numerous tries to get it to run, but eventually it ran.  I think it didn't like my hardware (which is the first time EVER for a recent Ubuntu release).

I have a Biostar TA760G AMD/ATI based mobo, and usually it installs perfectly (last 2 releases), and been using cheapo ATI mobos for my Linux machine for years.  Never a problem until now

I actually went into BIOS and did a "load safe options" or something like that.  Then it started to load.   It hung a few times, but eventually it ran and loaded.

I think the installer has a bunch of problems, with disk detection, and certain runtime device drivers it needs.  It might even have trouble with video when it tries to load X/Nautilus, but I don't know.   Mine was especially flaky this time.   Reminded me of the old days when major surgery was required to get it to run on anything...

---

