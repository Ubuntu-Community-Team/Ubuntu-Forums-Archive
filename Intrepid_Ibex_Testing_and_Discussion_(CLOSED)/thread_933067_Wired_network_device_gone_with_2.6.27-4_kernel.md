---
title: "Wired network device gone with 2.6.27-4 kernel"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdide on 2008-09-29
Hey intrepid testers, 

When I upgraded to 2.6.27-4 something wierd happened. My wired network device - good old eth0 (ibm thinkpad t61p) was gone, and instead I have a device called pan0 which is down, and I can't seem to ifup it.

I have might some non-default network setting from 6.10, but I mean .. the wired network .. that should just work, shouldn't it?

---

### Post by nebosuke on 2008-09-29
My guess is that you are using an intel device in your T61p for networking.
Please read the sticky **[Intrepid tester WARNING: Corruption of Intel e1000e Gigabit Cards]("http://ubuntuforums.org/showthread.php?t=927943")** for more information regarding this issue.

---

### Post by Delvien on 2008-09-30
Which could of rendered your NIC inoperable - perminately. Hope it didn't..

---

