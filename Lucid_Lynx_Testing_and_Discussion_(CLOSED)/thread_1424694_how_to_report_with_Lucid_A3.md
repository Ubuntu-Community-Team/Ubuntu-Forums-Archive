---
title: "how to report with Lucid A3 ?"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-03-08
Reporting when there is a crash work but we fall into troubles on the other cases:

- ubuntu-bug ALWAYS complaint that "genuine packages" are not genuine.
- apport-collect refuse to report if we are not the owner of that number's bug.
- there is a lot "silent problem" not detected by apport.

So, is there an other way to report ?

---

### Post by robertwall on 2010-03-08
> **dino99 said:**
> - ubuntu-bug ALWAYS complaint that "genuine packages" are not genuine.

This never happens for me. Are you sure you're typing the package name properly (do you have an example of one that isn't working?)?

> So, is there an other way to report ?
See [these instructions]("https://help.ubuntu.com/community/ReportingBugs#Filing bugs at Launchpad.net"). But you really should figure out why ubuntu-bug isn't working.

---

### Post by dino99 on 2010-03-08
> **robertwall said:**
> This never happens for me. Are you sure you're typing the package name properly (do you have an example of one that isn't working?)?


See [these instructions]("https://help.ubuntu.com/community/ReportingBugs#Filing bugs at Launchpad.net"). But you really should figure out why ubuntu-bug isn't working.

i'm not alone with this problem  ](*,)

---

### Post by kansasnoob on 2010-03-08
Please give us an example or two of specific packages so we can look into it.

---

### Post by dino99 on 2010-03-08
Here are examples:

ubuntu-bug metacity

ubuntu-bug gnome-panel

apport-collect 41870

i've tried to workaround by purging/reinstalling packages, but no succeeded.

[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/497796](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/497796)
[https://bugs.launchpad.net/ubuntu/+source/apport/+bug/527026](https://bugs.launchpad.net/ubuntu/+source/apport/+bug/527026)

---

### Post by itsjustarumour on 2010-03-08
> **kansasnoob said:**
> Please give us an example or two of specific packages so we can look into it.

nm-applet
network-manager

- get error message that "...not a valid Ubuntu package" or words to that effect (not at that machine at the mo).

---

