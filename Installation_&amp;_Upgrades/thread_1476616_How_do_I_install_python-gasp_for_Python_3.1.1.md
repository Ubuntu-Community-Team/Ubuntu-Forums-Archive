---
title: "How do I install python-gasp for Python 3.1.1?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by anthony62490 on 2010-05-08
Python 3.1 came out about a month ago, but now that I have upgraded, I can no longer import the GASP module

output:
```
anthony@anthony-desktop:~$ python Python/BYTE.py 
Traceback (most recent call last):
  File "Python/BYTE.py", line 2, in <module>
    from gasp import *
ImportError: No module named gasp

```

Importing GASP from Python 2.6 works just fine, but not with 3.1. How/where do I install/move the appropriate files so that I can use GASP?

---

### Post by sir_nasty on 2010-05-08
Please don't take this the wrong way but if you open BYTE.py what does line 2 say? Where is it looking?

---

### Post by anthony62490 on 2010-05-08
The test program is as follows:

```
#!/usr/bin/python
from gasp import *

begin_graphics()

Circle((200,200),60)
update_when("key_pressed")
end_graphics()
```

---

### Post by anthony62490 on 2010-05-08
bump

---

