---
title: "error while loading shared libraries"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by teja483 on 2011-06-22
hi all.

i have a platform independent  compiler. so, i created the common api's and platform api's using my complier. so i have this library files named cmn_api.a & platform_api.a in my auto/linjtag/lib.(they will be created when we run the makefile of the compiler).

the problem is when i'm trying to run the console application of my compiler. i have a menu.c from which i choose different modes and i operated on that.when i tried to open one of the executable i'm getting this error

testuser@testuser-desktop:~/infra/tools/genie/B_linjtag_dbg$ ./genie 
./genie: error while loading shared libraries: ../../../../infra/framework/lin/B_linjtag_dbg/cmn_api.so: cannot open shared object file: No such file or directory
:)

thanks in advance.

---

