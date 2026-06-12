---
title: "Error creating child process for this terminal"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Aries K on 2009-09-15
Hi, after recent updates my terminal fails to launch. The error message is "Error creating child process for this terminal". Does anyone have any ideas? Thanks in advance.

---

### Post by FuturePilot on 2009-09-15
I know this was a problem in Jaunty, not sure if it's still a problem in Karmic. But this is what I found. [https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927]("https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927") You might want to check if /dev/pts and /dev/shm are mounted.

---

### Post by zika on 2009-09-15
> **Aries K said:**
> Hi, after recent updates my terminal fails to launch. The error message is "Error creating child process for this terminal". Does anyone have any ideas? Thanks in advance.That was due to the problem with upstart today. The problem is resolved with the upgrade. Yes, /dev/shm and /dev/pts were not created among other things. I bit of mess that is cleaned now, I hope.

---

### Post by Aries K on 2009-09-15
> **zika said:**
> That was due to the problem with upstart today. The problem is resolved with the upgrade. Yes, /dev/shm and /dev/pts were not created among other things. I bit of mess that is cleaned now, I hope.

That fixed the problem thanks. I had to update in CLI then reboot. Terminal, Synaptic, and Update Manager are back to normal now. :popcorn:

---

