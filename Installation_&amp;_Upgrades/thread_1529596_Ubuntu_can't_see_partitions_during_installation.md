---
title: "Ubuntu can't see partitions during installation"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by saif_held on 2010-07-12
[SIZE=3]Hello everyone;

There's this guy, his English isn't that good, he posted a thread reporting his problem in Arabic and sadly he's a total beginner (maybe even worse)...

Anyhow, he has 5 partitions, all in NTFS. During installation the Ubuntu installer can't see the partitions, he used to use a 3rd party program to create/delete the partitions.

Any hints why this is happening?[/SIZE]

---

### Post by samikareim on 2010-07-25
[CENTER][FONT=Georgia]**[SIZE=5][COLOR=Sienna]pls help[/COLOR][/SIZE]**[/FONT]:(
[/CENTER]

---

### Post by kansasnoob on 2010-07-25
The first thing that jumps out at me is where saif_held says, "he has 5 partitions, all in NTFS."

Is this all on one hard drive? If so there's a 4 primary partition limit so that could pose a problem.

In order to get a better look at the exact situation we'd need to see some system specific info. The most useful thing would probably be the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It can be run from any Ubuntu (or most Linux) Live CD's or Live USB's and provides some basic info about partition structure, etc.

Even a screenshot of the entire drive/partitioning arrangement would suffice.

---

