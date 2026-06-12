---
title: "HELP: installing flyback"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by adityakavoor on 2007-11-07
I followed instructions here

[http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

when i run ./flyback.py I get the foll error
```

Traceback (most recent call last):
  File "./flyback.py", line 813, in <module>
    main_gui()
  File "./flyback.py", line 738, in __init__
    self.show_prefs_dialog()
AttributeError: main_gui instance has no attribute 'show_prefs_dialog'
aditya@ubuntu:~/flyback$ ./flyback.py 
Traceback (most recent call last):
  File "./flyback.py", line 813, in <module>
    main_gui()
  File "./flyback.py", line 738, in __init__
    self.show_prefs_dialog()
AttributeError: main_gui instance has no attribute 'show_prefs_dialog'

```

any idea ?

---

### Post by arvindkst on 2007-11-07
Quick fix

Open flyback.py and comment the following lines

        if not client.get_string("/apps/flyback/external_storage_location"):
            self.show_prefs_dialog()

---

