---
title: "callgrind of package valgrind disappeared?"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by Antenne on 2012-10-31
The valgrind package is supposed to contain callgrind, a profiling tool:
```
$ apt-cache search callgrind
valgrind - memory debugger and profiler
```I installed and used this a long while ago. Today I wanted to run it as usual and got:
```
valgrind --tool callgrind [...]
valgrind: callgrind: command not found
```Since I already have callgrind.out files all over my test directories, I know that this once worked. Checking the package:
```
$ dpkg -L valgrind | grep bin
/usr/bin/valgrind
/usr/bin/vgdb
/usr/bin/cg_merge
/usr/bin/cg_annotate
/usr/bin/cg_diff
/usr/bin/callgrind_annotate
/usr/bin/callgrind_control
/usr/bin/ms_print
/usr/bin/valgrind-listener
/usr/bin/valgrind.bin
``````
$ dpkg -L valgrind | grep callgrind
/usr/bin/callgrind_annotate
/usr/bin/callgrind_control
/usr/lib/valgrind/callgrind-x86-linux
/usr/share/man/man1/callgrind_annotate.1.gz
/usr/share/man/man1/callgrind_control.1.gz
/usr/include/valgrind/callgrind.h
```Nope, nothing useful. I keep my system fairly recent, but don't check every single update. Some package upgrade might have removed it. I already removed/reinstalled the package. No help.

Does anyone have a clue what happened to callgrind?

Thanks!

---

