---
title: "Clang and Clang++"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by mnouh on 2011-05-09
Wasn't sure who to address, clang or Ubuntu. I figured to address Ubuntu since it works on my other Operating Systems. Since 11.04 Natty, the current clang package that Ubuntu packaged is outdated.

There is C++ 4.5.2 and the current version cannot find the header files


End of search list. 
Hello.cpp:2:10: fatal error: '**iostream**' file not found 
#include <**iostream**> 
         ^ 
1 error generated. 

if you run clang++ -v filename.cpp it will show you where its trying to find the header files... and they dont exist on my machine since my machine only has 4.5 and 4.5.2 


This has nothing to do with system specs or configurations because I've tried it with different machines, and Ive installed the package the debian packaged version on my other machine and that works fine. It worked fine in 10.10.

---

### Post by yangcheng on 2011-06-23
I did a new installation of Ubuntu 11.04 and have the same problem. Clang and not found header files. 

I think there is clang community is aware of this issue an there is a patch:

[http://comments.gmane.org/gmane.comp.compilers.clang.devel/14609](http://comments.gmane.org/gmane.comp.compilers.clang.devel/14609)

but it's not in Ubuntu yet.

---

### Post by nonameentername on 2011-07-13
As a workaround you can fix this by creating a symbolic link:

```
sudo ln -s /usr/include/c++/4.5 /usr/include/c++/4.4
```This will allow clang to find the headers.

---

