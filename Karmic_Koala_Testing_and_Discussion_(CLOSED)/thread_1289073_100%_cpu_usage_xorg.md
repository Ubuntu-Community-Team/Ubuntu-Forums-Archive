---
title: "100% cpu usage xorg"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by AndersAA on 2009-10-12
Anyone run into this issue?  It's on an intel card, not 100% sure when it started but it's from this weekends updates atleast.

---

### Post by AndersAA on 2009-10-12
Note that this is with or without desktop effects, and cpu usage regardless of UXA/EXA driver path.

---

### Post by Laibcoms on 2009-10-12
Hmm, how do you check which processes are using CPU?  I tried "System Monitor" but it doesn't give me anything about processes that are using CPU, and I'm experiencing 100% CPU usage on my CPU2 (dual-core).

It might be related, since I noticed this after today's update, and xorg was one of the update I got.  (And it is only eating up CPU2.)

tnx!

---

### Post by taavikko on 2009-10-12
> **Laibcoms said:**
> Hmm, how do you check which processes are using CPU?

"top"
Is a CLI app.

---

### Post by Laibcoms on 2009-10-12
> **taavikko said:**
> "top"
Is a CLI app.

Thanks!

It **is** xorg on my end too that's eating up my CPU.

Using NVIDIA driver 185, for my GeForce 7300 LE.

---

### Post by todak on 2009-10-12
Log out, then log back in and the cpu usage drops to normal. I cannot figure what is causing this, but it seems to happen at each reboot.

---

### Post by TDK800 on 2009-10-12
> **todak said:**
> Log out, then log back in and the cpu usage drops to normal. I cannot figure what is causing this, but it seems to happen at each reboot.

Did upgrade from 9.04 to 9.10 yesterday, had the exact same problem, log out and log in fixes it for me too.

It was happening when the Nvidia driver version 185 wasn't even installed yet and after installing and enabling is happening too, maybe that helps to narrow it down.

---

### Post by andrewabc on 2009-10-12
It's a known bug on intel. There is a bug report and already a thread about it. No time to look.

EDIT:
Here is thread with bug report
[http://ubuntuforums.org/showthread.php?t=1272691](http://ubuntuforums.org/showthread.php?t=1272691)

---

### Post by Laibcoms on 2009-10-12
Yep, re-login works.

@andrewabc
I don't understand though.. "Intel" being the Processor or "Intel" video cards?

I have an Intel processor but NVIDIA for my video card, yet experiencing the same xorg CPU eating bug.

---

### Post by andrewabc on 2009-10-12
I have no idea if processor or graphics. :P

---

### Post by emarkay on 2009-10-12
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/439138](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/439138)

It looks pretty high in priority - may want to subscribe to this and see how it goes.

---

