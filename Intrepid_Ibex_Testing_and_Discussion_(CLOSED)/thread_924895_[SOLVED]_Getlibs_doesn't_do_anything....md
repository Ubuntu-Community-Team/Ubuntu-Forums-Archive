---
title: "[SOLVED] Getlibs doesn't do anything..."
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by doorknob60 on 2008-09-20
Well, Getlibs used to work for Sype, etc, but now after a recent ia32-libs update, it doesn't seem to do anything. Some apps work (Flash, Firefox 32 bit), but some don't (Skype). Getlibs normally fixes the problems, but it doesn't seem to this time. It worked fine before the update...and also Getlibs doesn't seem to give any errors, although it seems like it's downloading pretty fast, could that be it?

EDIT: I think this explains my problem pretty well :-P
```
austin@austin:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open sharedobject file: No such file or directory
austin@austin:~$ sudo getlibs /usr/bin/skype
[sudo] password for austin:
libQtDBus.so.4: libqt4-core
libQtGui.so.4: libqt4-gui
libQtNetwork.so.4: libqt4-core
libQtCore.so.4: libqt4-core
The following i386 packages will be installed:
libqt4-core
libqt4-gui
Continue [Y/n]? y
Downloading ...
Installing libraries ...
austin@austin:~$ skype
skype: error while loading shared libraries: libQtDBus.so.4: cannot open sharedobject file: No such file or directory
austin@austin:~$

```

---

### Post by psyke83 on 2008-09-20
> **doorknob60 said:**
> Well, Getlibs used to work for Sype, etc, but now after a recent ia32-libs update, it doesn't seem to do anything. Some apps work (Flash, Firefox 32 bit), but some don't (Skype). Getlibs normally fixes the problems, but it doesn't seem to this time. It worked fine before the update...and also Getlibs doesn't seem to give any errors, although it seems like it's downloading pretty fast, could that be it?


The ia32-libs package was updated to accommodate the new Flash release, so GetLibs won't be necessary. As for Skype, make sure that library was installed:

```
$ sudo updatedb
$ locate libQtDBus.so.4
```

It could also be a symlink issue:
```
$ locate libQtDBus.so
```

---

### Post by doorknob60 on 2008-09-20
```
austin@austin:~$ sudo updatedb
[sudo] password for austin:
austin@austin:~$ locate libQtDBus.so.4
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.4
/usr/lib/libQtDBus.so.4.4.1
austin@austin:~$ locate libQtDBus.so
/usr/lib/libQtDBus.so
/usr/lib/libQtDBus.so.4
/usr/lib/libQtDBus.so.4.4
/usr/lib/libQtDBus.so.4.4.1
austin@austin:~$

```

Yeah they're all in regular /usr/lib instead of /usr/lib32, so Getlibs isn't doing its job right...and yeah I know Flash works, but programs with extra dependencies besides the libs in ia32-libs simply don't work...

---

### Post by taur on 2008-09-20
I managed to get skype running by manually copying
the required files from the following packages:

[http://packages.ubuntu.com/intrepid/i386/libqtgui4](http://packages.ubuntu.com/intrepid/i386/libqtgui4)
[http://packages.ubuntu.com/intrepid/i386/libqt4-dbus](http://packages.ubuntu.com/intrepid/i386/libqt4-dbus)
[http://packages.ubuntu.com/intrepid/i386/libqt4-network](http://packages.ubuntu.com/intrepid/i386/libqt4-network)
[http://packages.ubuntu.com/intrepid/i386/libqtcore4](http://packages.ubuntu.com/intrepid/i386/libqtcore4)
[http://packages.ubuntu.com/intrepid/i386/libqt4-xml](http://packages.ubuntu.com/intrepid/i386/libqt4-xml)

using the info in this post here:
[http://ubuntuforums.org/showthread.php?p=475023](http://ubuntuforums.org/showthread.php?p=475023)

Skype now works, but getlibs does indeed not seem to be doing anything.

---

### Post by doorknob60 on 2008-09-27
Fixed it, packages like libqt4-gui in intrepid are just dummy packages, which don't really do anything. Manually istalling the real packages with sudo getlibs -p libqtgui4 (for example) is working. :) Tricky...

---

### Post by taur on 2008-09-28
Confirmed, that also fixes the:
"Fatal: Cannot mix incompatible Qt libraries"
discussed in this thread:
[http://forum.skype.com/lofiversion/index.php/t95626.html](http://forum.skype.com/lofiversion/index.php/t95626.html)
... wich showed up recently with my 'fix'.

---

