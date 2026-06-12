---
title: "Problems running an old project"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by hFit on 2010-05-15
hi....i'm not sure whether this is the right place to post, but i absolutely need help here...

i'm trying to install the protocol informatics package....i think i have installed its dependencies (sorry, i'm new to ubuntu):
Python >= 2.3.4     [http://www.python.org](http://www.python.org)
Numerical Python    [http://www.stsci.edu/resources/software_hardware/numarray](http://www.stsci.edu/resources/software_hardware/numarray)
Pyrex               [http://www.cosc.canterbury.ac.nz/~greg/python/Pyrex/](http://www.cosc.canterbury.ac.nz/~greg/python/Pyrex/)
Pcapy               [http://oss.coresecurity.com/projects/pcapy.html](http://oss.coresecurity.com/projects/pcapy.html)
Pydot               [http://dkbza.org/pydot.html](http://dkbza.org/pydot.html)

except that i'm using python 2.5 on ubuntu 8......

when i run the project, i get this error:
Traceback (most recent call last):
  File "main.py", line 11, in ?
    from PI import *
  File "/home/test/Desktop/PI/PI/distance.py", line 17, in ?
    import align
ImportError: /home/test/Desktop/PI/PI/align.so: invalid ELF header

am i missing something here?
would really appreciate any help....thks!

---

