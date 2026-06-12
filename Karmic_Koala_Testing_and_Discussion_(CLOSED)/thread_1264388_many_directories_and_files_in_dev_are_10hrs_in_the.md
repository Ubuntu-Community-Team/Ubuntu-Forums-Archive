---
title: "many directories and files in /dev are 10hrs in the future!"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-09-12
Hi Guys, I wonder if anyone else has this strange phenomenon? I also sometimes get a boot error message about something being in the future and have to reboot.
Cheers, Mike

---

### Post by Podex on 2009-09-12
So, what's the future like? Does Ubuntu have a new default theme yet?

---

### Post by mdurham on 2009-09-12
> **Podex said:**
> So, what's the future like? Does Ubuntu have a new default theme yet?

No, /dev still looks just like the old /dev. Boring but necessary!

---

### Post by dino99 on 2009-09-12
Lot of problems with that, like my system refuse to start. Just after begin the boot process, it fail to a maintenance shell with fsck error 16.
I've read on forum that is coz of "time in future".

Have to wait for some fixes.

---

### Post by taavikko on 2009-09-12
> **mdurham said:**
> Hi Guys, I wonder if anyone else has this strange phenomenon? I also sometimes get a boot error message about something being in the future and have to reboot.
Cheers, Mike

This should offer some advice:
[http://ubuntuforums.org/showthread.php?t=1252108](http://ubuntuforums.org/showthread.php?t=1252108)

---

### Post by MKdx on 2009-09-12
I had my machine rebooting quite few times with this problem before I relaized that the root partition was mounted as read only, and even after fsck says the problem is fixed, you find that it's not on reboot.

At the end, I had to to use a livecd to disable fsck for the root partition to allow me to login. I've enabled fsck the next day, and it seems fine so far.

Good thing I picked the LiveCD image of Karmic and not the alternative install though, otherwise I'd had to hunt for ext4 livecd.

---

