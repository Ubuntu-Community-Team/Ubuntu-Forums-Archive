---
title: "Migrating Wubi Install to Another Computer"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by JPS913 on 2011-01-30
Hey Guys,

I've been using a wubi install of Ubuntu 10.10 for the past few months on my girlfriend's laptop, which has less hardware issues than my more recent laptop. Now that I'm a little more versed in Ubuntu, I'd like to transfer my Wubi install onto an actual partition on my laptop drive for a traditional dual boot.

Is this possible, and if anyone's done this before, would you be able to spare a few minutes and outline the process? I wouldn't know where to start and how to do things since I'm dealing more or less with a file system acting like a partition than an actual one.

I found the steps of migrating a Wubi install to partion via the Wubi Guide, but it seems those are steps for migrating a wubi install to a new partition on the same computer.

Any help would be appreciated. Thanks.

---

### Post by bcbc on 2011-01-30
You can migrate from just the root.disk file. I have a script that does it. 

It runs from a live CD and will work provided:
1. the entire install is on the root.disk (e.g. no separate home.disk)
2. it uses grub2 (installed originally with release 9.10 or later)
3. you already know what kernel boot options you will need on the new computer (if it requires anything special).

There shouldn't be a problem migrating from one computer to another unless you have custom drivers installed for hardware that isn't present on the new computer.

PS the steps are very similar to the standard wubi migration (to the same computer)

---

