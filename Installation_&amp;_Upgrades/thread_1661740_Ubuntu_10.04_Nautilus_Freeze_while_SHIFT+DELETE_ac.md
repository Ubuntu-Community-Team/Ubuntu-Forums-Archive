---
title: "Ubuntu 10.04 Nautilus Freeze while SHIFT+DELETE action"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by stefanuswiely on 2011-01-07
Hello, I got problem with my Nautilus.

I use Ubuntu 10.04 (64bit) version, after I update system yesterday from 2.6.32-27-generic, suddenly my Nautilus freeze everytime I want to permanently delete files (SHIFT+DELETE).

Remove file to Trash will run OK, but when I empty trash, Nautilus will be freeze and I need to "Force Quit" it.

Please, help

---

### Post by andersgb1 on 2011-01-07
Yeah, me too. What's going on?

---

### Post by tomv on 2011-01-07
Since today I have the same probem (Ubuntu 9.10, 2.6.31-22 kernel).

---

### Post by jbrice on 2011-01-07
Same here over the past few days (10.04 32-bit).

---

### Post by jbrice on 2011-01-07
Hmmm - do you guys use RabbitVCS by any chance? 
I wonder if this is the issue:
[http://blog.rabbitvcs.org/archives/280](http://blog.rabbitvcs.org/archives/280)?

---

### Post by tomv on 2011-01-07
> **jbrice said:**
> Hmmm - do you guys use RabbitVCS by any chance? 
I wonder if this is the issue:
[http://blog.rabbitvcs.org/archives/280](http://blog.rabbitvcs.org/archives/280)?

jbrice, thanks for the hint. I do use RabbitVCS and it sounds like this might be the issue. I'll update RabbitVCS and check the issue when I am back at office.

---

### Post by oliver69 on 2011-01-07
I have the same issue in Lucid since 0.14-1. Meanwhile there is an upstream bug: [http://code.google.com/p/rabbitvcs/issues/detail?id=459](http://code.google.com/p/rabbitvcs/issues/detail?id=459)

Did anybody found a link to a previous .deb to downgrade?

---

### Post by stefanuswiely on 2011-01-07
> **jbrice said:**
> Hmmm - do you guys use RabbitVCS by any chance? 
I wonder if this is the issue:
[http://blog.rabbitvcs.org/archives/280](http://blog.rabbitvcs.org/archives/280)?

Yes, I use RabbitVCS.
I will try update the RabbitVCS next monday :)

Thank you for information.

---

### Post by jbrice on 2011-01-08
> **stefanuswiely said:**
> Yes, I use RabbitVCS.
I will try update the RabbitVCS next monday :)

Thank you for information.

No problem :)

Have just had the PC auto-update Rabbit to 0.14.1-1~lucid, but this exhibits the same behaviour. Also find that right-clicking in Thunar freezes the desktop completely, so not just a Nautilus problem. This is still a very sick Rabbit.

Uninstalling the Nautilus and Thunar plugins followed by restart and things seem back to normal. Fortunately I am not doing any development right now so can live without Rabbit for a while.

---

### Post by stefanuswiely on 2011-01-09
Problem solved after update the rabbit :D

---

### Post by tomv on 2011-01-10
The update of rabbit also solved the problem for me after restarting nautilus after the update.

---

### Post by jbrice on 2011-01-10
Now working fine here also after latest update of RabbitVCS from repo.

---

### Post by andersgb1 on 2011-01-10
Yup, mine also works now :D

---

