---
title: "Insight debugger installation issue"
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by silvercats on 2012-12-03
Lubuntu 12.10. 
I tried to install insight debugger ([www.sourceware.org/insight/](www.sourceware.org/insight/))


In its readme,it says to type "./configure" . it is ok. after that it is telling to type "make install" . After a while I got this error


```
checking for nm... nm
checking for ranlib... ranlib
checking for strip... strip
checking for windres... no
checking for windmc... no
checking for objcopy... objcopy
checking for objdump... objdump
checking for cc... cc
checking for c++... c++
checking for gcc... gcc
checking for gcj... no
checking for gfortran... no
checking for ar... ar
checking for as... as
checking for dlltool... no
checking for ld... ld
checking for lipo... no
checking for nm... nm
checking for objdump... objdump
checking for ranlib... ranlib
checking for strip... strip
checking for windres... no
checking for windmc... no
checking where to find the target ar... host tool
checking where to find the target as... host tool
checking where to find the target cc... host tool
checking where to find the target c++... host tool
checking where to find the target c++ for libstdc++... host tool
checking where to find the target dlltool... host tool
checking where to find the target gcc... host tool
checking where to find the target gcj... host tool
checking where to find the target gfortran... host tool
checking where to find the target ld... host tool
checking where to find the target lipo... host tool
checking where to find the target nm... host tool
checking where to find the target objdump... host tool
checking where to find the target ranlib... host tool
checking where to find the target strip... host tool
checking where to find the target windres... host tool
checking where to find the target windmc... host tool
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether -fkeep-inline-functions is supported... yes
configure: creating ./config.status
config.status: creating Makefile
cat@cat-virtual-machine:~/Desktop/insight-6.8-1$ make install
make[1]: Entering directory `/home/cat/Desktop/insight-6.8-1'
/bin/bash ./mkinstalldirs /usr/local /usr/local
make[2]: Entering directory `/home/cat/Desktop/insight-6.8-1/bfd'
make[2]: *** No rule to make target `install'.  Stop.
make[2]: Leaving directory `/home/cat/Desktop/insight-6.8-1/bfd'
make[1]: *** [install-bfd] Error 2
make[1]: Leaving directory `/home/cat/Desktop/insight-6.8-1'
make: *** [install] Error 2
cat@cat-virtual-machine:~/Desktop/insight-6.8-1$ 

```

help. Also I am using VMware workstation on Windows Host to run Lubuntu. In the start menu's "Programming" section , it shows "insight debugger" but nothing happens when I click. nothing, not even an error message shows up

---

### Post by dino99 on 2012-12-03
an easy way:

[HTML]http://www.baptiste-wicht.com/2012/01/install-insight-debugger-linux-mint-ubuntu/
[/HTML]
or from ubuntu repo:

[HTML]http://packages.ubuntu.com/search?keywords=insight[/HTML]

---

