---
title: "Nautilus, says 'trashing files'"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-08-30
So I wanted to reboot into one of my other partitions. When I clicked  restart, this messege window pops open. Was kinda scary the way it's worded. What did it mean any ways?
Thanks

---

### Post by maheshasolkar on 2009-08-30
Yes. I saw that yesterday too. Wonder what the deal is. I'll probably open a bug if I see that again.

---

### Post by VMC on 2009-08-30
Are you guys keeping current on updates. That has stopped for me a couple of days ago. After kernel 8 and some updates that followed.

---

### Post by DougieFresh4U on 2009-08-30
> **VMC said:**
> Are you guys keeping current on updates. That has stopped for me a couple of days ago. After kernel 8 and some updates that followed.

I have been getting nautilus crashes when I boot machine. When I log in and desktop appears, crash icon appears for 'nautilus'. But the issue today is when I want to log off/reboot.
 I find the wording  of the messege is rather amusing.

---

### Post by VMC on 2009-08-30
> **DougieFresh4U said:**
> I have been getting nautilus crashes when I boot machine. ...
 I find the wording  of the messege is rather amusing.

Your getting the nautilus crash message when you boot? I've never heard of anyone reporting that before. Only reboot or shutdown.

ps-Yes, I agree, the message your getting is amusing.

---

### Post by Eromatic on 2009-08-30
I was experiencing this issue after distro-updating today while running the 32bit version of Karmic under VirtualBox-Hardy32bit.

---

### Post by taavikko on 2009-08-31
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/419184](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/419184)

---

### Post by Seventh Reign on 2009-08-31
> **VMC said:**
> Your getting the nautilus crash message when you boot? I've never heard of anyone reporting that before. Only reboot or shutdown.

ps-Yes, I agree, the message your getting is amusing.

This is why I stopped using Debian Lenny.  Nautilus crashes 100% of the time on bootup with it.

Karmic, however, I havent had any significant problems with ... yet.

---

### Post by tekstr1der on 2009-08-31
> Your getting the nautilus crash message when you boot? I've never heard of anyone reporting that before.

Bug #403549: nautilus crashed with SIGSEGV immediately after start up
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/403549](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/403549)

Fix is committed upstream.

As for this thread's topic, the bug was fixed in the latest nautilus.
```
nautilus (1:2.27.91-0ubuntu2) karmic; urgency=low

  * debian/patches/90_git_change_fix_inhibit_issue.patch:
    - git change to fix an inhibit issue (lp: #419184)


```

---

