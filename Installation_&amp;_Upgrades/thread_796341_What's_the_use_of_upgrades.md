---
title: "What's the use of upgrades"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by aaargh486 on 2008-05-16
Today I have got 5 updates waiting. All to fix one bug:
 don't use dh_strip -s twice to no break the dbgsym variants

First of all: why is this included in the recommended releases? How many Ubuntu users will need this except for the developers?
And why do I have to download 5.3 MB to fix one bug. I thought one of the purposes of splitting packages is to have smaller updates?

PS: It may seem like one, but this is no rant. It's an honest question.

---

### Post by DieB on 2008-05-16
well it is included in the recommended, cause it does not fix any security issues.

to your question:
well different packages seem to be affected by this bug, so you have 5 "updates" + as far as I assume the update process delivers you with new packages, that fix the bug in the old ones, so they are not patches (thats why 5mb).
whoo needs it? probably only devs - i don't know - but as this problem might occure in normal use, everyone who uses (means has that package installed) might benefit from the update.

---

