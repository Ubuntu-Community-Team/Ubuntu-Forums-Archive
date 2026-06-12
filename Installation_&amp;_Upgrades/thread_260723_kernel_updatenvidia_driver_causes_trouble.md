---
title: "kernel update/nvidia driver causes trouble"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by leoquantus on 2006-09-19
for the second time wthin 5 days a kernel and driver causes troubles. X doesn't start anymore.black screen. the first update did cause the seem problem. what to do?:confused:

---

### Post by crgutierrez on 2006-09-19
Is this the ndivia upgrade available for download today????????????????? I hate this early week surpirses.

Carlos

---

### Post by MKR. on 2006-09-19
I think they may be nudging security fixes in the kernel out a bit too quickly. I *just* got the notice that a vulnerability had been identified in the kernel from the ISC newsfeed...

I'm going to do what I usualy do and wait before updating. :P

---

### Post by neumeka on 2006-09-19
I am having these problems as well.  X-server will not start after an upgrade.  Does anyone know anything I can do?  I have already tried to downgrade x-server, but that didn't fix the problem.

---

### Post by wkulecz on 2006-09-19
Anyone with nvidia drivers try this new update set?

It was waiting for me this morning (was off yesterday).  Having been burned and wasting nearly a whole day on last weeks "update" I'll let someone else go first this time :)

If its the same issue I had last week you can edit /etc/X11/xorg.conf and change driver from "nvidia" to "nv"  you'll be running a much slower driver, but at least the system will boot.

--wally.

---

### Post by leoquantus on 2006-09-19
did ya made aX11/xorg.conf backup before updating?

---

### Post by neumeka on 2006-09-19
Wally,
This fixed my problem for now.  I guess I need to figure out how to   reinstall my nvidia drivers.
Thanks,
Kyle

---

### Post by wkulecz on 2006-09-19
Here is my thread from last week.  It has the links to how I was able to regress to working nvidia drivers.

[http://www.ubuntuforums.org/showthread.php?t=257347](http://www.ubuntuforums.org/showthread.php?t=257347)

HTH,
--wally.

---

### Post by geckomind on 2006-09-19
Dell laptop with nVidea drivers here. #27 kernel broke my X Desktop completely... I am booting the #26 kernel via GRUB right now.:mad:

---

### Post by wkulecz on 2006-09-19
I pitty the poor fool who only has one computer and is trying to upgrade it.  Doesn't matter if its Windows or Linux, if you have issues and no net access, its pretty much game over!

--wally.

---

### Post by leoquantus on 2006-09-19
even THORVALDS would not disagree on that WALLY[-X

---

