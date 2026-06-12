---
title: "Upgraded from 16.04 to 17.10 and xorg exits immediately"
date: 2018-03-02
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2018-03-02
I seem to have gotten myself into a pickle.

I upgraded successfully from 16.04 to 17.10.  No errors, no problems, except that as soon as any user tries to log in on the greeter, it flashes black for a few seconds and then returns back to the greeter.  

I can log in on vt0 or vt1 with no problem, but if I try to run startx I get the same behvior; everything flashes black and then exits back to the terminal.

Xorg log files show no errors and no apparent reasons why this would be happening.

Any ideas?

---

### Post by cpdondo on 2018-03-02
So.. I did find that the i915 or intel Xorg driver is not loading.  I've reinstalled the xorg-intel package.  It's been so long and the system has been so reliable that I'm not really sure what I'm looking for.

---

### Post by cpdondo on 2018-03-02
Well, never figured out the problem, but I just emptied /etc/X11 and did a massive apt-get install --reinstall of everything xorg, and it worked.  Must have been some cruft left over.

---

### Post by #&amp;thj^% on 2018-03-02
> **cpdondo said:**
> Must have been some cruft left over.
+100
Glad you solved it && and thanks for posting your solution also. (This has always worked for me....knock on wood :) )

---

