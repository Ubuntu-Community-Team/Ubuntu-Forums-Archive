---
title: "Screen not locked on suspend"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by papangul on 2009-07-31
Post todays update, I find that the desktop screen is resuming in 'unlocked' state. Anyone else noted this?

---

### Post by graaant on 2009-07-31
> **papangul said:**
> Post todays update, I find that the desktop screen is resuming in 'unlocked' state. Anyone else noted this?

I've got this too. 
Can't seem to lock screen at all.

---

### Post by papangul on 2009-07-31
I can lock the screen, no probs with that.

I faced the problem of not being able to lock the screen earlier, reinstalling gnome-screensaver fixed that. Also ensure that the screensaver item is checked in System>Preferences>Startup Applications.

---

### Post by graaant on 2009-07-31
> **papangul said:**
> I can lock the screen, no probs with that.

I faced the problem of not being able to lock the screen earlier, reinstalling gnome-screensaver fixed that. Also ensure that the screensaver item is checked in System>Preferences>Startup Applications.


Ah, that'll be why I can't lock then. I didn't realise locking was dependent on screensaver and disabled it.
Thanks for the tip!

---

### Post by phenest on 2009-07-31
Just in case that doesn't work for others, open the Configuration Editor and check the suspend item under apps/gnome-power-manager/lock/suspend.

---

### Post by papangul on 2009-07-31
> **phenest said:**
> Just in case that doesn't work for others, open the Configuration Editor and check the suspend item under apps/gnome-power-manager/lock/suspend.
Nothing works here, that suspend item is checked here, but still the desktop screen will resume in an unlocked state.:confused:

---

### Post by Jay_Bee on 2009-07-31
I can confirm this, is there a bug report for this?

---

### Post by phenest on 2009-07-31
[Bug 407315]("https://bugs.launchpad.net/ubuntu/+bug/407315")

---

