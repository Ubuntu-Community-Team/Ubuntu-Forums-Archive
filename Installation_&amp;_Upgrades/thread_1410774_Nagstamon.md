---
title: "Nagstamon"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by cpickering on 2010-02-19
Hello,

I'm attempting to install Nagstamon (the website has no help) on Ubuntu 9.10..

I've installed 'python-eggtrayicon' to make it work, however, when I attempt to run nagstamon, I get the following error:

```

carl@sup08:~$ nagstamon 
Traceback (most recent call last):
  File "./nagstamon", line 76, in <module>
    nagstamonGUI.Settings(servers=servers, output=output, conf=conf)
  File "/usr/lib/nagstamon/nagstamonGUI.py", line 1588, in __init__
    self.FillTreeView()
  File "/usr/lib/nagstamon/nagstamonGUI.py", line 1666, in FillTreeView
    self.selected_server = server_list[0]
IndexError: list index out of range
carl@sup08:~$ 


```

---

### Post by cpickering on 2010-02-22
*bump*

---

### Post by Eidolon- on 2010-02-22
Have you tried installing nagstamon 0.9.2? That fixed my problem with the IndexError.

---

