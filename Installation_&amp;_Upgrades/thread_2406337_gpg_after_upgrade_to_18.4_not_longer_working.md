---
title: "gpg after upgrade to 18.4 not longer working"
date: 2018-11-19
forum: Installation &amp; Upgrades
---

### Post by vogel-kai on 2018-11-19
hi, after upgrade ubuntu from 16.4 to 18.4 gpg agent is not starting, got relocation error:
gpg-agent -v --daemon
gpg-agent: relocation error: gpg-agent: symbol assuan_sock_set_system_hooks version LIBASSUAN_1.0 not defined in file libassuan.so.0 with link time reference

any ideas?
regards Kai

---

### Post by vogel-kai on 2018-11-19
Agent is not running:
ai@X201ub:~$ gpg --export-secret-key
gpg: can't connect to the agent: IPC "connect" Aufruf fehlgeschlagen
gpg: error getting the KEK: Agent läuft nicht
gpg: WARNUNG: Nichts exportiert


-----
ai@X201ub:~$ gpg --version
gpg (GnuPG) 2.2.4
libgcrypt 1.8.4

**Enigmail Version 2.0.8 (20180804-1515)**

---

### Post by vogel-kai on 2018-11-20
solved

---

