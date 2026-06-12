---
title: "Eric IDE will not launch"
date: 2009-05-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fifth on 2009-05-25
Launching the Eric Python IDE gives the following traceback;

```

Traceback (most recent call last):
  File "/usr/share/eric/modules/eric4.py", line 43, in <module>
    from KdeQt.KQApplication import KQApplication
  File "/usr/share/eric/modules/KdeQt/__init__.py", line 20, in <module>
    import Preferences
  File "/usr/share/eric/modules/Preferences/__init__.py", line 26, in <module>
    from PyQt4 import 
ImportError: cannot import name Qsci

```

Seems to be a problem with python-qscintilla. I've re-installed Eric and all Scintilla related packages but same result.

---

### Post by conorw on 2009-05-25
um hi, sorry. I can't help you because I'm a total noob and need help myself. I just wanted to ask how you make a thread because I can't find a place where it says "start new thread" or anything like that.

---

### Post by fifth on 2009-05-25
> **conorw said:**
> um hi, sorry. I can't help you because I'm a total noob and need help myself. I just wanted to ask how you make a thread because I can't find a place where it says "start new thread" or anything like that.

Welcome to the Ubuntu Forums Conor. Theres a button at the top and bottom of each page marked 'New Thread'.

[IMG]http://ubuntuforums.org/picture.php?albumid=1130&pictureid=4029[/IMG]

The 'New Thread' button is available when viewing any of the forums.

When viewing a thread, you'll get a 'New Reply' button in roughly the same place.

---

### Post by fifth on 2009-05-27
I've been doing more tests and find I cannot import Qsci from PyQt4.

```

>>> from PyQt4 import Qsci
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: cannot import name Qsci

```

But still trying to resolve :( Only difference between python-scintilla2 and the rest of the PyQt files is PyQt itself installs to;

/usr/lib/pyshared/python2.6/PyQt4
and
/usr/lib/pyshared/python2.5/PyQt4

where as python-scintilla installs to;

/usr/lib/python2.6/dist-packages/PyQt4

but i dont't think this is relevant as linking to the 2.6 folder throws the same error .

---

### Post by _Purple_ on 2009-05-27
May be it is a bug. Have you seen this?
[https://bugs.launchpad.net/ubuntu/+source/eric/+bug/380701](https://bugs.launchpad.net/ubuntu/+source/eric/+bug/380701)

---

### Post by fifth on 2009-05-27
> **_Purple_ said:**
> May be it is a bug. Have you seen this?
[https://bugs.launchpad.net/ubuntu/+source/eric/+bug/380701](https://bugs.launchpad.net/ubuntu/+source/eric/+bug/380701)

Thanks, I was just trying to report the problem and came across the same. I've added a comment but so far its listed as 'Undecided', hopefully someone will look at it soon as its a deal breaker for some developers and end users on Karmic.

---

### Post by fifth on 2009-06-04
After updates today (python-qscintilla2), eric now displays the splash screen followed by;

```
Warning: translation file 'qt_en_GB'could not be loaded.
Using default.
Warning: translation file 'eric4_en_GB'could not be loaded.
Using default.
Warning: translation file 'qscintilla_en_GB'could not be loaded.
Using default.
Segmentation fault

```

---

