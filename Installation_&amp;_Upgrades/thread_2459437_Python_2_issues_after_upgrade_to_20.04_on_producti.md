---
title: "Python 2 issues after upgrade to 20.04 on production server"
date: 2021-03-18
forum: Installation &amp; Upgrades
---

### Post by raydude on 2021-03-18
Our production scripts are currently in python 2. It is on my schedule to upgrade them to Python 3. I don't have the time to change the code at the moment, other pressing matters, but our production crew went ahead and upgraded the server to 20.04 and while everyone was crossing their fingers, we've hit our first snag.

Our production scripts use termcolor and python-termcolor doesn't exist in Focal. There is a Focal python3-termcolor and there is python-termcolor for older Ubuntus.

pip does not seem to exist even though python-pip-whl is installed.

Can someone guide me out of this mess?

Thanks in advance.

---

### Post by norobro on 2021-03-18
> **raydude said:**
> Our production scripts are currently in python 2. It is on my schedule to upgrade them to Python 3. I don't have the time to change the code at the moment, other pressing matters, but our production crew went ahead and upgraded the server to 20.04 and while everyone was crossing their fingers, we've hit our first snag.
FYI  [https://docs.python.org/3/library/2to3.html](https://docs.python.org/3/library/2to3.html)
> Our production scripts use termcolor and python-termcolor doesn't exist in Focal. There is a Focal python3-termcolor and there is python-termcolor for older Ubuntus.Don't use the termcolor package but it looks like python3-termcolor is the original code repackaged for python3. Look under "Download Source Package" here:  [https://packages.ubuntu.com/focal/python3-termcolor](https://packages.ubuntu.com/focal/python3-termcolor)

> pip does not seem to exist even though python-pip-whl is installed.It's pip3 in focal:```
$ which pip3
/usr/bin/pip3
```HTH

---

### Post by raydude on 2021-03-18
Thanks. But I don't have time to update the scripts. I need to get python 2 working. I need to install python-termcolor (for python 2) to get the scripts working. I need pip2, not pip3.

There are thousands of lines of python 2.6 code written by many people over the course of ten years and I can't risk running it through a conversion script in our production environment where downtime matters.

But I definitely will use that script  as a starting place for when I do the official update (outside of production) later this year. I really appreciate that. I had no idea it existed.

Is there a way to get termcolor working in python 2.7?

---

### Post by raydude on 2021-03-18
I downloaded the source and used ./setup.py install to install the package. Now I have to do the same with paramiko.

---

### Post by ubfan1 on 2021-03-19
You could roll back to 18.04, which has three more years of support, and convert to python3 at your leisure.

---

