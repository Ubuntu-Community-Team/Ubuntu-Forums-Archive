---
title: "System freezes"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by t.letum on 2008-07-28
I am encountering a very strange issue. From time to time the whole system freezes. To unfreeze it I have to move my mouse or type something on the keyboard. It's very annoying.
Some technical information:
32 bit Ubuntu 8.04 on T9300@2.5GHz, 2GB RAM.

I experience this problem once in every 5-20 seconds! I can't even start my system without clicking <ctrl> during the boot process.

Freeze looks like everything is paused. The screen doesn't go black - it's normal, I can see what is happening, or how every action is paused (even animations on websites). The system unfreezes immediately after providing some input.

It looks to me like the global system timer (does exist something like that?) is pausing and, as the effect, every single task doesn't know that in the real world some piece of time elapsed. After providing some input, the timer resumes and all the tasks start their work like there haven't been any pause. The exception is system time - after system have frozen I waited 2 minutes: freeze-time 14:08; resume-time: 14:10. There haven't been 14:09!

I haven't tested it on battery (don't have any right now), only on main power.

Any ideas how to fix it?

---

### Post by Pumalite on 2008-07-28
Check screensaver>Power Management>Turn sliders all the way to the right.

---

### Post by t.letum on 2008-07-28
Didn't help.

---

### Post by t.letum on 2008-07-29
I added "acpi=off" to the kernel's boot options and Ubuntu started to work properly. I mean, as much properly as it can without it :/ It's ridiculous if laptop has no acpi, so my problem is not resolved yet..

---

### Post by t.letum on 2008-08-06
Any help?

---

