---
title: "System freeze on second suspend attempt"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by papangul on 2009-07-20
I am using ubuntu since 2005 but never faced problem with suspend on my intel hardware. Last week I upgraded from hardy to karmic(three distro upgrades in consecutive three days). I faced a lot of problems with jaunty so I decided to upgrade to karmic alpha. Things are better with karmic except a few minor problems and this major suspend problem.

First time the suspend/resume is working fine but when I am trying to suspend it again or to shut down or log out from my account or even lock the screen, the screen begins to tone down brightness and then when it is almost black the whole system freezes, so that I have to press the hdd reset button.I have not found any clue in dmesg or syslog.

There are bug reports in launchpad of similar problems in earlier releases, but not exactly the same problem.

Is anyone else facing this problem?

---

### Post by komputes on 2009-07-20
What version of ubuntu are you running and what is the make/model of your computer?

---

### Post by nperry on 2009-07-20
> **komputes said:**
> What version of ubuntu are you running and what is the make/model of your computer?

Hes running Karmic..

---

### Post by papangul on 2009-07-20
> **komputes said:**
> ...make/model of your computer?

Intel 810e chipset.

---

### Post by komputes on 2009-07-20
Does it not have a Manufacturer name (Dell, Asus, HP) and a model name and number (Inspiron, Eee, Proliant) etc. This is just to help me see if there are other similar reports for this hind of hardware. The chipset does not really help.

---

### Post by papangul on 2009-07-20
I assembled the machine myself,it is not a branded machine. From the hardware information I can see a lot of intel controllers, this intel chipset was very well known in it's days.

Suspend/resume is working multiple times from the gdm login screen, but after having suspended/resumed the machine once from the login screen, when I am logging into my account, the system is freezing at the next shutdown/suspend/logout/lockscreen attempt.

Today I will try to blacklist some kernel modules and then see what happens when I suspend the machine.

---

