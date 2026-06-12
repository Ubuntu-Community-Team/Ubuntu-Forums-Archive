---
title: "Blank screen when attempting to install"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by jazz53 on 2010-06-02
I can not load  from Live CD 10.4
Sequence:

1. Boot CD drive, Ubuntu loading screen appears with 5 blinking red dots
2. Red dots all light up and then monitor blanks out
3. CD is spinning still, and activity lights are blinking but the  monitor does not work at all

have a ati radeon 5700.
Tried both 32 & 64bit,  screen blanks and continues to load. can not get screen back
Must  be a video driver problem.
I do not want to install yet, but have used live cd's for trouble shooting on other comps.

Help Please

---

### Post by dino99 on 2010-06-02
try with nomodeset on the boot line

---

### Post by jazz53 on 2010-06-02
Ok just tried 9.10.
No Problem , fired right up.
It is not my comp, it is a problem with 10.4

---

### Post by jazz53 on 2010-06-03
OK tried the "nomodeset" with no success.
Still blank screen

---

### Post by jazz53 on 2010-06-05
bump

---

### Post by wojox on 2010-06-05
> **dino99 said:**
> try with nomodeset on the boot line

Try default xforcevesa

---

### Post by jazz53 on 2010-06-05
Sorry I am a Newb
Please explain how to
"default xforcevesa"
I am trying to use the "live CD"

Thank You

---

### Post by davidmohammed on 2010-06-05
when the install options appears (language etc) - press F6 - should display the boot options.  Edit the boot options to include

nomodeset xforcevesa

before "quiet splash"

---

