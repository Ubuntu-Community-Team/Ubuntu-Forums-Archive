---
title: "Guake Install"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by u-foka on 2007-09-26
Hy!

I try to use guake (quake style terminal for gnome)
[http://guake-gnome-vte.sourceforge.net/](http://guake-gnome-vte.sourceforge.net/)

I installed it, and everything looks fine, but when i start guake, it's tol me, the guake.schemas gconf schema isn't installed...  then i did it, but it still won't work :S

Anyone can use that app?
Or any ideas?

---

### Post by gabrielteratos on 2007-10-02
After install guake, just execute:

gconftool-2 --install-schema-file /usr/etc/gconf/schemas/guake.schemas

This will be fixed in next version

---

### Post by coldstatue on 2007-10-06
What do you type after 

```

svn co http://svn.guake-terminal.org/guake guake
```

?

I get the following, and then a prompt

```
A    guake/trunk
A    guake/trunk/m4
A    guake/trunk/m4/intltool.m4
A    guake/trunk/m4/acinclude.m4
A    guake/trunk/configure.ac
A    guake/trunk/AUTHORS
A    guake/trunk/TODO
A    guake/trunk/INSTALL
A    guake/trunk/po-extract
A    guake/trunk/ChangeLog
A    guake/trunk/src
A    guake/trunk/src/common.py
A    guake/trunk/src/guake.in
A    guake/trunk/src/guake.py
A    guake/trunk/src/statusicon.py
A    guake/trunk/src/globalhotkeys
A    guake/trunk/src/globalhotkeys/eggaccelerators.h
A    guake/trunk/src/globalhotkeys/example.py
A    guake/trunk/src/globalhotkeys/keybinder.h
A    guake/trunk/src/globalhotkeys/globalhotkeys.c
A    guake/trunk/src/globalhotkeys/Makefile.am
A    guake/trunk/src/globalhotkeys/eggaccelerators.c
A    guake/trunk/src/globalhotkeys/testbinding.c
A    guake/trunk/src/globalhotkeys/keybinder.c
A    guake/trunk/src/Makefile.am
A    guake/trunk/src/guake_globals.py.in
A    guake/trunk/src/dbusiface.py
A    guake/trunk/src/simplegladeapp.py
A    guake/trunk/COPYING
A    guake/trunk/Makefile.am
A    guake/trunk/data
A    guake/trunk/data/pixmaps
A    guake/trunk/data/pixmaps/guake.png
A    guake/trunk/data/pixmaps/right_normal.svg
A    guake/trunk/data/pixmaps/littleguakelogo.svg
A    guake/trunk/data/pixmaps/guake.svg
A    guake/trunk/data/pixmaps/up_normal.svg
A    guake/trunk/data/pixmaps/down_in.svg
A    guake/trunk/data/pixmaps/tabdown.svg
A    guake/trunk/data/pixmaps/left_normal.svg
A    guake/trunk/data/pixmaps/right_in.svg
A    guake/trunk/data/pixmaps/add_tab.png
A    guake/trunk/data/pixmaps/close.svg
A    guake/trunk/data/pixmaps/statusicon_out.png
A    guake/trunk/data/pixmaps/up_in.svg
A    guake/trunk/data/pixmaps/new_guakelogo.png
A    guake/trunk/data/pixmaps/Makefile.am
A    guake/trunk/data/pixmaps/tabup.svg
A    guake/trunk/data/pixmaps/statusicon_over.png
A    guake/trunk/data/pixmaps/guakelogo.svg
A    guake/trunk/data/pixmaps/add_tab.svg
A    guake/trunk/data/pixmaps/down_normal.svg
A    guake/trunk/data/pixmaps/littleguakelogo.png
A    guake/trunk/data/pixmaps/left_in.svg
A    guake/trunk/data/about.glade
A    guake/trunk/data/guake.glade
A    guake/trunk/data/Makefile.am
A    guake/trunk/data/guake.desktop.in
A    guake/trunk/data/org.gnome.Guake.service.in
A    guake/trunk/data/prefs.glade
A    guake/trunk/data/guake.schemas
A    guake/trunk/autogen.sh
A    guake/trunk/NEWS
A    guake/trunk/README
A    guake/trunk/po
A    guake/trunk/po/pt_BR.po
A    guake/trunk/po/ChangeLog
A    guake/trunk/po/POTFILES.in
A    guake/branches
A    guake/branches/before-refactoring
A    guake/branches/before-refactoring/guake.png
A    guake/branches/before-refactoring/common.py
A    guake/branches/before-refactoring/guake.py
A    guake/branches/before-refactoring/utils.py
A    guake/branches/before-refactoring/guakeApplet.py
A    guake/branches/before-refactoring/daemon.py
A    guake/branches/before-refactoring/README
A    guake/branches/before-refactoring/buttons
A    guake/branches/before-refactoring/buttons/left_normal.svg
A    guake/branches/before-refactoring/buttons/right_in.svg
A    guake/branches/before-refactoring/buttons/.noPIL.png
A    guake/branches/before-refactoring/buttons/right_normal.svg
A    guake/branches/before-refactoring/buttons/statusicon_out.png
A    guake/branches/before-refactoring/buttons/up_in.svg
A    guake/branches/before-refactoring/buttons/statusicon_over.png
A    guake/branches/before-refactoring/buttons/up_normal.svg
A    guake/branches/before-refactoring/buttons/down_in.svg
A    guake/branches/before-refactoring/buttons/down_normal.svg
A    guake/branches/before-refactoring/buttons/left_in.svg
A    guake/branches/before-refactoring/locale
A    guake/branches/before-refactoring/locale/pt_BR
A    guake/branches/before-refactoring/locale/pt_BR/LC_MESSAGES
A    guake/branches/before-refactoring/locale/pt_BR/LC_MESSAGES/guake.mo
A    guake/branches/before-refactoring/DEVEL
A    guake/branches/before-refactoring/DEVEL/gettext.txt
A    guake/branches/before-refactoring/DEVEL/TODO
A    guake/branches/before-refactoring/poExtract.py
A    guake/branches/before-refactoring/close.svg
A    guake/branches/before-refactoring/Dialogs.py
A    guake/branches/before-refactoring/main.py
A    guake/branches/before-refactoring/guakelogo.svg
A    guake/branches/before-refactoring/glade
A    guake/branches/before-refactoring/glade/guake.png
A    guake/branches/before-refactoring/glade/new_guakelogo.svg
A    guake/branches/before-refactoring/glade/about.glade
A    guake/branches/before-refactoring/glade/prefs.glade
A    guake/branches/before-refactoring/glade/guake.svg
A    guake/branches/before-refactoring/glade/tabdown.svg
A    guake/branches/before-refactoring/glade/flux.jpg
A    guake/branches/before-refactoring/glade/imgs
A    guake/branches/before-refactoring/glade/imgs/tabup.svg
A    guake/branches/before-refactoring/glade/imgs/tabdown.svg
A    guake/branches/before-refactoring/glade/close.svg
A    guake/branches/before-refactoring/glade/oldprefs.glade.bkp
A    guake/branches/before-refactoring/glade/statusicon_out.png
A    guake/branches/before-refactoring/glade/guakeabt.png
A    guake/branches/before-refactoring/glade/guake.glade
A    guake/branches/before-refactoring/glade/new_guakelogo.png
A    guake/branches/before-refactoring/glade/tabup.svg
A    guake/branches/before-refactoring/glade/guakelogo.svg
A    guake/branches/before-refactoring/glade/addTerm.svg
A    guake/branches/before-refactoring/addTerm.svg
A    guake/tags
Checked out revision 1.

```

I have the ~/guake directory, and I know I need to run ./configure, but I can't figure out which directory to run it in. It seems I've tried all subs under /guake. 
I keep getting
```
bash: ./configure: No such file or directory
```

---

### Post by u-foka on 2007-10-07
You should use autogen.sh :)

---

### Post by coldstatue on 2007-10-07
Ah, thank you. works great!

---

