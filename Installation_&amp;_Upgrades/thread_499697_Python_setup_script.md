---
title: "Python setup script"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by PietreWitobi on 2007-07-12
So I've downloaded this source written in python.  Unfortunately - I have no experience with Python.  Not to be beaten, I tried several things.  I started by running. ```
python setup.py
``` then ```
python2.5 setup.py
``` then ```
py_compilefiles setup.py
```

The last was the only one to complete, and I got the same error message for both of the others...> Traceback (most recent call last):
  File "setup.py", line 5, in <module>
    import psyco
ImportError: No module named psyco

Then I ran the same two commands with setup.pyc, and got the same error messages.

I downloaded and installed many python addendums hoping one would have the psyco module.

Can anyone help me?  Am I even going about this the right way?  I'm lost in a very dark forest here.

---

### Post by moephan on 2007-07-12
Did you search synaptic for "psyco"? I'm not 100% certain, but I am guessing you need to install the "python-psyco" package.

HTH

Cheers, Rick

---

