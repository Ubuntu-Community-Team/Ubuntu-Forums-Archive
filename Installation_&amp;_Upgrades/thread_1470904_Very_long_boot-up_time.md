---
title: "Very long boot-up time"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Axellink on 2010-05-03
Hey Guys

I have installed both the Ubuntu 10.04 and the NBR version on my Toshiba NB200 Netbook but come across this annoying problem.  It takes ages for the OS to boot up.  I am dual booting so i select Ubuntu and then I see a cursor flashing at the top left hand corner for the next 4-5 minutes before I see the login screen.

I do not have anything connected to the Netbook and I have chose the "install Ubuntu side to side with other OS" option on set up.  I only have 1 HDD which is partitioned.  The weird thing is, once I've logged in, everything flies really smoothly.  XP doesn't have the same issue as well.

As stated before I have tried both the NBR and the normal version and still come across the same annoying issue.

---

### Post by Axellink on 2010-05-03
"I just went into my BIOS and changed **SATA Controller Mode** to **Compatibility  **from** AHCI** and viola successful boot!

I'm guessing there is a driver for AHCI which may be disabled or not  loading at boot before it tries to mount / but this is just conjecture  based on a similar problem with Windows installations I've had with  these machines."

The above resolved my issue

---

### Post by MoheySaleh on 2010-05-14
thanks for posting the solution. i had the same issue and now it's solved.

---

