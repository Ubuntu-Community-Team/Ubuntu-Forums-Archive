---
title: "Problem trying to use ubuntu-bug command"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-25
i'm trying to use this command to attach debuggin information to bug number and i get this messege 

i'm translating so it might not be accurate process identifier that  pointed does not belong to any software. ubuntu-bug alone however does work.


how can i fix this problem?


thanks in advance.

---

### Post by mdurham on 2010-02-25
Hi aviramof,
I also found that didn't work. Try the following

> 
See: [http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/](http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/)

$ ubuntu-bug (package name here)
eg.
	$ ubuntu-bug network-manager      	# report a bug on Network Manager
	$ ubuntu-bug linux                	# report a bug on the Linux kernel

The man page for ubuntu-bug contains more examples.

---

### Post by aviramof on 2010-02-25
thank you.

as you can see here this is the bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/526375](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/526375)

and i have been told to run this command ubuntu-bug 526375 and as i said it didn't worked i tried ubuntu-bug #526375 and i'm not sure but maybe it worked.

---

### Post by dino99 on 2010-02-25
> **aviramof said:**
> thank you.

as you can see here this is the bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/526375](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/526375)

and i have been told to run this command ubuntu-bug 526375 and as i said it didn't worked i tried ubuntu-bug #526375 and i'm not sure but maybe it worked.

seen your bug report, but some months ago when all the apport hooks have been started to be created, i remember that the process to report has been modified: so ubuntu-bug <<package name>> work but not ubuntu-bug <<bug number >>. Maybe i am wrong but i think it's how it work now, not a bug, as if you report against a known bug, you just need to validate that bug by "affect me too" on top of that report. Running ubuntu-bug << package name>> automatically brings you to that bug's number.

---

### Post by aviramof on 2010-02-25
but i'm the one who opened this bug.

---

### Post by philinux on 2010-02-25
> **aviramof said:**
> i'm trying to use this command to attach debuggin information to bug number and i get this messege 

i'm translating so it might not be accurate process identifier that  pointed does not belong to any software. ubuntu-bug alone however does work.


how can i fix this problem?


thanks in advance.

```
apport-collect 526375
```

ubuntu-bug can be used with a package name or pid or running program not a bug report.

---

### Post by aviramof on 2010-02-25
thank you very much.

---

