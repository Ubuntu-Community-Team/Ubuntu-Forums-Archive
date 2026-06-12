---
title: "gdesklet stopped working"
date: 2009-07-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-07-05
Was trouble shooting wifi but had some hard lock ups requiring me to do a hard shut down.  did that a few times and now gdesklets is not working.  running gdesklets in a terminal creates the following:

> buzzmandt@buzzmandt-laptop:~$ gdesklets
Starting gdesklets-daemon...
Connecting to daemon [ ###         ]
==========================================================[07/05/09-17:17:43]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]db type could not be determined
in /usr/lib/gdesklets/gdesklets-daemon: line 10 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/main/Starter.py: line 2 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/DaemonConfigger.py: line 1 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/StateSaver.py: line 128 <module>
in /usr/lib/gdesklets/config/StateSaver.py: line 30 __init__
in /usr/lib/gdesklets/config/Backend.py: line 68 Backend
in /usr/lib/python2.6/shelve.py: line 234 open
in /usr/lib/python2.6/shelve.py: line 218 __init__
in /usr/lib/python2.6/anydbm.py: line 80 open
[EXC]/usr/lib/python2.6/anydbm.py

[---]   75             mod = _defaultmod
[---]   76         else:
[---]   77             raise error, "need 'c' or 'n' flag to open new db"
[---]   78     elif result == "":
[---]   79         # db type cannot be determined
[ERR]>  80         raise error, "db type could not be determined"
[---]   81     else:
[---]   82         mod = __import__(result)
[---]   83     return mod.open(file, flag, mode)


Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.


I had a look at the log file but its LOOOOOOONGGGGGG.  If asked to post it will post it here.  

any ideas?

---

### Post by wayne_cat on 2009-07-05
gdesklets starts without a problem on my system. Create a bug report ;)

---

### Post by buzzmandt on 2009-07-05
not so sure if it's a bug or if something happened to it during the lockups/forced shut downs trying to deal with the wifi not working.  

Maybe I should purge it then reinstall....I'll give that one a shot.

EDIT:  that didn't work either.

---

### Post by wayne_cat on 2009-07-05
You could try to remove gdesklet with --purge ... to delete the old config settings .. and reinstall it.

edit: ok ... you have tried that ... did not work :(

---

### Post by buzzmandt on 2009-07-05
Okay, got it working.  The old getting rid of/renaming ~/.gdesklets so it sees a brand new install.  renamed to ~/.gdesklets2 and everything works now.

---

