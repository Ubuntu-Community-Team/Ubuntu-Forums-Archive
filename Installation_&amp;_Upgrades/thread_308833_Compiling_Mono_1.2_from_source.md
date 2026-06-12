---
title: "Compiling Mono 1.2 from source"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by auroraborealis on 2006-11-28
I'm trying to compile and install Mono 1.2 via instructions [here]("http://www.mail-archive.com/mono-list@lists.ximian.com/msg20859.html"). Everything is fine (libgdiplus/mono compile & installation), but when I run mcs it crashes (output attached). Does anyone have any ideas?

Edit: I'm using the current [stable sources](http://go-mono.com/sources-stable/)

```
$ mono --version
Mono JIT compiler version 1.2.1, (C) 2002-2006 Novell, Inc and Contributors. www.mono-project.com
        TLS:           __thread
        GC:            Included Boehm (with typed GC)
        SIGSEGV:       normal
        Disabled:      none
$ mcs >& crash.txt
Aborted (core dumped)

```

---

### Post by auroraborealis on 2006-11-28
Ok I guess the solution was easier than I thought.

```
$ sudo chmod -R a+r /usr/lib/mono/gac/*
```

---

