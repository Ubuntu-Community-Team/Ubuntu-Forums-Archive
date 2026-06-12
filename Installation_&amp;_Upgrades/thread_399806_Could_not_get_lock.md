---
title: "Could not get lock"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by Liam1964 on 2007-04-02
When I try to install a new app, or upgrade using ADD/REMOVE or Synaptics I get the message below.

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I have posted this question on the new users page, but nobody is helping me ... does anyone here recognise this problem.

Please treat me like an idiot when replying, I am not an advanced user!

---

### Post by 23meg on 2007-04-02
You can only run only one package management program (Synaptic, apt-get, Update Manager, aptitude, etc.) at a time. If you launch a second one, you get that error.

---

### Post by Liam1964 on 2007-04-02
Sorry I forget to mention ...

I have already checked I am only running one package management software.
I can also upgrade using the sudo command line

The issue is I want to add some applications that I can not do using the sudo command because I do not know what I am doing

---

### Post by Liam1964 on 2007-04-02
Oh and now having read the bottom line on 23meg's message, I have done many many searches for this problem, and have come back with similar, but not the same.

---

### Post by 23meg on 2007-04-02
Is the update manager icon in your notification area greyed out?

---

### Post by Liam1964 on 2007-04-02
No it is bright red

---

