---
title: "systemd-shim not properly loaded"
date: 2019-03-17
forum: Installation &amp; Upgrades
---

### Post by robert48 on 2019-03-17
Hello

I am upgrading and have hit this error message. Repeat attempts to upgrade do not help.

> installed systemd-shim package post-removal script subprocess returned error exit status 2

What is systemd-shim? How do I get past this issue?

---

### Post by ubfan1 on 2019-03-17
See bug [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859)

---

### Post by robert48 on 2019-03-18
> **ubfan1 said:**
> See bug [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859)

Thank you! That fixed it. Quite a lot of info in the bug report so to slim it down for anybody following this fixed the issue for me:-

[https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859/comments/3](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1773859/comments/3)

---

