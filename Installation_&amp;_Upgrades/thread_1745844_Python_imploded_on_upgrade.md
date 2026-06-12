---
title: "Python imploded on upgrade"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Juppers on 2011-05-01
On upgrade I ran into this catch-22, and have almost 500 packages in limbo because of it. Any ideas on how to fix python-gobject or pycompile or whichever is angry?

Setting up python-gobject (2.28.3-1ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 322, in <module>
    main()
  File "/usr/bin/pycompile", line 299, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 217, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 180, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe
dpkg: error processing python-gobject (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of python-gtk2:
 python-gtk2 depends on python-gobject (>= 2.15.3); however:
  Package python-gobject is not configured yet.
 python-gtk2 depends on python2.6-gobject; however:
  Package python2.6-gobject is not installed.
  Package python-gobject which provides python2.6-gobject is not configured yet.
 python-gtk2 depends on python2.7-gobject; however:
  Package python2.7-gobject is not installed.
  Package python-gobject which provides python2.7-gobject is not configured yet.
dpkg: error processing python-gtk2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gmenu:
 python-gmenu depends on python-gtk2; however:
  Package python-gtk2 is not configured yet.
dpkg: error processing python-gmenu (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already

---

### Post by Juppers on 2011-05-06
Any ideas?

---

### Post by xavierzhao on 2011-06-15
hi, same problem.


Setting up python-apt (0.7.100.3ubuntu6.1) ...
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 322, in <module>
    main()
  File "/usr/bin/pycompile", line 299, in main
    options.force, options.optimize, e_patterns)
  File "/usr/bin/pycompile", line 217, in compile
    pipe.send(fn)
  File "/usr/bin/pycompile", line 180, in py_compile
    stdin.write(filename + '\n')
IOError: [Errno 32] Broken pipe

How to fix?

---

### Post by Juppers on 2011-06-15
Mine was caused by some old python that was hiding in usr/local. Do a locate on pycompile and you should find the bad stuff.

---

### Post by xavierzhao on 2011-06-16
> **Juppers said:**
> Mine was caused by some old python that was hiding in usr/local. Do a locate on pycompile and you should find the bad stuff.

OK, thank you, this problem has already solved, and I removed pycompile in /usr/bin.

---

