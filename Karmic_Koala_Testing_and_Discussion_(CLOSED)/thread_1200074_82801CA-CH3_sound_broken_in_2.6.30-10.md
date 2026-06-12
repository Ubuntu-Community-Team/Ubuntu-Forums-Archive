---
title: "82801CA-CH3 sound broken in 2.6.30-10"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by David Gerard on 2009-06-29
I installed Kubuntu 9.10a2 and sound was fine - kernel was 2.6.30-8-generic.

I promptly did a full upgrade, which took the kernel to 2.6.30-10-generic. Now sound doesn't work ...

The error notification is:

The audio playback device Intel 82801CA-ICH3 with AD1886A (Intel 82801CA-ICH3) does not work.
Falling back to .

Note that this is an incredibly generic Intel audio chip that's worked with Ubuntu since 5.04 ...

Any quick fixes? Just report a bug?

dmesg doesn't even mention the chip in question. It does mention module ac97, for what that's worth.

---

### Post by soapytheclown on 2009-06-29
My sound stopped working today too, but i did the kernel update a few days ago just randomly stopped i cant remmber if i even installed any updates tbh, it was working before lunch, came back restarted and it was dead! minw is an intel chip too btw:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by David Gerard on 2009-06-29
Reported as [bug 393629]("https://bugs.launchpad.net/bugs/393629").

---

### Post by David Gerard on 2009-07-01
OK, I did aptitude update;aptitude upgrade today and rebooted, and sound is back. w00t! Solved itself then :-D

---

