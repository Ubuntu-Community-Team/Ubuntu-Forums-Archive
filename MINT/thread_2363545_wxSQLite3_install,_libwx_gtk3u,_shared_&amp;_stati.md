---
title: "wxSQLite3 install, libwx_gtk3u, shared &amp; static question."
date: 2017-06-11
forum: MINT
---

### Post by edward210 on 2017-06-11
I'm trying to install wxSQLite3 and have an issue not seen before.

Here is the make result:

```
stv@HpNotebook ~/Downloads/wxsqlite3-3.5.3 $ make
CC sqlite3/secure/src/sqlite3secure.lo
CXX src/wxsqlite3.lo
CXXLD libwxcode_gtk3u_wxsqlite3-3.0.la

*** Warning: Linking the shared library libwxcode_gtk3u_wxsqlite3-3.0.la against the
*** static library /usr/local/lib/libwx_gtk3u_core-3.0.a is not portable!

*** Warning: Linking the shared library libwxcode_gtk3u_wxsqlite3-3.0.la against the
*** static library /usr/local/lib/libwx_baseu-3.0.a is not portable!
ar: `u' modifier ignored since `D' is the default (see `U')
CXX samples/minimal.o
CXXLD samples/minimal
CXX samples/treeview/foldertree.o
CXX samples/treeview/projectlist.o
CXX samples/treeview/treeviewapp.o
CXX samples/treeview/treeviewsample.o
CXXLD samples/treeview/treeview
```

This was after using: ./configure --disable-shared.

Did Not Create a libwxcode_gtk3u-wxsqlite3-3.0.so.0 files without the --disable-shaed.

Not sure if I need to reload the Mint 18.1 OS + apps and start over or ?
I have another fully working linux PC, with no wxSQLite3 problems (using wxSQLite3 shared, no make warnings).

---

### Post by howefield on 2017-06-11
What's the underlying operating system ?

```
cat /etc/*-release
```

---

### Post by edward210 on 2017-06-11
Mint 18.1.
Sorry for the omission.

---

### Post by howefield on 2017-06-11
Ok, thread moved to the "*MINT*" forum where those who know the distribution can respond.

---

### Post by steeldriver on 2017-06-11
Sometimes it's helpful to 'make clean' to clear out any objects that might have been compiled without the --disable-shared flag

---

### Post by edward210 on 2017-06-11
Thanks steeldriver,
Same results after using make clean.

---

### Post by edward210 on 2017-06-12
I have succeeded in building a static library for wxSQLite3 now, and that is solved I think, even with the make errors, the 'libwxcode_gtk3u_wxsqlite3-3.0.a' file was created.

---

