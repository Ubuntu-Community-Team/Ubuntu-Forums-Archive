---
title: "Can no longer add printer during preseed"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by carlexpc on 2015-04-23
Hi everyone,

I've been using preseed for my workstation installations since Trusty and I can successfully pre-install a printer. I've recently upgraded my preseed script for Vivid and I have noticed that
I can no longer pre-install a printer with the latest Ubuntu version and I get this error:

"lpadmin: Unable to connect to server: Bad file descriptor"

There might be some changes in the new Ubuntu version that triggered this problem.

---

### Post by dino99 on 2015-04-24
The main change i can think about is 'systemd' now used by default, instead upstart. But you can test booting with upstart (advanced boot option)
[https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers)

---

