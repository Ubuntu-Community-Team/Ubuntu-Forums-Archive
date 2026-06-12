---
title: "Can't remove gpar2"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by ivolution on 2006-09-04
Every time I want to use apt-get for a package I get 

```
E: The package gpar2 needs to be reinstalled, but I can't find an archive for it

```
I can't remove or reinstall this package. The package was a .deb package which I installed manually.[FONT="Arial"][/FONT]

---

### Post by FakeOutdoorsman on 2006-09-04
Try this in the terminal:

> sudo dpkg --remove --force-depends --force-remove-reinstreq gpar2

Referenced from [problems with synaptic package manager]("http://www.ubuntuforums.org/showpost.php?p=1362927&postcount=32").

---

### Post by ivolution on 2006-09-05
I've allready tried that. .. Didn't work.
What's next?

---

### Post by ivolution on 2006-09-05
> **FakeOutdoorsman said:**
> Try this in the terminal:



Referenced from [problems with synaptic package manager]("http://www.ubuntuforums.org/showpost.php?p=1362927&postcount=32").

when i run that command I get these errors:
```
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 86531 files and directories currently installed.)
Removing gpar2 ...
***
* Updating MIME database in /usr/share/mime...
Wrote 475 strings at 20 - 2764
Wrote aliases at 2764 - 2910
Wrote parents at 2910 - 32b0
Wrote literal globs at 32b0 - 330c
Wrote suffix globs at 330c - 65c4
Wrote full globs at 65c4 - 65e8
Wrote magic at 65e8 - bc34
Wrote namespace list at bc34 - bc44
***
/var/lib/dpkg/info/gpar2.postrm: line 25: update-desktop-database: command not found
dpkg: error processing gpar2 (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2

```

---

### Post by FakeOutdoorsman on 2006-09-05
Maybe this will work then:

```
/var/lib/dpkg/info$ sudo rm gpar2.*
```

Referenced from [Major broken package issue]("http://www.ubuntuforums.org/showthread.php?p=1223001").

---

### Post by ivolution on 2006-09-05
> **FakeOutdoorsman said:**
> Maybe this will work then:

```
/var/lib/dpkg/info$ sudo rm gpar2.*
```

Referenced from [Major broken package issue]("http://www.ubuntuforums.org/showthread.php?p=1223001").

Thanks I've tried that before but it didn't work either:

```
bash: /var/lib/dpkg/info$: No such file or directory

```

---

### Post by FakeOutdoorsman on 2006-09-05
What does it say when you try to reinstall it?

```
dpkg -i gpar2.deb
```

---

### Post by ivolution on 2006-09-06
> **FakeOutdoorsman said:**
> What does it say when you try to reinstall it?

```
dpkg -i gpar2.deb
```

```
dpkg: serious warning: files list file for package `gpar2' missing, assuming package has no files currently installed.
86532 files and directories currently installed.)
Preparing to replace gpar2 0.3-1 (using gpar2_0.3-1_i386.deb) ...
Unpacking replacement gpar2 ...
dpkg: dependency problems prevent configuration of gpar2:
 gpar2 depends on libpar2-0 (>= 0.2); however:
  Package libpar2-0 is not installed.
 gpar2 depends on libgtkmm-2.4-1c2 | libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2 is not installed.
  Package libgtkmm-2.4-1c2a is not installed.
 gpar2 depends on gnome-desktop-data; however:
  Package gnome-desktop-data is not installed.
dpkg: error processing gpar2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gpar2

```
I'm working with Kubuntu and don't have gnome installed. (I I don't want to work with gnome). The libgtkmm... I can't install because I can't install anything anymore.

---

### Post by ivolution on 2006-09-06
Never mind, after deleting /var/lib/dpkg/info/gpar2.postrm
I could apt-get remove it.

---

### Post by robert114 on 2006-11-02
have you been able to install gpar2 after all?
didn't work for me on my amd64

---

