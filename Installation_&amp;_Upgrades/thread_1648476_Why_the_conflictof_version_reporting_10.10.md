---
title: "Why the conflictof version reporting 10.10?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2010-12-18
So I installed Ubuntu 10.10 on a brand new system.  NOw looking around Ststem / About Ubuntu reports that I'm running 11.04 Natty Narwhal but System / Administration / System Monitor still reports 10.10 - That sounds right since I never saw a version upgrade come through.  

But how does this happen?

---

### Post by kansasnoob on 2010-12-18
This bug:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

> Thanks for reporting. This is a known issue caused by a bad commit changing the entities used in help for the Maverick branch too, not only for the Natty branch. This will be fixed soon, hopefully, it is a very simple fix.

---

