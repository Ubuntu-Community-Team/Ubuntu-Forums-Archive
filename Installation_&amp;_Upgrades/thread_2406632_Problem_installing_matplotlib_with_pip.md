---
title: "Problem installing matplotlib with pip"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by Biscarri on 2018-11-23
Hello,

I have installed 'pip'...

```
__$ sudo apt install python-pip
```

An then tried to install 'matplotlib'...

```
__$ pip install matplotlib
Collecting matplotlib
  Downloading https://files.pythonhosted.org/packages/89/0c/653aec68e9cfb775c4fbae8f71011206e5e7fe4d60fcf01ea1a9d3bc957f/matplotlib-3.0.2.tar.gz (36.5MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 36.5MB 43kB/s 
    Complete output from command python setup.py egg_info:
    
    Matplotlib 3.0+ does not support Python 2.x, 3.0, 3.1, 3.2, 3.3, or 3.4.
    Beginning with Matplotlib 3.0, Python 3.5 and above is required.
    
    This may be due to an out of date pip.
    
    Make sure you have pip >= 9.0.1.
    
    
    ----------------------------------------
Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-qpPJCy/matplotlib/
You are using pip version 8.1.1, however version 18.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.


```

After that I have tried to upgrade 'pip'...

```
__$ pip install --upgrade pip
Collecting pip
  Downloading https://files.pythonhosted.org/packages/c2/d7/90f34cb0d83a6c5631cf71dfe64cc1054598c843a92b400e55675cc2ac37/pip-18.1-py2.py3-none-any.whl (1.3MB)
    100% |&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;&#9608;| 1.3MB 770kB/s 
Installing collected packages: pip
Successfully installed pip-8.1.1
You are using pip version 8.1.1, however version 18.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.

```

But it seems it has not been upgraded. Then I have tried unsuccesfuly the following actions...

```
__$ pip install matplotlib
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

__$ matplotlib --version
matplotlib: no s'ha trobat l'ordre

__$ pip uninstall matplotlib
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

__$ pip --version
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

__$ pip install --upgrade pip
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

__$ sudo apt autoremove
[sudo] contrasenya per a biscarri: 
S'està llegint la llista de paquets… Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 185 no actualitzats.

__$ pip install --upgrade pip
Traceback (most recent call last):
  File "/usr/bin/pip", line 9, in <module>
    from pip import main
ImportError: cannot import name main

__$ 

```

Please, can somebody give me some advice on this issue?

Thanks,
Lluis

---

