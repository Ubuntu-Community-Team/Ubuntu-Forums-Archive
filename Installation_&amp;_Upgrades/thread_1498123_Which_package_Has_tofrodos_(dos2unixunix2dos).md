---
title: "Which package Has tofrodos (dos2unix/unix2dos)"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by cmnorton on 2010-05-31
Which package contains tofrodos? I noticed build-essential is now loaded on a 10.04 install by default, but not tofrodos.

---

### Post by strydervtx on 2010-06-04
I had the same problem of finding dos2unix/unix2dos. tofrodos is its own package and the programs were renamed, for some unknown reason, to 'fromdos' and 'todos'.

---

### Post by gmargo on 2010-06-04
Search for it with "apt-cache":
```

$ apt-cache search tofrodos
tofrodos - Converts DOS <-> Unix text files, alias tofromdos

$ apt-cache show tofrodos
Package: tofrodos
[ ... snip ... ]
Description: Converts DOS <-> Unix text files, alias tofromdos
 DOS text files traditionally have CR/LF (carriage return/line feed) pairs
 as their new line delimiters while Unix text files traditionally have
 LFs (line feeds) to terminate each line.
 .
 Tofrodos comprises one program, "fromdos" alias "todos", which converts
 text files to and from these formats. Use "fromdos" to convert DOS
 text files to the Unix format, and "todos" to convert Unix text files
 to the DOS format.
[ ... snip ... ]

```

---

### Post by JeffDavidoff on 2011-01-06
I found this URL [http://www.virtualhelp.me/linux/164-dos2unix-missing-ubuntu-1004](http://www.virtualhelp.me/linux/164-dos2unix-missing-ubuntu-1004) a very helpful explanation on how to install and use dos2unix recent Ubuntu versions.

---

