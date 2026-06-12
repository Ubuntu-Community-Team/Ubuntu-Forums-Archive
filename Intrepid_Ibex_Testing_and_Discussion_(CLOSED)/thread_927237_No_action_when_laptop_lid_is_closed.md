---
title: "No action when laptop lid is closed"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by roja on 2008-09-22
I noticed that the screen is not blanked when the lid is closed on my HP 530. When testing the other options for AC power as well as Battery power none of them works (apart from "Do nothing"). It works OK with HH and Sidux running live from CD. 
Is it only me?

---

### Post by mrtenl on 2008-09-23
Hey, I also got a HP 530, and i have the exact same problem.
Default behavior for my laptop in hardy when the screen was closed was to suspend if on battery, and black out the screen when on AC. After the upgrade to ibex, my computer doesn't seem to notice when the screen is closed.

Also, suspend and resume doesn't work, have tried both the 'hibernate' and 'uswsusp' packages.
uswsusp gives me this error:
morten@loltop:~$ s2both 
/dev/mem: Permission denied
s2both: Could not lock myself. Reason: Cannot allocate memory
morten@loltop:~$ sudo s2both 
[sudo] password for morten: 
s2both: Could not stat the resume device file. Reason: No such file or directory

the suspend-command works, but my laptop fails to wake from the suspend.

---

### Post by Nullack on 2008-09-23
Please consider looking for an existing bug on LP about this, and subscribing to show your support. If there isnt an existing bug, you could report a new one.

---

### Post by mrtenl on 2008-10-02
Where do i search for existing bugs? And how do i report a new one?

---

### Post by ktp on 2008-10-02
> **mrtenl said:**
> Where do i search for existing bugs? And how do i report a new one?

Here are some links:
[https://bugs.launchpad.net/ubuntu]("https://bugs.launchpad.net/ubuntu")
[http://www.ubuntu.com/community/reportproblem]("http://www.ubuntu.com/community/reportproblem")
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by mrtenl on 2008-10-03
Thanks :)
I could not find any previous, similar bugs, so i reported it. Can be found here: [https://bugs.launchpad.net/ubuntu/+bug/277534](https://bugs.launchpad.net/ubuntu/+bug/277534)

---

### Post by mrtenl on 2008-10-06
> **roja said:**
> I noticed that the screen is not blanked when the lid is closed on my HP 530. When testing the other options for AC power as well as Battery power none of them works (apart from "Do nothing"). It works OK with HH and Sidux running live from CD. 
Is it only me?

Hej grabben :)
If you could register at launchpad and confirm the bug i posted, we may have a chance of it being fixed in the final 8.10 release.
[https://bugs.launchpad.net/ubuntu/+bug/277534](https://bugs.launchpad.net/ubuntu/+bug/277534)

---

