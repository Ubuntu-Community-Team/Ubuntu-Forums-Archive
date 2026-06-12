---
title: "Another Grub error"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by dhess31 on 2009-11-23
After today's updates I can no longer boot into Windows 7.  I get an "invalid signature" error.

Running update-grub doesn't fix the problem, because it says Found Windows 7 (loader) on /dev/sdc1
grub-probe: error: Cannot find a GRUB drive for /dev/sdc1.  Check your device.map.

Any ideas?

Don

---

### Post by phillw on 2009-11-23
Hi, head over this way ---->   [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards,

Phill.

---

### Post by dhess31 on 2009-11-23
Thanks Phill, but none of those posts fixed my problem.

Don

---

### Post by namok on 2009-11-23
In the terminal type:```
cat /boot/grub/device.map
```Feedback paste to next message.

---

### Post by dhess31 on 2009-11-23
OK.  I managed to fix it.

Here's what I had to do:

I re-installed grub2 from a live-cd.  The first pass through, it STILL didn't see my Windows installation.

So I did a grub-install --recheck and THIS time it found all of them.

Then, I booted back into Ubuntu and did:

sudo update-grub

And THIS time it didn't have any warnings, and found all of my drives.

Now it works.  Don't know what caused the updates today (23th Nov) that did this, but now it is fixed.

Don

---

