---
title: "Opera on Ubuntu 7.04"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by kirtimaan on 2007-04-26
Hello,

Today I installed Ubuntu 7.04 and after installing necessary plugins and software, I installed Opera webbrowser (I have 9.10)

First time it complaint about missing dependency libqt3 and which I installed. After that Opera installation was successful. However, now when I try to launch it, it simply don't run. I tried to launch it via terminal to see the problem and found following message :

kirtimaan@myhost:/$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault (core dumped)


Is it due to any compatibility issue or missing library ?

Please guide.

Thanks, Kirtimaan

---

### Post by zPacKRat on 2007-04-26
uninstall 9.10 and download 9.20 from the opera web site and all should be good. durring beta older versions were broken, however this has been fixed in the latest version of Opera.

---

