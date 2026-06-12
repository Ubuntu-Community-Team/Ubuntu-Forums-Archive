---
title: "xserver was failing to start due to missing file, now hangs on startup"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by macaholic on 2009-01-28
After running a normal update two days ago, I was dismayed to realize that X had begun to fail on load due to a missing file (libxcb-xlib if I remember correctly). I deciphered that the reasoning behind the missing library as due to a conflict between libxcb1 and libxcb-xlib0 . Naively I attempted to fix this issue myself by installng the library from the source to no avail. This is when I made the mistake of force installing libxcb-xlib0, after that, x would start, but hang with just the X icon. As of rich now I have no GUI and no Internet access on this computer, I can However, install single packages that I could download elsewhere. I wanted to post here before filing a bug report in attempt to avoid redundncy and in hopes of  a possbile albeit unlikey "quick fix". Thank you for your time

---

### Post by tepsipakki on 2009-01-29
fixed already

libxcb (1.1.93-0ubuntu2) jaunty; urgency=low

  * libxcb1 should Breaks: libxcb-xlib0 instead of Conflicts:, since
    there are no file overlaps and Breaks will allow apt to better
    calculate an upgrade from intrepid.

---

### Post by macaholic on 2009-01-29
> **tepsipakki said:**
> fixed already

libxcb (1.1.93-0ubuntu2) jaunty; urgency=low

  * libxcb1 should Breaks: libxcb-xlib0 instead of Conflicts:, since
    there are no file overlaps and Breaks will allow apt to better
    calculate an upgrade from intrepid.

Alright then how would I fix this issue?

---

### Post by macaholic on 2009-01-29
I installed the newest version of libxcb1, and am now back to getting the original"
 "error while loading libxcb-xlib.so.0" type of error when attempting to start X. Am I missing something?

---

### Post by tepsipakki on 2009-01-30
do a apt-get dist-upgrade, something is missing from your system.

---

### Post by macaholic on 2009-02-02
Did that, all packages that can be updated have, sill getting the same error.

---

### Post by klange on 2009-02-04
I also have this issue, and nothing I do seems to fix it.

---

### Post by macaholic on 2009-02-12
Bump? Any resolution on this yet?

---

