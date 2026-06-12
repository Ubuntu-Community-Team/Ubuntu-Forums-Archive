---
title: "g++ installation in ubuntu"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by aliakbar82 on 2009-11-29
I want to install qt in ubuntu 9.04.I unzipped "qt-x11-opensource-src-4.3.5.tar.gz" file and did every thing in its instruction untill I reached the command make intall;i typed it but saw this error:
make[1]: g++: Command not found

make[1]: *** [.obj/release-shared/qapplication.o] Error 127

make[1]: Leaving directory `/home/moltani/tmp/qt-x11-opensource-src-4.3.5/src/gui'

make: *** [sub-gui-install_subtargets-ordered] Error 2
I think i shoud install g++. if yes how? and if no what I shoud do to solve this problem?

---

### Post by jsmnuk on 2010-02-11
> **aliakbar82 said:**
> I want to install qt in ubuntu 9.04.I unzipped "qt-x11-opensource-src-4.3.5.tar.gz" file and did every thing in its instruction untill I reached the command make intall;i typed it but saw this error:
make[1]: g++: Command not found

make[1]: *** [.obj/release-shared/qapplication.o] Error 127

make[1]: Leaving directory `/home/moltani/tmp/qt-x11-opensource-src-4.3.5/src/gui'

make: *** [sub-gui-install_subtargets-ordered] Error 2
I think i shoud install g++. if yes how? and if no what I shoud do to solve this problem?

I have the same problem, except my "command not found" is "MKDIR _P". Anybody home out there in Ubuntuland who can help?

---

### Post by lisati on 2010-02-11
Try this:
```
sudo apt-get install g++
sudo apt-get build-essential
```

---

