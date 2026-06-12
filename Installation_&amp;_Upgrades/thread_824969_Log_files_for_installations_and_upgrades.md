---
title: "Log files for installations and upgrades?"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by noctivago on 2008-06-10
Hi all,

what is the log file (if exists) for the installations and upgrades of Ubuntu? In the last update, my video driver (restricted) was removed and now the UI runs slow.

---

### Post by unutbu on 2008-06-10
What program did you use to perform the installation/upgrade? For example, Synaptic, Adept, aptitude or apt-get?

---

### Post by noctivago on 2008-06-10
synaptic to install and update-manager to update =)

---

### Post by unutbu on 2008-06-10
Go to File>History.
The actual log files that Synaptic is reading are in
/var/lib/apt/lists/, but it is easier to just use Synaptic.

---

### Post by unutbu on 2008-06-10
Sorry -- I have to take that back. 
/var/lib/apt/lists/ does not seem to contain the info Synaptic uses to generate the History list.

---

