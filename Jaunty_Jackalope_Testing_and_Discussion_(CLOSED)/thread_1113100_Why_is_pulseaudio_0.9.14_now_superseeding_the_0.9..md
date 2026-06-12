---
title: "Why is pulseaudio 0.9.14 now superseeding the 0.9.15 test packages?"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-04-01
The nerve of the Ubuntu devs adding "1:" to their versions.

---

### Post by chrisccoulson on 2009-04-01
You could read the changelog perhaps
> pulseaudio (1:0.9.14-0ubuntu16) jaunty; urgency=low

  * Introduce epoch to fix my stupidity in uploading a test release of
    pulseaudio.

 -- Luke Yelavich < [email]themuso@ubuntu.com[/email]>  Wed, 01 Apr 2009 14:04:33 +1100

---

### Post by zekopeko on 2009-04-01
> **chrisccoulson said:**
> You could read the changelog perhaps

naaah... it's easier to be bash. /s

---

### Post by Kow on 2009-04-01
Yea adding an epoch wasn't the way to fix the problem, in fact it probably created more problems for them. Oh well what is done is done.

---

### Post by chrisccoulson on 2009-04-01
> **Kow said:**
> Yea adding an epoch wasn't the way to fix the problem, in fact it probably created more problems for them. Oh well what is done is done.

How would you have fixed the problem then? This is exactly what the epoch is for with the Debian version numbering system

---

### Post by Kow on 2009-04-01
> **chrisccoulson said:**
> How would you have fixed the problem then? This is exactly what the epoch is for with the Debian version numbering system

Append something like +actually0.9.14 to it. Now when they try and sync/merge pulseaudio with debian all kinds of issues will arise... most of their automated scripts probably won't work with the epoch.

---

### Post by plun on 2009-04-02
Yeah... what a mess with todays kernel update....  crap..;)

The test 7 package can be downloaded from here

[https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003396.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-April/003396.html)

I lost all sound hardware after todays update, back with the test 7 package.

:guitar:

---

