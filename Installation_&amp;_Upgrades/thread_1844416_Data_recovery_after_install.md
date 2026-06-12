---
title: "Data recovery after install"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by bumbleman123 on 2011-09-15
Hi,

Basically, what I'm wondering is if the reformat that ubuntu performs when installing is a full (low level) format or a quick (high level) format?

Thanks in advance for your help

---

### Post by Mark Phelps on 2011-09-17
Low-level formats require special software.  That is NOT what Ubuntu does.  It only does the typical filesystem reformats, which means basically, that it erases the contents of the partition table -- but in reality, leaves the actual data intact.  That's how data recovery apps work -- they look for files and directories that are still intact.

---

