---
title: "Ask Ubuntu Forums: Copy Protection of USB stick"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by mburris on 2007-07-21
Over the last month I have been working on a very interesting project:
Creating a PC that runs from a heavily customized LiveUSB stick version of Fesity Fawn.

Now that almost all of the work is done, I would like to start thinking about ways to prevent the linux system from booting if the usb stick's serial number is different from a predefined number.

Any Ideas?

---

### Post by kidders on 2007-07-23
Hi there,

Interesting idea. One way of doing that might be to encrypt the USB stick's filesystems using its own device UUID as part of the encryption key. I once did something similar with a desktop machine of mine, where I engineered it to boot successfully only if the correct USB device was plugged in at the time. Without it, dmcrypt (I imagine that's what I used) read the wrong encryption keyphrase (or none at all), and my root filesystem failed to mount.

Naturally, such a scheme -- or any other, for that matter -- would be easy to circumvent, if someone really wanted to though. Given access to the original USB disk, there would be no way to prevent someone duplicating it in workable condition. :-(

---

