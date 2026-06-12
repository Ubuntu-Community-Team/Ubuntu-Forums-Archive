---
title: "[SOLVED] installing qt (designer, linguist, assistant)"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by chaichy on 2008-01-28
hello community,
after i got used to ubuntu more and more I recently decided to change from windows to ubuntu completely. So I'm trying to install Qt but it doesn't work. I tried it 3 times now so i want to ask the community whether someone could help. Because I have problems installing qt with simple "make" and "make install" i tried >> sudo apt-get libqt4-dev which worked. But it didn't install the designer, linguist and assistent and i would like to have them, too. But compiling from the source doesn't work because make throws me an error 
```
/usr/bin/ld: cannot find -lQtScript
collect2: ld returned 1 exit status
make[2]: *** [../../../../lib/libQtDesigner.so.4.3.3] Error 1
make[2]: Leaving directory `/tmp/qt-x11-opensource-src-4.3.3/tools/designer/src/lib'
make[1]: *** [sub-lib-make_default-ordered] Error 2
make[1]: Leaving directory `/tmp/qt-x11-opensource-src-4.3.3/tools/designer/src'
make: *** [sub-src-make_default] Error 2

```
so i thought perhaps a installation through the packet manager. Although searching "qt" brought me some hits it was the designer etc. for qt 3. But I'd like to get the one for qt4. So I ask if someone has a solution for me.
Thank you in advance for your help
chaichy

--------
[edit:]
solved the problem myself. wrote a bit to fast x) 
apt-get install qt4-dev-tools an qt4-designer 
was the solution

---

