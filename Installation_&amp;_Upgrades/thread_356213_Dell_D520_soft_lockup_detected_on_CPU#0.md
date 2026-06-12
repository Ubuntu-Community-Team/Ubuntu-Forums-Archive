---
title: "Dell D520 soft lockup detected on CPU#0"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by bandie on 2007-02-08
Hi
trying to install edgy on a brand new Dell latitude D520, Windows XP runs fine, inserting the Edgy DVD, live CD boots as far as the bouncing orange progress bar then changes to a black screen with the following

* Activating Swap....                                          OK
mount: Function not implemented   
* Checking file systems...                                  OK
fsck 1.39 (29 May-2006)

[17179633.996000] BUG: soft lockup detected on CPU#0


whats going on?
any ideas?

---

### Post by bandie on 2007-02-08
seems to have been a CD/DVD issue as using the alt CD install appears fine

---

### Post by veloce on 2007-02-09
I got that error after having to power off after hibernation crashed the system. Wouldn't even boot into recovery mode.

To get it to work again, I changed some BIOS settings :
	turned off wireless (cause I'm not using it at the moment)
	turned off anything that looked like it was meant for windoze, including USB emulation

Booted into recovery mode and it worked.  Rebooted and system started normally.

---

