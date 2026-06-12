---
title: "Boot Splash disappears at: Reading files needed to boot..."
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by loko on 2008-10-17
Hello,

i just installed the Intrepid from daily-live from today.
It installed fine. First boot was with a nice boot-splash but after reboot, this boot-splash disappears and the boot enters text-mode at: 

Reading files needed to boot...


usplash.conf is ok, the right resolution is in there.

i did updated the initram, helped nothing.

somebody have an idea about that?

---

### Post by FuturePilot on 2008-10-18
I noticed this same thing today when I booted up. I thought it was something I did, but apparently not.

---

### Post by FuturePilot on 2008-10-20
I found this bug report.
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990")

Sure enough my swap partition had a different UUID.

---

