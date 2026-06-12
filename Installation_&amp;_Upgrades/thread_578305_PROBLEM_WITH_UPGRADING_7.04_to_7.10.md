---
title: "PROBLEM WITH UPGRADING 7.04 to 7.10"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by piSSta55 on 2007-10-17
**hi Guys i upgradet ubuntu 7.04 to 7.10 , I restart the system and i can not start any application in console i get this error:**
```

KABOOOM!!!

Whoops, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/ubuntu/+source/command-not-found
Please include the following information with the report:
/usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 10, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.5/site-packages/CommandNotFound/__init__.py", line 1, in <module>
    from CommandNotFound import CommandNotFound
  File "/usr/lib/python2.5/site-packages/CommandNotFound/CommandNotFound.py", line 7, in <module>
    import apt_pkg
ImportError: /usr/local/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
Python version: 2.5.1 final 0
```

Please can some one help me ?

---

### Post by cuby on 2007-10-17
can you call the programs manager and force an update?
did you try that?

---

### Post by piSSta55 on 2007-10-17
no the update manager ,also wont go ..

---

### Post by WarLud on 2007-11-24
I just upgraded and got this same problem does anyone have an answer????

---

### Post by mirceade on 2008-01-18
Someone suggested
ldd /usr/lib/libstdc++.so.6
sudo mv /usr/local/lib/libgcc_s.so.1 /usr/local/lib/libgcc_s.so.1.old

as seen here [http://ubuntuforums.org/showthread.php?t=270605](http://ubuntuforums.org/showthread.php?t=270605).
Not sure what it does, but it helped me once. After updating again the problem reoccurs and this time arround it does not go away.

---

