---
title: "Question regarding apt-get updates/upgrades..."
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by OrangeCrate on 2008-10-11
Generally, when there are updates, I opt for apt-get to update and upgrade. Then I run through the clean, autoclean, and autoremove options to keep things tidy.

**When there has been a package held back, I normally use apt-get dist-upgrade to release it. **Yesterday, by doing that, like many, I lost my desktop.

I haven't been burned until this time, and **I'm wondering if my** update/upgrade **strategy on held back packages is a good one, or not.**

Comments?

---

### Post by ktp on 2008-10-11
What I do is, I try to stay way from partial update.  If I see one I would just wait a day and see if it resolves it self...specaily when in alpha/beta install.  Most of time this will work.

When I do partial update, using apt-get dis-upgrade, I make sure it is not removing something critical.  If you are not sure if you need it or not, then just wait and see or do little research.

---

### Post by jblackhall on 2008-10-11
In general I think it's a bad idea unless you're sure that what's being removed is supposed to be removed.  I had a topic on this (except using update manager and/or synaptic).  Essentially dist-upgrade is the same thing as "partial upgrade" in Update Manager I think.

[http://ubuntuforums.org/showthread.php?t=942744](http://ubuntuforums.org/showthread.php?t=942744)

---

### Post by plun on 2008-10-11
This is a development version and nearly all dev versions breaks more or less.

This is basic knowledge

[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)


Everyone also have a search function directly to Ubuntus repo within
Firefox 3 (just to change with the arrow to "**Ubuntu package search**").

---

### Post by OrangeCrate on 2008-10-11
O.K., thanks all.

I think I was more interested this time, with getting another cup of coffee, than in what was actually being deleted. I'll have to pay more attention in the future.

Lesson learned.

---

