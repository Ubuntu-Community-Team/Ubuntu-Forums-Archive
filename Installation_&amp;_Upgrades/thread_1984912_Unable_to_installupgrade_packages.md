---
title: "Unable to install/upgrade packages"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by jackal_79 on 2012-05-22
Hi All,
     Iam unable to upgrade existing packages.Everytime i try this i get Package Operation Failed with details as below.Please advice:
===================================================================
```
installArchives() failed: perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/locale: 1: Syntax error: word unexpected (expecting ")")
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/locale: 1: Syntax error: word unexpected (expecting ")")
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LANG = "en_IN.ISO8859-1"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
/usr/bin/locale: 1: Syntax error: word unexpected (expecting ")")
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 241042 files and directories currently installed.)
Preparing to replace python-aptdaemon-gtk 0.43+bzr697-0ubuntu1 (using .../python-aptdaemon-gtk_0.43+bzr697-0ubuntu1.2_all.deb) ...
Unpacking replacement python-aptdaemon-gtk ...
Preparing to replace python-aptdaemon.gtk3widgets 0.43+bzr697-0ubuntu1 (using .../python-aptdaemon.gtk3widgets_0.43+bzr697-0ubuntu1.2_all.deb) ...
Unpacking replacement python-aptdaemon.gtk3widgets ...
Preparing to replace python-aptdaemon.gtkwidgets 0.43+bzr697-0ubuntu1 (using .../python-aptdaemon.gtkwidgets_0.43+bzr697-0ubuntu1.2_all.deb) ...
Unpacking replacement python-aptdaemon.gtkwidgets ...
Preparing to replace aptdaemon 0.43+bzr697-0ubuntu1 (using .../aptdaemon_0.43+bzr697-0ubuntu1.2_all.deb) ...
Unpacking replacement aptdaemon ...
Preparing to replace python-aptdaemon 0.43+bzr697-0ubuntu1 (using .../python-aptdaemon_0.43+bzr697-0ubuntu1.2_all.deb) ...
Unpacking replacement python-aptdaemon ...
Processing triggers for man-db ...
/usr/bin/locale: 1: Syntax error: word unexpected (expecting ")")
Setting up gconf2 (3.2.3-0ubuntu0.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 120, in <module>
    trim(os.path.join(defaults_dest,"%%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 14, in get_valid_languages
    cmd = subprocess.Popen(['locale', '-a'], stdout=subprocess.PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 8] Exec format error
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-aptdaemon (0.43+bzr697-0ubuntu1.2) ...
Setting up python-aptdaemon.gtkwidgets (0.43+bzr697-0ubuntu1.2) ...
Setting up python-aptdaemon.gtk3widgets (0.43+bzr697-0ubuntu1.2) ...
Setting up python-aptdaemon-gtk (0.43+bzr697-0ubuntu1.2) ...
Setting up aptdaemon (0.43+bzr697-0ubuntu1.2) ...
dpkg: dependency problems prevent configuration of ubuntu-tweak:
 ubuntu-tweak depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntu-tweak (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 gconf2
 ubuntu-tweak
Error in function: 
Setting up gconf2 (3.2.3-0ubuntu0.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 120, in <module>
    trim(os.path.join(defaults_dest,"%%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 14, in get_valid_languages
    cmd = subprocess.Popen(['locale', '-a'], stdout=subprocess.PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 8] Exec format error
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-tweak:
 ubuntu-tweak depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntu-tweak (--configure):
 dependency problems - leaving unconfigured
```
=================================================================

---

### Post by zvacet on 2012-05-23
```
sudo dpkg --configure -a
```

---

### Post by jackal_79 on 2012-05-23
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

I got following output from above command.What does it mean?
==================================

Setting up gconf2 (3.2.3-0ubuntu0.1) ...
Traceback (most recent call last):
  File "/usr/sbin/gconf-schemas", line 120, in <module>
    trim(os.path.join(defaults_dest,"%gconf-tree.xml"), get_valid_languages())
  File "/usr/sbin/gconf-schemas", line 14, in get_valid_languages
    cmd = subprocess.Popen(['locale', '-a'], stdout=subprocess.PIPE)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1239, in _execute_child
    raise child_exception
OSError: [Errno 8] Exec format error
dpkg: error processing gconf2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-tweak:
 ubuntu-tweak depends on gconf2 (>= 2.28.1-2); however:
  Package gconf2 is not configured yet.
dpkg: error processing ubuntu-tweak (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
 ubuntu-tweak
jackal@jackal-XFX-nForce-650i-Ultra:~$ 
===================================================

---

### Post by jadtech on 2012-05-23
since it seems there is dependency issues you  should try this 

```
 sudo apt-get upgrade -f

``` 

this should build  a dependancy list down load what is need and install ..

---

### Post by zvacet on 2012-05-23
```
sudo dpkg --configure gconf2
```

---

### Post by jackal_79 on 2012-05-29
> **zvacet said:**
> ```
sudo dpkg --configure gconf2
```

On running above command i got this"

sudo dpkg --configure gconf2
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on libxml2 (>= 2.7.4); however:
  Package libxml2 is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gconf2
jackal@jackal-XFX-nForce-650i-Ultra:~$ 

Please suggest

---

### Post by shafi.dude99 on 2012-05-29
try running this code :

sudo locale-gen

sudo apt-get clean all

sudo apt-get update

---

