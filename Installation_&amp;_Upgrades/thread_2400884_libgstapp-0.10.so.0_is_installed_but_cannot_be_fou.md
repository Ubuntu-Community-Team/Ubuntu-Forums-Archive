---
title: "libgstapp-0.10.so.0 is installed but cannot be found by Antidote8"
date: 2018-09-11
forum: Installation &amp; Upgrades
---

### Post by alexandre12 on 2018-09-11
Hi, 

I have a fresh install of ubuntu 18.04, but an old Antidote8 that I want to install. I installed it once and it said my cd key couldn't be written down on the computer. So i figured I didn't installed it with proper permissions so I remove all antidote's file and reinstall with a chmod 755. Now after the install Antidote won't even start :
```
alex@Alexfregate:~$ Antidote
/opt/Druide/Antidote8/Programmes64/Antidote8.bin: error while loading shared libraries: libgstapp-0.10.so.0: cannot open shared object file: No such file or directory


```

But when I look in /usr/lib/x86_64-linux-gnu/  libgstapp-0.10.so.0 is there... 
I'm not familiar with symbolic linking, but I think it could solve the problem?

Thanks all for your help.

---

