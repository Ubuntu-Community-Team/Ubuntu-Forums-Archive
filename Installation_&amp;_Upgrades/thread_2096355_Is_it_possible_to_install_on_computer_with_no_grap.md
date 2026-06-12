---
title: "Is it possible to install on computer with no graphic output?"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by miloske on 2012-12-19
I'm just curious - is it possible to install Ubuntu on a laptop with dead graphic card (no picture on monitor and no output on VGA port)? Could the installation process be somehow automated (including the network settings)?

---

### Post by cwsnyder on 2012-12-19
The simplest solution would be to SSH into the computer after it booted with a Live CD which was set up to receive SSH, then continue the install from the remote computer.  Of course, you would be setting up the computer as a server, and would have to check in through remote access every once in a while to check for problems/reports.

---

