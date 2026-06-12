---
title: "What's with python?"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Doctor Drive on 2009-11-17
System: Ubuntu 9.10
Architecture: i386

When i'm trying to launch any adesklet it gives me something like that
[php]
doctor@Doctor:~/.desklets/CircleMeter$ python circlemeter.py --nautilus
Do you want to (r)egister this desklet or to (t)est it? t
Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "circlemeter.py", line 2, in <module>
    from adesklets.commands import *
  File "/usr/local/lib/python2.6/dist-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets interpreter initialization error - xwininfo: error: No such window with id 0x180001e.

Exception AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0x8e46d4c>> ignored
[/php]

The problem with that wierd so called **AttributeError 'NoneType'** also had appeared while trying to use **Vodafone Mobile Connect** in some python script.

----------------------------
Any ideas what's the problem?

---

### Post by Doctor Drive on 2009-11-18
up

---

