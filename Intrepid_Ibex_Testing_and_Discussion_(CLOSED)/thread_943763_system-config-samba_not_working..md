---
title: "system-config-samba not working."
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TremerePuck on 2008-10-10
This is what I get when I run it:

Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 44, in <module>
    import mainWindow
  File "/usr/share/system-config-samba/mainWindow.py", line 23, in <module>
    import sambaBackend
  File "/usr/share/system-config-samba/sambaBackend.py", line 30, in <module>
    from rhpl.translate import _, N_
ImportError: No module named rhpl.translate

---

### Post by plun on 2008-10-10
Confirmed bug
[https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/280872](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/280872)

---

