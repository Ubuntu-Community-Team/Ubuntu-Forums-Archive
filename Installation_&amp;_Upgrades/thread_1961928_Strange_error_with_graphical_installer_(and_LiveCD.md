---
title: "Strange error with graphical installer (and LiveCDs)"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by gebauer on 2012-04-20
Hi all,

I'm trying to install Ubuntu (12.04 LTS beta2 in the moment) on a PC, which is running Windows 7 already.
It has a onboard video chip called something like VIA chrome 9 in Windows' device manager.

Whenever I start into the graphical installer of Ubuntu (regardless whether I use ACPI=off or not) I see the attached screwed up interface.

I tried to use the alternate installer, but as soon as I press "Install" I get a black screen and nothing happens.

Interestingly I had similar graphic problems with the current GParted Live CD rendering them unusable as well. So it seems a similar driver problems with both distributions.

I once installed WUBI on that PC, and it worked okay. Altough the speed were dreadfull, that's why I decided to go for a "real" dual-boot system.

I appreciate any hint what I can still try.

Regards,
Jan

PS: The cursor is in the upper right corner of the screen...

---

### Post by darkod on 2012-04-20
Except with acpi=off, have you also tried with 'nomodeset' ?

---

### Post by gebauer on 2012-04-20
> **darkod said:**
> Except with acpi=off, have you also tried with 'nomodeset' ?

Well, I tried both together (unaware what both settings really do, I'm afraid).

Regards,
Jan

---

### Post by darkod on 2012-04-20
nomodeset is for the video drivers, if the problem is there. If that didn't work, I have no other ideas right now...

---

### Post by gebauer on 2012-04-20
No it doesn't change anything... But thanks for your efforts so far...

Jan

---

