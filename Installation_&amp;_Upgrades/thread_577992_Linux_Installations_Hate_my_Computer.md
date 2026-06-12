---
title: "Linux Installations Hate my Computer"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by flummoxed on 2007-10-16
Every time I try to reinstall Ubuntu, I have to jump through hoops just to get the install to complete. The Desktop graphical install has NEVER worked once, although it obviously works for other people, because ubuntu still uses it. The 7.10 - rc1 install graphic install crashed. So i switched back to the trusty old alternate install, which usually crashed 3 or 4 times before I manage to get it installed properly.

This time, no dice. I got an even stranger error than normal... apparently APT couldn't find a KERNEL to install! I've never heard of this one... but I guess maybe it's because of the release candidate status... does anyone know more about this?

My CD's are always md5sum'd and the disc integrity after the burn is verified.

So I thought Okay... ubuntu installations never work, maybe some other distro will work. I downloaded PCLinuxOS, to give it a test drive. Got most of the way through the graphical installer, and then that disappeared without a word. Needless to say, the install didn't work.

I then tried the full Sabayon CD, which got 89% in a text mode installer of the way there then also crashed. I tried PCLinuxOS again after that, which ultimately failed but magically managed to install GRUB, much to my joy, so I can now boot my windows XP partition again, which is what I'm currently using. 

3 different distros on 3 verified CD's... alternate installers and everything...  they ALL failed. This computer has a history of failing the linux installs. So what the hell is up?

Here is my hardware:

AMD X2 3800+
2 Gigs DDR2 RAM
EVGA Geforce 7950GT KO
80 Gig Western Digital Hard drive (WD800JD-00LSA0)
250 Gig Western Digital Hard Drive (WD2500KS-00MJB0)
both hard drives are SATA

The way it's partitioned is this:

**80 gig drive**
15 gig / partition 
60 ish gig /home parition
2 gig swap

**250 gig drive**
80gig windows installation partition
160 ish gig my documents partition

Any thoughts?

---

### Post by -grubby on 2007-10-16
get a new computer?

---

### Post by Scheater5 on 2007-10-16
My 2 cents worth - X11 doesn't like your video card.

---

### Post by buzzmandt on 2007-10-16
don't know if it will help but i had the same problems with my desktop.  Could not get any live cd's to even work, let alone a graphical install

I went into bios and disabled apci as well as a few other nonstandard bios options and now i have no problems.  now live cd's work just fine and i can install graphically.

---

### Post by flummoxed on 2007-10-16
> **nathangrubb said:**
> get a new computer?

More like get an old one :roll:

> **Scheater5 said:**
> My 2 cents worth - X11 doesn't like your video card.

Probably...

---

