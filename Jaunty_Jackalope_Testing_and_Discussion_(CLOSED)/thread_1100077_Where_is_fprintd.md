---
title: "Where is fprintd?"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-03-18
So I noticed that the GNOME 2.26 release notes mentioned support for integrating with fprintd, so users can enroll fingerprints for login via gnome-about-me. (Came as a surprise to me; I thought it was still a bit unstable, being worked on specifically with Fedora).

However, it doesn't appear any package in Ubuntu's repositories provides fprintd :/
We have libfprint, but the fprintd command doesn't exist and gnome-about-me does nothing.

Any news on this?

---

### Post by stoffe on 2009-03-19
I wondered the same thing, and I'm also curious if it's possible to get this to work, or if I should try one of the older methods available. I'm just now setting up a Thinkpad with Jaunty and there's Thinkfinger, possibly among others, but I'd prefer this way I think.

---

### Post by scaine on 2009-03-19
Hey Stoffe - long time no see.  Where've you been?

I have access to USB-based UPEK fingerprint scanners, so if you find any updates regarding fprintd, please post back and I'll get some testing done.

---

### Post by taavikko on 2009-03-19
Does this pkg have to be manually installed
**libpam-fprint** before testing it,

Don't have hardware to test it. But after reading this, I'll suspect that it is needed
> If a system is configurated for allowing fingerprint authentication, users can enroll their fingerprints via Desktop &#9656; Preferences &#9656; About Me from the panel menu.

---

### Post by noworry on 2009-03-20
I tried to install libpam-fprint, but still i don't see the option of finger print reader in "About Me" !!

---

### Post by stoffe on 2009-03-21
It seems you need to install this: [http://reactivated.net/fprint/wiki/Fprintd](http://reactivated.net/fprint/wiki/Fprintd) which for now includes compiling not only the daemon itself but also a new version of libusb from git. Seems noone has made a deb for this anywhere that I can find, yet. :)

> **scaine said:**
> Hey Stoffe - long time no see.  Where've you been?

Hehe, hello there! To be perfectly honest, I grew really fed up with the steady decline of signal-to-noise in the forums. I usually return at least for a while every time I've installed a new development version though. ;) There's always something... :D

---

### Post by stoffe on 2009-03-21
Found a PPA, but with failed build at least for now...

[https://launchpad.net/~kachristmas/+archive/ppa/](https://launchpad.net/~kachristmas/+archive/ppa/)

---

