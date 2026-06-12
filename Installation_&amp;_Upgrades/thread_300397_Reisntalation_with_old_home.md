---
title: "Reisntalation with old /home"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by dark_templar on 2006-11-15
I reinstalled Ubuntu in my system where I already had, in a separate partition a /home directory. In the instalation options, I chose where to install the / and then the /home without reformating  it. The problem is that now the installation does not recognize the old /home/me saying there is no home for my user, even if in the instalation I indicated where the old /home was. How to fix this?

---

### Post by Irony on 2006-11-15
Check that the following is in your fstab file;

[PHP]/dev/hda?       /home      ext3    defaults        1       2[/PHP]

Where ? is the number of your home partition.

---

### Post by dark_templar on 2006-11-16
It's more like

/dev/hda?       /home      ext3    defaults        0       2

---

