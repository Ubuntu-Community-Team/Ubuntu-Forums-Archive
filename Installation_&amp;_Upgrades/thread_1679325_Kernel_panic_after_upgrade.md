---
title: "Kernel panic after upgrade"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Ouroborus on 2011-01-31
So, with the end of the month coming around, and since I'm on quota'ed internet, I figured I'd use take the opportunity to update my Ubuntu install.

Preface: I don't have a CD burner, or cds to burn.  The Ubuntu install discs I have are 7.04/7.10 cds I burned off a few years ago when I was a senior in college.

I was running Hardy Heron on my system (old Gateway, 32-bit Pentium 4 chip, NVidia 32 mb gpu, 1 gb ram, set to dual-boot Ubuntu and XP).  Started the system update, pressed yes, went to sleep.  Got up a couple times during the night, closed some error dialog box that was open, slept, checked it again, it said something about problems with dbs because it couldn't open messages or somesort.  When I woke up, the machine was off.  Booted it up.  Picked the top boot option, 10.04 LTS with generic 2.6.32.21 kernel.  Immediately after selecting that option, I get the following error message:

Kernel panic : VFS : unable to mount root fs on unknown-block(0,0)

I would like to avoid having to reinstall from 7.04 and reupdate everything, not to mention losing some small quantities of data and programs that were on the Ubuntu partition, and the time + bandwidth that costs.

So, what can I do to isolate where the problem is coming from, and figure out what (I'm guessing here) has become corrupted?

---

### Post by mörgæs on 2011-01-31
I don't think that it is worth the while to maintain a system that has been updated from 7.04/7.10. Rather go for a fresh install.

You must be able to burn a CD with 10.04 or 10.10 somewhere. This will also give you the option of running a live Ubuntu as a first step to see how the new versions behave.

---

### Post by Ouroborus on 2011-02-02
Regrettably, just because I must be able to do something doesn't mean I can -- one of the side benefits of living in the middle of nowhere means there's no store to stop by and buy a cd burner and a cd to burn to.

Any ideas on trying to salvage the Linux partition?  I've considered trying to boot into Linux off either a CD or USB drive, and then somehow mount an image to install from, I'm still reading into how that would work, but that doesn't help me figure out what went wrong in the first place.

---

