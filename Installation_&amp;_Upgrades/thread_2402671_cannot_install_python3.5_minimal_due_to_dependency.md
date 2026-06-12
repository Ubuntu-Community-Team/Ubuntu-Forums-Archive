---
title: "cannot install python3.5 minimal due to dependency problems"
date: 2018-10-03
forum: Installation &amp; Upgrades
---

### Post by tonverkleij on 2018-10-03
Hello,

I have a Ubuntu 16.04 system and I was trying to install glances using sudo apt-get install samba, however this failed.  It seems that python3 is not properly working. 

I get all sorts of errors and with installing and running sudo apt-get upgrade:

```
root@MDB01:/var/cache/apt/archives# apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
samba is already the newest version (2:4.3.11+dfsg-0ubuntu0.16.04.16).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
127 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up python3.5-minimal (3.5.2-2ubuntu0~16.04.4) ...
# Empty sitecustomize.py to avoid a dangling symlink
Could not find platform independent libraries <prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
Fatal Python error: Py_Initialize: Unable to get the locale encoding
ImportError: No module named 'encodings'


Current thread 0x00007f7f2148e700 (most recent call first):
Aborted
dpkg: error processing package python3.5-minimal (--configure):
 subprocess installed post-installation script returned error exit status 134
Setting up python-extras (0.0.3-3) ...
/var/lib/dpkg/info/python-extras.postinst: 6: /var/lib/dpkg/info/python-extras.postinst: pycompile: not found
dpkg: error processing package python-extras (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up python-semantic-version (2.3.1-1) ...
/var/lib/dpkg/info/python-semantic-version.postinst: 6: /var/lib/dpkg/info/python-semantic-version.postinst: pycompile: not found
dpkg: error processing package python-semantic-version (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of python3-minimal:
 python3-minimal depends on python3.5-minimal (>= 3.5.1-2~); however:
  Package python3.5-minimal is not configured yet.


dpkg: error processing package python3-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3.5:
 python3.5 depends on python3.5-minimal (= 3.5.2-2ubuntu0~16.04.4); however:
  Package python3.5-minimal is not configured yet.
```

How can I completely eradicate the failing python3.5 package including dependencies and everything related and perform a solid clean reinstall of Python3.5?

---

### Post by tonverkleij on 2018-10-03
Oh, I forgot to mention, there is also Python3.6 installed on this system, in total there is pyton2.7, Python3.6 and Python3.6 installed on this system.  How to fix this disorder?

---

### Post by monkeybrain20122 on 2018-10-07
> **tonverkleij said:**
> Oh, I forgot to mention, there is also Python3.6 installed on this system, in total there is pyton2.7, Python3.6 and Python3.6 installed on this system.  How to fix this disorder?

How did you install python-3.6? The python3 version for 16.04 is 3.5.

In general don't mess with the default python since some components of the system may have version specific python dependency. If you want a different version of python either use a contained environment like anaconda or compile python from source and install it locally in your $HOME and set the proper environmental variables when use. Specifically don't use the two ppas advertised in some blogs since they really mess up the dependencies.

---

