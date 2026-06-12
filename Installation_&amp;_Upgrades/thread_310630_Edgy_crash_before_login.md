---
title: "Edgy crash before login"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by tswoolway on 2006-12-01
Just installed Edgy on a previously Windows only laptop. However, it won't boot past the login screen: about 4 secs after the username box is brought up the screen freezes and I have to do a powercycle to recover at all. I tries exiting into a tty session before this happened but it crashed anyway, I believe the process that is crashing is klogd (the login process)?

Here is as much detail from the screen as I could scribble on a bit of paper:

Stacktrace:
00000018 c04936c8 00000268 c012bca7 00000000 00000286 cc801400 c037ee60

Proc: klogd (pid: 3852, task ccfca580)

Kernel panic- not syncing, fatal exception in interrupt.


Windows now has a 13GB partition, which leaves Ubuntu with about 7Gb, which I think should be big enough.

Does anyone have any idea? I'm really keen to start using ubuntu.

Cheers,

Tom

---

### Post by linusr on 2006-12-16
I too face a similar problem with Edgy.

Edgy boots normally till X-server starts and then system goes to stand by(possibly)

So, I had to restart  but it does'nt occurr everytile (5/10)

What could be thr reason? How do i check logs to find the reason?

---

