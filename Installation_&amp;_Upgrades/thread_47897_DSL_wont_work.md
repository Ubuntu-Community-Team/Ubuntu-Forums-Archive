---
title: "DSL wont work"
date: 2005-07-10
forum: Installation &amp; Upgrades
---

### Post by kevver on 2005-07-10
I am trying to install Ubuntu on a system connected to my DSL modem.
When it tries to install networking, it can't connect and I have to skip and continue the installation.
It's just a simple bridge modem. ISP is SBC.
Mandriva 10.1 installation worked smoothly before on this machine.
Also my windows computer works with the modem and thru a router.

Why won't Ubuntu connect properly?

---

### Post by adwait on 2005-07-10
If you have tp supply a password etc. while connecting to the internet (ie: its not stored on the router itself) then skip that step in the installation and carry on. After you have installed Ubuntu, run pppoeconf if you DSL connection runs on PPPoE (mostly that's what they run on).

---

