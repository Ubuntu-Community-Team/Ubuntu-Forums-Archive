---
title: "Problems with bluetooth mouse"
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-05-22
I'm using a Kensington Si670m bluetooth mouse instead of the laptops touchpad. It worked perfectly in Jaunty including the tilt wheel, but now, not so good. If I resume from hibernation, it won't work at all. And the cursor keeps jumping to the top-left of the screen sometimes, particularly when using the tilt wheel.

---

### Post by phenest on 2009-05-31
No one else?

---

### Post by davideotape on 2009-05-31
> **phenest said:**
> No one else?

sorry, don't have a Bluetooth mouse :(

---

### Post by Martey on 2009-05-31
I have a wireless Apple Mighty Mouse, but cannot replicate your issues. Maybe it's an issue with your specific model of mouse?

---

### Post by phenest on 2009-05-31
Hmmm, worked perfect in Jaunty.

---

### Post by phenest on 2009-07-23
Just installed Karmic alpha 3 fresh. Horizontal scrolling appears to be working (there is movement in the scrollbar), but the cursor keeps jumping to the top-left of the screen.

---

### Post by phenest on 2009-07-23
Incidentally, my touchpad works fine.

---

### Post by philcamlin on 2009-07-23
driver issue with the mouse?

maybe :P

just a guess since nobody else knows :popcorn:

---

### Post by phenest on 2009-07-23
> **philcamlin said:**
> driver issue with the mouse?

maybe :P

just a guess since nobody else knows :popcorn:

If so, where do I start?

---

### Post by mortti on 2009-07-25
It may not be the same issue at all, but I've got a Logitech 270(?) bluetooth mouse which stopped working after installing the Alpha 3. The strangest thing is, that it worked just fine when I had the 9.10 upgrade from 9.04 and before that. Not after installing the 9.10 Alpha 3 from the beginning it stopped working. That is: I must grant access for the bluetooth device all the time when the mouse gives a signal and still it won't get parity.

I read something about problems with decision whether to have bluez or blueman by default in Karmic. Maybe it's because of that?

The even more annoying thing is that my touchpad lost all it's "advanced" features i.e. the tapping and two-finger-scrolling just a few updates after the Alpha 3 install. Now it's pretty hard to use my laptop at all without a corded mouse...

---

### Post by ScarletPea on 2009-07-26
I too have a logitech 270. Stopped working after dist upgrade to Karmic.
 I tried the svn version of bluez, with the same results.

Turns out to be the kernel. I am using one of the 2.6.28's from Jaunty and bluetooth is back to normal.
Maybee try 2.6.30 and see if that works.

I'lle try and find a bug to post this on as well 8)

This prob. wont fix erratic behavior, but might help null behavior.

---

### Post by phenest on 2009-08-05
> **ScarletPea said:**
> I too have a logitech 270. Stopped working after dist upgrade to Karmic.
 I tried the svn version of bluez, with the same results.

Turns out to be the kernel. I am using one of the 2.6.28's from Jaunty and bluetooth is back to normal.
Maybee try 2.6.30 and see if that works.

I'lle try and find a bug to post this on as well 8)

This prob. wont fix erratic behavior, but might help null behavior.

Did you manage to find or report a bug for this?

---

### Post by phenest on 2009-08-08
Bump.

I'd like to report this, but no idea who to.

---

### Post by phenest on 2009-08-15
> **davideotape said:**
> sorry, don't have a Bluetooth mouse :(

I shouldn't have put 'Bluetooth' in the title. This is about the tilt wheel not working.

I have reported a bug. Don't know what package it comes under. [Bug 413971]("https://bugs.launchpad.net/ubuntu/+bug/413971")

---

### Post by phenest on 2009-09-07
This is now working due to an update today in the package xserver-xorg-input-synaptics (I'm guessing but it did coincide).

---

