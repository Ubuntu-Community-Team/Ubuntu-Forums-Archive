---
title: "tried ghdl tutorial and got &quot;cannot find -lgnat-3.4&quot;"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2006-04-01
Installed ghdl, tried the simple 'Hello Word' tutorial example from   [http://ghdl.free.fr/ghdl/index.html](http://ghdl.free.fr/ghdl/index.html) and got

```
ghdl -a hello.vhdl
ghdl -e hello_world
/usr/bin/ld: cannot find -lgnat-3.4
collect2: ld returned 1 exit status
```

libgnat is installed, the file is under /usr/lib/libgnat-3.4.so.1 .

Has somebody an idea on what is going wrong here ?

---

### Post by wfjm on 2006-04-01
Important Note I forgot:

I tried the same under Debian Sarge, installed ghdl+gnat.
No problems, all works fine !

A "ghdl  -e -v hello_world" shows

```

$ ghdl  -e -v hello_world
...
 -L/usr/lib/gcc/i486-linux/3.4.4/adalib/ -lgnat-3.4

```

Under Ubuntu the ADA run time system is installed under

   /usr/lib/gcc/i486-linux-gnu/3.4.5/adalib/

while under Debian

   /usr/lib/gcc/i486-linux/3.4.4/adalib/

Finally a hack like

  # mkdir -p /usr/lib/gcc/i486-linux/3.4.4/
  # ln -s /usr/lib/gcc/i486-linux-gnu/3.4.5/adalib adalib

made it work.

The ghdl package should be fixed, though.

---

