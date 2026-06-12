---
title: "How do I install python-gasp for Python 3?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by anthony62490 on 2010-05-08
Python 3.1.1 came out about a month ago, but now that I have upgraded, I can no longer import the GASP module

Test Program:

```
[COLOR="Red"]#!/usr/bin/python[/COLOR]
[COLOR="Orange"]from[/COLOR] gasp [COLOR="Orange"]import[/COLOR] *

begin_graphics()

Circle((200,200),60)
update_when([COLOR="Green"]"key_pressed"[/COLOR])
end_graphics()
```

And the Output:
```
anthony@anthony-desktop:~$ python Python/BYTE.py 
Traceback (most recent call last):
  File "Python/BYTE.py", line 2, in <module>
    from gasp import *
ImportError: No module named gasp

```

Importing GASP from Python 2.6 works just fine, but not with 3.1. How/where do I install/move the appropriate files so that I can use GASP?

---

### Post by anthony62490 on 2010-05-09
bump

---

### Post by anthony62490 on 2011-02-19
Necro-bump? The question is still relevant.

---

