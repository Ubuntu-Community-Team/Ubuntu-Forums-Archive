---
title: "boot up hangs due to &quot;Setting the system clock&quot;"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rwabel on 2008-09-22
Sometimes the boot up is hanging at [B]"Setting the system clock"

[/B]I have to power off the PC and power on again. After several retries it does then work to boot up. Anyone know why it hangs there? I didn't have that with ubuntu hardy so far.

---

### Post by rwabel on 2008-09-22
Just came around this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263928](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263928)

Seems to be what I do experience

---

### Post by Peter09 on 2008-09-22
Yeah, this is an on-going problem. Try holding a key down during the boot sequence. It works for me.

---

### Post by rwabel on 2008-09-22
thanks for the hint. Will try that

---

### Post by bimmerd00d on 2008-10-06
> **Peter09 said:**
> Yeah, this is an on-going problem. Try holding a key down during the boot sequence. It works for me.

lol why did that work?  I noticed it didn't do this when i first installed the Intrepid beta.  As soon as i ran update-manager and rebooted it started this.  It doesn't seem to be kernel related, as i can still select the old kernel and it still hangs.  holding a key works :lol:

---

