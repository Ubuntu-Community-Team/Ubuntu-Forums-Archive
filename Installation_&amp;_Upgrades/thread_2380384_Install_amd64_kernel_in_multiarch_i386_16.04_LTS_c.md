---
title: "Install amd64 kernel in multiarch i386 16.04 LTS computer"
date: 2017-12-16
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-12-16
I installed an amd64 kernel ina previously i386 machine. I assumed that all of the i386 packages would run under amd64 and that is mostly the case. However there is one serious problem I haven't been able to figure out. The network adapter on the mother board is not started properly. It works fine if I boot the old i386 kernel but not if I boot the new amd64 kernel.

There are few error messages I can track down.

During boot the ethernet card is found

syslog : Dec 16 14:38:04 hamlet systemd[1]: Found device RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Motherboard (one of many)).

But the interface is never brought up. I've checked everything I can think of now.

---

### Post by rsteinmetz70112 on 2018-01-21
During teh upgrade linux-generis-extras was not installed. Installing it solved the issue.

---

