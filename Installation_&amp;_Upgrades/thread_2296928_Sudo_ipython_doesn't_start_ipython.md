---
title: "Sudo ipython doesn't start ipython"
date: 2015-09-29
forum: Installation &amp; Upgrades
---

### Post by rj7 on 2015-09-29
Hi,
I have ubuntu 14.04. I am starting to use ipython now and i am facing an odd issue. When i start ipython normally it works. If i do the same with sudo it doesn't work.
F```


raja@raja-XPS-ubuntu:~$ sudo ipython
sudo: ipython: command not found
raja@raja-XPS-ubuntu:~$ ipython
Python 2.7.10 |Anaconda 2.3.0 (64-bit)| (default, May 28 2015, 17:02:03) 
Type "copyright", "credits" or "license" for more information.

IPython 3.2.0 -- An enhanced Interactive Python.
Anaconda is brought to you by Continuum Analytics.
Please check out: http://continuum.io/thanks and https://anaconda.org
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object', use 'object??' for extra details.

In [1]: 
Do you really want to exit ([y]/n)? y
raja@raja-XPS-ubuntu:~$ sudo ipython
sudo: ipython: command not found
raja@raja-XPS-ubuntu:~$ 



```

Can someone please help me understand why this happens?


Raja

---

### Post by ian-weisser on 2015-09-29
How, exactly, did you install ipython?

Please show us the complete output of the command:
```
which ipython
```

---

