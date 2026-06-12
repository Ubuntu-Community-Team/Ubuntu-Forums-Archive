---
title: "Computer hangs after upgrading"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by stucliff on 2007-10-18
Today I've upgraded to 7.10 from 7.04. Everything seemmed OK in the process. But after resart my PC and when the log screen is suposed to appear, the screen goes out of signal and the computer do not respond.

What can it be?

Any idea how to solve it?

My hardware

Athlon XP 2400+

ATI 9200 SE

1GB RAM

---

### Post by electricmonk on 2007-10-18
Sounds like a similar problem I had/have on one of my 7.0.4 boxen. Try going to the boot menu when the grub loader starts and bring it up in safe mode ( I can't remember exact debian speak for this). This should all take place in text  and when complete you should be presented with a root prompt. Ctl-d to bring it on up - I suspect a race condition but have no proof and the problem only occurs about 1 reboot in 4.

---

### Post by stucliff on 2007-10-19
Booting in recovery mode and reconfiguring x server have solved the problem!

---

