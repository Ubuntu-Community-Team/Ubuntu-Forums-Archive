---
title: "minor bug in nautilus"
date: 2009-01-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-07
This is a minor bug, but I noticed if you use nautilus to create a share and don't have the program installed it will prompt you to get it.  All is well and good unless another synaptic is running.  You get the typical error stating it is running, but nautilus thinks that it installed the service.

---

### Post by danf_1979 on 2009-01-07
You should report this bug on launchpad, or it will go without notice.

---

### Post by cariboo on 2009-01-08
That isn't a bug, it is normal operation, apt puts a lock file in /var/cache/apt/archives while synaptic is running. The lock doesn't allow another program to download packages into the archives directory until it is cleared. Closing synaptic or update manager clears the lock file.

Jim

---

### Post by steeleyuk on 2009-01-08
Thats not the problem. Nautilus thinking that the service has been installed when it hasn't is the bug.

---

### Post by LordVeovis on 2009-01-08
> **danf_1979 said:**
> You should report this bug on launchpad, or it will go without notice.

[https://bugs.launchpad.net/ubuntu/+bug/315901](https://bugs.launchpad.net/ubuntu/+bug/315901)

Reported

---

### Post by LordVeovis on 2009-01-11
Can anyone else please reproduce this so we can confirm it?

---

### Post by MadsRH on 2009-01-11
Perhaps you could post a step-by-step list on how to reproduce the bug so we can confirm it?

---

### Post by chrisccoulson on 2009-01-11
Also, the bug should be reported against nautilus-share, and not nautilus

---

### Post by LordVeovis on 2009-01-11
> **chrisccoulson said:**
> Also, the bug should be reported against nautilus-share, and not nautilus

This is my first bug report, sorry :(

Also the steps to reproduce were on the bug report itself, here they are:

> I think this bug may be in nautilus somewhere.

Prerequisites: Have another package manager open and in use. And not have the packages installed that are needed for file sharing.

If you open nautilus and right click a folder. Go to 'Sharing Options' and share the folder. If you did not have the samba packages installed it will prompt you to download them. Because another app has a lock on it, it will tell you something along the lines of it's busy try later. That works as intended. When you click 'ok' nautilus assumes the package has successfully installed. It does not check.

---

### Post by LordVeovis on 2009-01-11
It's been moved.  It's against nautilus-share now

---

