---
title: "how to compile modified .cc &amp; .h files in ns2?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by adilodha on 2010-04-01
hello,
i am using ubuntu 9.10. i have installed ns-allinone-2.34.
installation is successful.

now whenever i make changes in .h and .cc files of ns2, i need to compile them.
i tried with g++ filename.cc.
it shows a lot of errors that the header files which are included in the files are not available. the files are there but g++ is unable to locate their locations.

then i read somewhere that i have to use 'makefile' command to compile the files.
but it's giving me error that "bash: /usr/ns-allinone-2.34/tcl8.4.18/unix/Makefile: Permission denied" when i typed "Makefile" only.

also i am not getting the x11r6 folder at "/usr/" location but path is set for that like "/usr/x11r6/lib" and there is no folder like that.

i also read somewhere on net that this may be because of the higher version of gcc/g++.

i am doing a project in wifi handover and i need answers of above queries as early as possible.
hope i get these solved soon.

thank you.

---

