---
title: "boot linux from boot.ini"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by swaraj_de on 2010-11-04
i have two xp sp2 in C: and E: 
and 
ihave installed ubantu & it's  boot loader on F:
now i'm unable to boot my desktop in ubuntu
so WHAT CHANGE CAN BE DONE IN XP BOOT LOADER TO GET ALL THREE OS BOOT OPTIONS BEFORE BOOT????
my boot loader is below

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

thanks in advance:confused:

---

### Post by oldfred on 2010-11-04
Did you install wubi? It should have set it up for you.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Something like this boot.ini entry, may be f: in your case:
c:\wubildr.mbr="Ubuntu-Linux"

---

