---
title: "Kernel panic"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nixie Pixel on 2009-02-16
I had a kernel panic tonight.  My uname:

```
Linux raptor 2.6.28-7-generic #20-Ubuntu SMP Mon Feb 9 15:43:21 UTC 2009 i686 GNU/Linux

```

I had several windows of Firefox open (Firefox has been crashing like crazy recently in Jaunty), and Thunderbird, which was in the foreground.  I was reading an email.

The thing I did to cause this was to take my hand off my USB mouse, which I had been using since boot, and double-tap my laptop touchpad, which I hadn't touched since boot (and may not have even touched it since I installed Jaunty).

Can anyone help me troubleshoot a kernel panic?  What steps should I take to find out exactly how it happened?

Thanks!

---

### Post by iponeverything on 2009-02-16
Is it reproducible with the method you described?

If so, go to launchpad and open a bug report.

The first step in diagnosing and fixing a kernel panic is being able to reliably reproduce the panic. 

If the panics happen at seemingly random times, it might be flaky memory.

---

### Post by ronacc on 2009-02-16
also check /var/log/kernel.log  and /home/<you>/ .xsession-errors  and >system>administration>system log  to see if there are any messages at the time of the panic . also if you can reproduce it you might want to install kerneloops  .

---

### Post by Nixie Pixel on 2009-02-17
I haven't been able to reproduce it, unfortunately...

---

### Post by ronacc on 2009-02-17
then it may not be a bug , I had a flaky middle button on a usb mouse that drove me crazy for a while ,it only happened rarely and could not be reproduced on demand making it very hard to track down . since it happened when you were double tapping your touchpad , if it does recur try adjusting your doubleclick delay .

---

