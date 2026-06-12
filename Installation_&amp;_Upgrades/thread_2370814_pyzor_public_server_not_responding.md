---
title: "pyzor public server not responding"
date: 2017-09-07
forum: Installation &amp; Upgrades
---

### Post by dramaekrs on 2017-09-07
Hi,

I've installed pyzor on three systems (an e-mail gateway on one site, an e-mail server on a second site, on my desktop) On all systems I opened port 24441. On every system I get no response on pyzor ping:
Artvark desktop:
~$ pyzor ping
public.pyzor.org:24441    (504, 'Reading response timed-out.')

Other Xenial systems:
~$ pyzor ping
public.pyzor.org:24441    TimeoutError:

Is the pyzor public server down?

Dominique.

---

### Post by ajgreeny on 2017-09-07
I can run **ping public.pyzor.org** without a problem but it could be the port 24441 that is the problem.

Unfortunately I know nothing about pyzor and do not have it installed so can not run the **pyzor ping** command.

---

