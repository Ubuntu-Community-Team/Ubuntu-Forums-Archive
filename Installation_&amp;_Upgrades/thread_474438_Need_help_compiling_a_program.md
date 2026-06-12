---
title: "Need help compiling a program"
date: 2007-06-15
forum: Installation &amp; Upgrades
---

### Post by vertigo1980 on 2007-06-15
Hi all,

i am trying to compile and install [divfix++](http://divfixpp.sourceforge.net/) on feisty. the site lists wxwidgets as a dependency, so i installed the 'headers' and -dev files for version 2.8. when i grab and extract the source, i notice there is no configure file so i just tried "make", and got:

```
`/home/compile/wxWidgets-2.8.3/wx-config --cxx` `/home/compile/wxWidgets-2.8.3/wx-config --cxxflags` -c -Os src/DivFix++App.cpp -o src/DivFix++App.o
/bin/sh: /home/compile/wxWidgets-2.8.3/wx-config: not found
/bin/sh: /home/compile/wxWidgets-2.8.3/wx-config: not found
/bin/sh: -c: not found
make: *** [src/DivFix++App.o] Error 127

```

i noticed it is looking for wx-config in /home for some reason, so i changed the part of the "makefile" so that instead of looking for wxconfig in "/home/whatever/it/was" to just "wx-config", then ran make again. i got this:

```
`wx-config --cxx` `wx-config --cxxflags` -c -Os src/DivFix++App.cpp -o src/DivFix++App.o
`wx-config --cxx` `wx-config --cxxflags` -c -Os src/DivFix++.cpp -o src/DivFix++.o
`wx-config --cxx` `wx-config --cxxflags` -c -Os src/DivFix++Core.cpp -o src/DivFix++Core.o
`wx-config --cxx` `wx-config --cxxflags` -c -Os src/DivFix++Gui.cpp -o src/DivFix++Gui.o
`wx-config --cxx` src/DivFix++App.o src/DivFix++.o src/DivFix++Core.o src/DivFix++Gui.o `wx-config --libs` -o DivFix++
msgfmt locale/tr/DivFix++.po -o locale/tr/DivFix++.mo
msgfmt locale/hu/DivFix++.po -o locale/hu/DivFix++.mo
```

that seemed to go without errors, so i did a sudo checkinstall, and got this:

```
cp DivFix++ /usr/local/bin
cp locale/tr/DivFix++.mo /usr/local/share/locale/tr/LC_MESSAGES/DivFix++.mo
cp: cannot create regular file `/usr/local/share/locale/tr/LC_MESSAGES/DivFix++.mo': No such file or directory
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

so i guess my question is, how on earth do i compile this program? am i even going about it the right way?

thanks! :)

---

### Post by vertigo1980 on 2007-06-15
anybody? :)

---

### Post by jfinkels on 2007-06-15
> **vertigo1980 said:**
> Hi all,

i am trying to compile and install [divfix++](http://divfixpp.sourceforge.net/) on feisty. the site lists wxwidgets as a dependency, so i installed the 'headers' and -dev files for version 2.8. when i grab and extract the source, i notice there is no configure file so i just tried "make", and got:

```
`/home/compile/wxWidgets-2.8.3/wx-config --cxx` `/home/compile/wxWidgets-2.8.3/wx-config --cxxflags` -c -Os src/DivFix++App.cpp -o src/DivFix++App.o
/bin/sh: /home/compile/wxWidgets-2.8.3/wx-config: not found
/bin/sh: /home/compile/wxWidgets-2.8.3/wx-config: not found
/bin/sh: -c: not found
make: *** [src/DivFix++App.o] Error 127

```

It looks your going to have to edit the makefile yourself. Change the line that has "/home/compile/wxWidgets-2.8.3/wx-config --cxx" so that it points to the actual wxWidgets-2.8 wxconfig file. I don't know where that file is, so check out the "Installed Files" tab in the "Properties" dialog for the wxwidgets package you installed in Synaptic.

---

### Post by vertigo1980 on 2007-06-17
thanks jfinkels, but i did change the directory to just "wx-config", as i said in my original post, and that error went away. :)

but it does not compile/install

---

### Post by IcarusR on 2007-06-17
Have you tried installing using Synaptic ???
Instructions here... [http://ralph.n3rds.net/index.php?/archives/191-Divfix++-AVI-repair-preview.html](http://ralph.n3rds.net/index.php?/archives/191-Divfix++-AVI-repair-preview.html)

---

### Post by vertigo1980 on 2007-06-17
the official repo's don't have it at all, and the link you mentioned provides a 3rd party repository, which only has the old version. i cannot find a deb package of the latest version, 0.29, so i am trying to compile it. :)

---

### Post by PaulFr on 2007-06-17
Perhaps the directory **/usr/local/share/locale/tr** or **/usr/local/share/locale/hu** is missing on your machine. I had installed gnome-sudoku before trying to compile DivFix++ and this created the directories. The makefile in DivFix++ just assumes these directories already exist, and fails if it does not - so maybe you should install gnome-sudoku first to create these directories :-)

---

### Post by PaulFr on 2007-06-17
Instead of installing gnome-sudoku :-) I guess you could 

[B]sudo mkdir -p /usr/local/share/locale/tr/LC_MESSAGES
sudo mkdir -p /usr/local/share/locale/hu/LC_MESSAGES[/B]

to create these two directories.

---

### Post by vertigo1980 on 2007-06-17
thanks paulfr, pretty odd since i think it should be able to do that itself (given sudo permissions), but that did it, it now compiles and runs ;)

the /hu directory was in the makefile too, so i created it as as well.

---

