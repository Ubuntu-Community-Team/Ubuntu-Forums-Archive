---
title: "Lucid Lynx Beta breaks Python installation:ImportError: No module named _md5"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by danjac on 2010-03-24
I've just upgraded to Lynx from Karmic. All working well except the default Python 2.6 install:

Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import hashlib
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.6/hashlib.py", line 136, in <module>
    md5 = __get_builtin_constructor('md5')
  File "/usr/lib/python2.6/hashlib.py", line 63, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5
>>>

---

### Post by danjac on 2010-03-25
On further analysis it appears that this only affects the Python executable under virtualenv, not the default Python, so should be fixable by reinstalling the virtualenv.

---

### Post by danjac on 2010-03-25
The solution (although not ideal) was to delete and rebuild the virtualenvs created under Karmic.

---

