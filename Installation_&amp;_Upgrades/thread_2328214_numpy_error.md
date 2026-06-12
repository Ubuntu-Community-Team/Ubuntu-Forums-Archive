---
title: "numpy error"
date: 2016-06-18
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2016-06-18
Dear Fellows

   I have installed python 2.7.5 through these these commands:
```

sudo apt-get install build-essential checkinstall
sudo apt-get install libreadline-gplv2-dev libncursesw5-dev libssl-dev libsqlite3-dev tk-dev libgdbm-dev libc6-dev libbz2-dev
cd ~/Downloads/
wget http://python.org/ftp/python/2.7.5/Python-2.7.5.tgz
tar -xvf Python-2.7.5.tgz
./configure
make
sudo checkinstallcd Python-2.7.5

```
then I tried to run a python file, I face this error:

```

Traceback (most recent call last):
  File "verifyChargeBump.py", line 3, in <module>
    import numpy as np  # NumPy (multidimensional arrays, linear algebra, ...)
ImportError: No module named numpy

```

Can some body please hint me how can I fix this?

   Regards

---

### Post by babakflame on 2016-06-18
I found this valuable link:


  [http://askubuntu.com/questions/359254/how-to-install-numpy-and-scipy-for-python](http://askubuntu.com/questions/359254/how-to-install-numpy-and-scipy-for-python)

---

### Post by Topsiho on 2016-06-19
You should install numpy first, before you can use it, as it is not installed by default.
You can install it using synaptic (easiest way, because you need not know the exact name of the package), or use sudo apt-get install <package name>

As there are 2 versions of python, python and python3, you should install the numpy that you need:

python-numpy and/or
python3-numpy

Python will be replaced by python3 completely, some day, so if you do not really need to use python, you better put your energy and effort in python3. I guess ...

Topsiho

---

