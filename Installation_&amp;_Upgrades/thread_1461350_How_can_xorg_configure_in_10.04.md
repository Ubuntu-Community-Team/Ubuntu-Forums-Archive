---
title: "How can xorg configure in 10.04?"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by strawberry on 2010-04-24
Came from 8.04, fresh install. The monitor was not detected properly, I have 1024x768 max resolution on a 1280x1024 screen. As 10.04's xorg has no xorg.conf file, I cannot tell it the right data. What and where are the new config files please?

---

### Post by wojox on 2010-04-24
What video card/chip do you have:

```
lspci | grep VGA
```

---

### Post by strawberry on 2010-04-24
Hi,
nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
It has solved yet. I copied the xorg.conf from the backupped 8.04 system to the new 10.04.
I know it shouldn't be the proper solution.

---

### Post by quadproc on 2010-04-24
> **strawberry said:**
> Came from 8.04, fresh install. The monitor was not detected properly, I have 1024x768 max resolution on a 1280x1024 screen. As 10.04's xorg has no xorg.conf file, I cannot tell it the right data. What and where are the new config files please?
The newer Ubuntu versions do not require an xorg.conf file.  If the system does not have one then the X server looks at the hardware and makes its best guess for setting things up.

If your system does have an xorg.conf file then the X server will read it so you should be able to use the file that used to work for you.

quadproc

---

### Post by strawberry on 2010-04-25
quadproc,
it's clear now, thanks for the clarification.
strawberry

---

### Post by quadproc on 2010-04-25
> **strawberry said:**
> quadproc,
it's clear now, thanks for the clarification.
strawberry
You are welcome.  Glad that you have a solution now.

quadproc

---

