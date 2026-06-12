---
title: "How to prevent Apache from Autostart?"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by midnightflash on 2007-03-10
Hi there,

how can I prevent, f.e. apache or snort, to autostart at boot?
Using Edgy but will be the same with Feisty.

Thank's in advance...
Midnightflash

---

### Post by Captain_Riker on 2007-03-12
Hi,

Either System -> Sessions -> Startup Programms
or System -> Administration -> Services

or, what I prefer,

open a Terminal -> enter sudo apt-get install rcconf -> run rcconf from Console.

This will allow you to change the startup scripts/Services for the current runlevel.

Greetings
Captain_Riker

---

