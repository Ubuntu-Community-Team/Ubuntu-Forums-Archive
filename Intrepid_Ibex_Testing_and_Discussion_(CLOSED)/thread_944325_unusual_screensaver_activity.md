---
title: "unusual screensaver activity"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zapcojake on 2008-10-11
Hello, I upgraded from Hardy to Intrepid using update-manager -c -d.  My screen in Hardy used to just fade to black after being idle for 10 minutes.  Since the upgrade after 10 minutes go by the screen begins to fade but then just brightens back up.  The screen never goes black, even if left all day.   I have a MSI GeForce 8600 using the driver from the repo's.  I combed through dmesg output but didn't see anything.  Should I file a bug report?

---

### Post by Pogo on 2008-10-11
See this bug:
[https://bugs.launchpad.net/bugs/273787](https://bugs.launchpad.net/bugs/273787)

---

### Post by zapcojake on 2008-10-11
So should I take any further action?

---

### Post by jblackhall on 2008-10-11
better bug report:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/278112](https://bugs.launchpad.net/ubuntu/intrepid/+source/compiz/+bug/278112)

You have a couple of different options for how to fix it temporarily as said in there.  Disable compiz, check the option in compiz settings, or just lock your screen when not in use.

---

### Post by Pogo on 2008-10-11
Thanks jblackhall, marked [https://bugs.launchpad.net/bugs/273787](https://bugs.launchpad.net/bugs/273787) as a duplicate.

---

### Post by zapcojake on 2008-10-11
I am ok here, I just wanted to make sure the bug has been reported.

---

