---
title: "aptitude bug"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jamieleshaw on 2009-12-17
Hello, will this bug ever be fixed?, does anyone have a work around?
[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681)

---

### Post by VMC on 2009-12-17
> **jamieleshaw said:**
> Hello, will this bug ever be fixed?, does anyone have a work around?
[https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/128681)

According to reports there, it is Apt and not Aptitude error:

```
$ dpkg -S /etc/apt/apt.conf.d/01autoremove /etc/apt/apt.conf.d/01ubuntu
apt: /etc/apt/apt.conf.d/01autoremove
apt: /etc/apt/apt.conf.d/01ubuntu

This is a bug in the apt package, not aptitude.

```

---

### Post by jamieleshaw on 2009-12-17
Well, will that be fixed?
;)

---

### Post by VMC on 2009-12-17
Did you confirm that the problem still exists?

The file in question "/etc/apt/apt.conf.d/01ubuntu" is reported as having directives that causes the problem.

Right now the contents of 01ubuntu:
```
APT
{
};
```

With a date of 15OCT2009.

It appears they fixed the problem but didn't show the bug report confirmed.

If you ran across the same issue today, what were you doing?

We need to update the LP if we still have a problem.

---

### Post by jamieleshaw on 2009-12-17
Testing aptitude to see if it did it and it didn't.
Steps to reproduce
1. sudo aptitude install elinks - all is fine
2. sudo aptitude remove elinks - removes package elinks but does not remove it's installed dependencies

---

### Post by VMC on 2009-12-17
jamieleshaw, Can you update that LP bug, and tomorrow when I get up I will try what you did and also confirm the error. Thanks for finding this rather **old** bug.

---

### Post by jamieleshaw on 2009-12-17
Done, I noticed this because I'm in the process of documenting aptitude.

---

### Post by JBAlaska on 2009-12-17
I've only noticed this if I use apt **and** aptitude...If you use one or the other consistently, this conflict does not occur..or am I missing something?

---

### Post by jamieleshaw on 2009-12-17
I'd had been using apt-get.

---

### Post by mc4man on 2009-12-17
While I mainly use apt-get for a few reasons, aptitude will 'catch' them the next time it's run.

---

### Post by VMC on 2009-12-17
> **JBAlaska said:**
> I've only noticed this if I use apt **and** aptitude...If you use one or the other consistently, this conflict does not occur..or am I missing something?

I remember someone else mentioning this. They have separate databases, and you should only use one or the other.

I wonder how to prove this theory out.

---

