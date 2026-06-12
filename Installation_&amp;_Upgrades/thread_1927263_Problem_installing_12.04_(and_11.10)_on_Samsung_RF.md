---
title: "Problem installing 12.04 (and 11.10) on Samsung RF510"
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by maribr on 2012-02-17
Hello,
I'm having problems in installing precise on Samsing RF510 laptop [**(Spec)**]("http://www.samsung.com/us/computer/laptops/NP-RF510-S02US-specs")
Installation process just breaks in certain moment. Same situation occured with 11.10 installation.
[**Syslog of 12.04 installation**]("http://pastebin.com/178NEf60")
From what I see the problem is somewhere in here:
ubuntu install.py: Exception during installation:
ubuntu install.py: Traceback (most recent call last):
ubuntu install.py: File "/usr/share/ubiquity/install.py", line 657, in <module>
ubuntu install.py: install.run()
ubuntu install.py: File "/usr/share/ubiquity/install.py", line 130, in run
ubuntu install.py: self.copy_all()
ubuntu install.py: File "/usr/share/ubiquity/install.py", line 437, in copy_all
ubuntu install.py: self.db.progress('SET', 10 + copy_progress)
ubuntu install.py: File "/usr/lib/python2.7/dist-packages/debconf.py", line 60, in <lambda>

Can someone point me in the right direction with a solution
BR
marib

---

### Post by gordintoronto on 2012-02-17
12.04 is Alpha software. It is expected to break, and when you report problems in the proper forum, Canonical can fix them.

Perhaps you could clarify about 11.10: Ubuntu 11.10 64-bit? Burned to a CD? Error messages appear when? What type of installation? (WUBI, dual-boot, only Ubuntu?)

---

