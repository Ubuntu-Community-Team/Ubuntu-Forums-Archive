---
title: "Does Java also misuse ext4?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-04-08
Hi folks,
Does Java (under the hood) also use ext4 without timely fsync() ?
Do I have to review the way I close files in Java?

Just wondering whether this is a purely C/C++ problem.

---

### Post by MacUntu on 2009-04-08
strace it.

---

### Post by gnomeuser on 2009-04-08
> **cl333r said:**
> Hi folks,
Does Java (under the hood) also use ext4 without timely fsync() ?
Do I have to review the way I close files in Java?

Just wondering whether this is a purely C/C++ problem.

It is not purely a language problem, it is an implementation problem.

You should review that Java does things in a way that is within the *does loathing make a sound? if so insert it here* POSIX specification.

---

