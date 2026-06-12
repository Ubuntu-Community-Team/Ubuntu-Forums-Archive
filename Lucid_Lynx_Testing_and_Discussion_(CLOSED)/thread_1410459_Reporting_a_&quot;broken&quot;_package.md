---
title: "Reporting a &quot;broken&quot; package?"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tr333 on 2010-02-18
I have submitted a [bug report for calendarserver](https://bugs.launchpad.net/ubuntu/+source/calendarserver/+bug/426778) requesting upgrade to the latest upstream release.  This package is currently uninstallable in both karmic and lucid and should either be fixed or removed from the archive.  What is the best way to notify the Ubuntu/MOTU devs that this package is broken?

---

### Post by Ibidem on 2010-02-18
Launchpad.

(I.e. the report you filed)

---

### Post by SevenMachines on 2010-02-19
hi, your bug is already assigned. A quick look suggests the problem is the dependencies of the new version of calendarserver, which need to be resolved before it can get into debian. which then someone needs to decide whether or not it would be ok to introduce not only the new calendarserver but also these new dependencies into lucid without causing problems.

---

### Post by tr333 on 2010-02-19
I understand that the best solution lies with waiting for Debian to update, which appears to be happening (slowly).  The problem I have is that the package in it's current state is uninstallable and should be removed from the archive if it's not going to be fixed/updated.  It's better to not have it at all than have it broken and leaving a bad experience for anyone that tries to use it (although the best option would be to get the package fixed).

---

### Post by SevenMachines on 2010-02-19
i think the reason for removing the package is when its broken and not developed, in other words would never be fixed, which obviously isnt true in this case. theres still a couple of months to make freeze exceptions before release which might be reasonable in this case. it can also be backported if it doesnt reach debian in reasonable time. best wait and remind the assignee if its in debian and can therefore be merged if possible

---

