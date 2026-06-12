---
title: "Unpacking in dpkg takes for ages..."
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zika on 2010-03-13
As of today, maybe yesterday, in any kind of installation or upgrade unpacking part of the process is soooo looooong... Anyone else having that "problem"... I've canceled several installations because I thought something was wrong with the .deb files, but I was wrong. Unpacking tool is to blame...

---

### Post by DoeRayMe on 2010-03-13
Yep got this problem too

---

### Post by timosha on 2010-03-13
Ditto

---

### Post by zika on 2010-03-14
Today, it would, almost, be faster for me to compile kernel myself, than what it takes for dpkg to upgrade 2.6.34-999... It took less than a minute, befor...

---

### Post by mc4man on 2010-03-16
Have also noticed, though not all the time - but most.
This update today seems to address this 
> dpkg (1.15.5.6ubuntu3) lucid; urgency=low

  * Revert fsync during package unpack for now; it's unacceptably slow for
    packages with lots of small files, and we can't ship beta-1 this way.
    We'll do something better once it's decided upstream (LP: #537241).
 -- Colin Watson < [email]cjwatson@ubuntu.com[/email]>   Tue, 16 Mar 2010 10:04:38 +000


---

### Post by zika on 2010-03-17
> **mc4man said:**
> Have also noticed, though not all the time - but most.
This update today seems to address thisI wouldn't like my machine to crash now, without fsync, while unpacking some stuff, kernel .deb for example...

---

### Post by zika on 2010-04-20
It was quick, for some time, but it slows, again, it seems... Not so radically as before, but...

---

### Post by zenarcher on 2010-04-20
Same here.  Seems to unpack very, very slowly!

zenarcher

---

### Post by Arla on 2010-04-21
Going to bump! I'm updating my "test" system that I've not updated in a while, and it's taking, AGES to unpack everything.

---

### Post by mc4man on 2010-04-21
> it was quick, for some time, but it slows, again, it seems... Not so radically as before, but...

Well another change (you can usually retrieve changelogs from synaptic

> dpkg (1.15.5.6ubuntu4) lucid; urgency=low

  * Backport from upstream:
    - Restore fsync during package unpack (LP: #559915).  This is now done
      by deferring the fsync and rename for normal files in tar extraction
      so that it's done in one pass afterwards, to avoid massive I/O
      degradation due to the serialization from each write + fsync. 

---

### Post by Longinus00 on 2010-04-21
I guess Theodore Ts'o fsync suggestion was ridiculous after all. :rolleyes:

---

### Post by Yellow Pasque on 2010-04-21
It's good to know that I wasn't imagining it :P

---

