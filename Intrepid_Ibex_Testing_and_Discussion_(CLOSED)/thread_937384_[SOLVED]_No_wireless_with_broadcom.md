---
title: "[SOLVED] No wireless with broadcom"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by slugicide on 2008-10-03
So, I upgraded to the beta on my laptop.  Only to find I no longer have wireless.  Now I'm screwed (I know.  But I thought a beta at least would have working wireless [wouldn't you?]).
So, I'm asking if there's a solution.  Broadcom on a Dell E1505.  fwcutter is installed, but whatever driver it installed didn't work.   

Please help?

---

### Post by Hatfield on 2008-10-03
Do you have the b43 driver installed?
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by slugicide on 2008-10-03
> **Hatfield said:**
> Do you have the b43 driver installed?
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)


Yes.  
I should mention, in case it matters, that this computer came with 802.11 draft n support.

---

### Post by slugicide on 2008-10-03
It appears the problem was the new kernel was not compatible with the driver.

---

### Post by JacquiOh on 2008-10-04
Sorry to butt in but what did you do to fix it? I'm having the same issue I think!

---

### Post by slugicide on 2008-10-04
No problem.  When you start your computer you will see more than one kernel.  The topmost one will be chosen automatically.  Try one below it, with the next lowest number.  That should solve it.  Sorry I don't remember which kernel versions were talking about.

---

