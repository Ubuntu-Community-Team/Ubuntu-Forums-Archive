---
title: "ttk module not found"
date: 2015-11-29
forum: Installation &amp; Upgrades
---

### Post by Peter_Knapen on 2015-11-29
I have installed python3, python3-tk. In this case I thoufht ttk would be supported, but when I include following lines in the python script:
 import tkinter as tk
 from tkinter import *
 from ttk import *
I get the error: ImportError: No module named 'ttk'

What is goiing wrong?

---

### Post by steeldriver on 2015-11-29
Hello and welcome to the forums

What version of Ubuntu? How did you install python3?

All current version of Ubuntu ship with python3 by default, I think - including the ttk module as part of the standard library

---

### Post by Peter_Knapen on 2015-11-29
Thanks for the quick response. I am using ubuntu 14.04 LTS and installed the packages using the synaptic package manager

---

### Post by Peter_Knapen on 2015-11-29
I have attached a file as result of the command find . | grep python3.4 > ~/python3_4.txt and zipped it

---

### Post by steeldriver on 2015-11-29
It looks like the commands you are using are appropriate for python2.x, whereas for python3.x it should be

```

from tkinter import *
from tkinter.ttk import *

```

See [https://docs.python.org/3/library/tkinter.ttk.html](https://docs.python.org/3/library/tkinter.ttk.html)

---

### Post by Peter_Knapen on 2015-11-30
Thanks,
ttk is working now. I got the lines from an external example.

---

