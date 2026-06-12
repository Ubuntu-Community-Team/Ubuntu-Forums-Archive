---
title: "12 KdeSudo popup at login"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jfbilodeau on 2009-10-19
Hello, world,

I'm getting 12 KdeSudo password prompt when I log into Kubuntu with the following message:

"No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit..."

Any ideas?

---

### Post by jfbilodeau on 2009-10-19
> **jfbilodeau said:**
> Hello, world,

I'm getting 12 KdeSudo password prompt when I log into Kubuntu with the following message:

"No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit..."

Any ideas?

Just to clarify, this started happening after I upgraded from Jaunty to Karmic.

---

### Post by todak on 2009-10-19
I have discovered that if I had a program running that required root access and then I restarted the computer without first shutting that program down, I would get the kdesudo message, too, as KDE is attempting to restart the program you left running at the time of reboot, but is attempting to start it without the password dialog.

---

