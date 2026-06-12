---
title: "Autoinstall of Ubuntu 20  reboots during security upgrades"
date: 2020-12-28
forum: Installation &amp; Upgrades
---

### Post by scahartner on 2020-12-28
When trying to PXE boot the ubuntu installer I consistently run into a problem where during the installation of the security upgrades the host system (bare metal) reboots. This happens consistently and is rather tricky to diagnose. I tried to enable rsyslog logging, but this option is not yet available. 

Any pointers on:
[LIST]
[*]why the system is rebooting ?
[*]how I can diagnose the problem further ?
[*]is there an option to prevent the automatic reboot ?
[/LIST]

Much appreciated

---

### Post by CelticWarrior on 2020-12-28
Have you tried *not *installing the updates?
You can - and should - install them later, after the OS itself has been successfully installed.

---

### Post by EuclideanCoffee on 2020-12-28
If the reboot happens after the update, it's likely unrelated to the update itself. Ubuntu does not reboot like Windows does. You're also missing a step. First, the local cache must update before it can install. After it upgrades, then your computer is marked for a reboot to ensure the correct kernel is running. Regardless, your computer does not auto-reboot after an update. There's no way to avoid it if you're trying to install software from the Internet.

---

### Post by ajgreeny on 2020-12-28
I'm in full agreement with CW.

I have never once in the 16 years of using Ubuntu added either updates or the proprietary packages that are available when installing.  It is so much easier and faster to install the whole system without that activity slowing the process, normally taking me about 10 minutes maximum, then after a reboot I update everything and add whatever else is needed.

---

### Post by EuclideanCoffee on 2020-12-28
Automated installs typically update when configuring the main repository. I know this because behind a proxy, your installation will fail unless you first configure the proxy. You likely update but don't know during the installation process. You simply don't need to upgrade, so you don't apply the updates.

---

### Post by ActionParsnip on 2020-12-29
Installing updates is in I advise to avoid too. Just get the OS installed and you can mess with it when you are booted in to the installed OS

---

