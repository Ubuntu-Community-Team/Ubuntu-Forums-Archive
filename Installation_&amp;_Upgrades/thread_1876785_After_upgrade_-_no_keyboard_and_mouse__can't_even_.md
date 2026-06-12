---
title: "After upgrade - no keyboard and mouse  *can't even use recovery"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by j3st3rc on 2011-11-06
I upgraded standard Ubuntu 11.04 to 11.10, and now it boots up fine, grub works fine, but I cannot input anything from my mouse or keyboard. My keyboard/mouse set is the logitech mx5000/1000 bluetooth. I am running on an amd 64 bit.

I tried live booting kubuntu aswell and at the screen that says "try" and "install", I get no keyboard/mice input.

Any ideas on how to fix it?

---

### Post by raja.genupula on 2011-11-07
[http://ubuntuforums.org/showthread.php?t=1292477](http://ubuntuforums.org/showthread.php?t=1292477)

---

### Post by j3st3rc on 2011-11-07
> **raja.genupula said:**
> [http://ubuntuforums.org/showthread.php?t=1292477](http://ubuntuforums.org/showthread.php?t=1292477)

This didn't help, but thanks.

-My keyboard does nothing in recovery
-alt+sysrq+r does nothing
-mouse does nothing

All works until ubuntu loads.

---

### Post by j3st3rc on 2011-11-08
Any chance of getting some help?

---

### Post by j3st3rc on 2011-11-10
bump.....

---

### Post by darkod on 2011-11-10
Any chance of connecting a wired keyboard temporarily? I guess the bluetooth receiver doesn't work properly and hence the keyboard set.

---

### Post by j3st3rc on 2011-11-10
> **darkod said:**
> Any chance of connecting a wired keyboard temporarily? I guess the bluetooth receiver doesn't work properly and hence the keyboard set.

I don't have a wired keyboard :(

---

### Post by darkod on 2011-11-10
If you boot with the cd in live mode, do they work? I mean live mode of 11.10.

---

### Post by j3st3rc on 2011-11-10
> **darkod said:**
> If you boot with the cd in live mode, do they work? I mean live mode of 11.10.

Live mode as in the "try" option?

When i boot it from the cd it goes to the screen to select "try" or install. There it freezes just like on the login screen.

---

### Post by darkod on 2011-11-11
There is really not much to do with the keyboard and mouse not working. How about borrowing a usb keyboard from a neighbor/friend? Any chance of that?

Probably all you need is a few minutes to start it with a working keyboard and install the bluetooth properly.

---

### Post by j3st3rc on 2011-11-11
> **darkod said:**
> There is really not much to do with the keyboard and mouse not working. How about borrowing a usb keyboard from a neighbor/friend? Any chance of that?

Probably all you need is a few minutes to start it with a working keyboard and install the bluetooth properly.
  I have a laptop, can I somehow connect it to the laptop?

---

### Post by bsniadajewski on 2011-11-27
I don't believe using a wired USB keyboard will work yet, j3st3rc.  Ther has been a bug report [#854967]("https://launchpad.net/bugs/854967") filed for the package friendly-recovery.  When you boot into recovery to do anything, it will show the menu but the keyboard will not respond to any keypresses.

---

