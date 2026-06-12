---
title: "hal removal and dmraid"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by seamuso on 2010-04-05
should dmraid work without hal being installed? Is there something additional that needs to be configured?

I removed hal, rebooted, my raid5 had disappeared -

/dev/mapper/control was the only entry

I reinstalled hal, /dev/mapper also had the correct nvidia_cjfahbac and nvidia_cjfahbac1 entries and I was able to mount and access the array.

it's a 1.5tb raid5 (4x500GB) that has all of my virtualbox vm files that are shared across 2 operating systems.

---

### Post by Killigrew on 2010-04-06
hi

hal is officially removed, but still needed by some programs
so if you use one of those you still have to install it.
perhaps you can look at the project website of dmraid if
they are working on a release that doesn't use hal
or perhaps they already have one which is just not in the lucid repos jet...

greetings

---

