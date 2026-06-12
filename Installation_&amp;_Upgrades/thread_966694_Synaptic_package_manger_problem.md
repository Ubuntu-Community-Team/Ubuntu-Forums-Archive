---
title: "Synaptic package manger problem"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by ZoOorO on 2008-11-01
Hello, when i start SPM and wants to install updates i get this message[html]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
[/html]

please help me fast, i also can't setup flash the terminal run starts and closes down at the same moment :/

---

### Post by roger_1960 on 2008-11-01
Hi

Open terminal  applications-accessories-terminal and then copy (or type) into it at the prompt

sudo dpkg --configure -a

then enter your password (which wont appear) and you will have done what is needed.  The problem would have been that your download was interupted.  This command should fix it.

---

### Post by ZoOorO on 2008-11-01
> **roger_1960 said:**
> Hi

Open terminal  applications-accessories-terminal and then copy (or type) into it at the prompt

sudo dpkg --configure -a

then enter your password (which wont appear) and you will have done what is needed.  The problem would have been that your download was interupted.  This command should fix it.
wow thanks alot :D!! really great support!!

---

