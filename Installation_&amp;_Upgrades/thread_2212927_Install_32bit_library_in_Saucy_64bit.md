---
title: "Install 32bit library in Saucy 64bit??"
date: 2014-03-23
forum: Installation &amp; Upgrades
---

### Post by amigabill2 on 2014-03-23
I'm having problems using Eagle PCB version 5.12 in 64bit saucy. It seems to be a problem of libpng12-0. 

eagle
eagle: error while loading shared libraries: libpng12.so.0: cannot open shared object file: No such file or directory



As the ia32lib stuff is gone, how do I get this satisfied? I do have the 64bit version of this library, but that doesnt' seem usable by Eagle. As there is not an apt package for Eagle 5, dependencies are not automatically satisfied. 

ls /usr/lib/x86_64-linux-gnu/libpng*

/usr/lib/x86_64-linux-gnu/libpng*
/usr/lib/x86_64-linux-gnu/libpng12.a     /usr/lib/x86_64-linux-gnu/libpng.a
/usr/lib/x86_64-linux-gnu/libpng12.so    /usr/lib/x86_64-linux-gnu/libpng.so
/usr/lib/x86_64-linux-gnu/libpng12.so.0



I am able to use Eagle 6.5, having installed the apt package for eagle 6.4 to get dependencies, then removed the 6.4 version. 

But there are times I want/need to use 5.x still, and so need this 32bit library somehow.

---

### Post by oldos2er on 2014-03-23
Try ```
sudo apt-get install libpng12-0:i386
```

---

### Post by kostkon on 2014-03-23
```
sudo apt-get install libpng12-0:i386
```
More about multiarch, [here]("https://help.ubuntu.com/community/MultiArch").

EDIT: oldos2er was faster :P

---

