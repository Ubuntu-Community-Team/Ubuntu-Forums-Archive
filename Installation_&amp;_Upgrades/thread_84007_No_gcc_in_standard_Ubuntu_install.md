---
title: "No gcc in standard Ubuntu install"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by CrowBoy1960 on 2005-10-30
Hi all,

I have just installed Ubuntu as I'm getting kinda pissed off with Windoze, but I want to use a program called AmiBroker (plus a few others)  which apparently runs under wine on Linux. I tried to install wine but ran into a minor problem when I found out gcc wasn't installed :( . I started to download it using the Package manager then I figured it must be on the CD somewhere. I figured given that gcc isn't there there would be many other nifyt development tools missing (eg make/gmake etc). Can someone tell me if there are development tools on the CD and how to install them (I have broadband but only 1GB a month download limit which I am chewing through :).

Thanks in advance,

Martin.

PS another completely un-related question, anyone had any luck getting a Lexmark X1170 printer working under Linux??

---

### Post by Xian on 2005-10-30
[QUOTE=CrowBoy1960]I want to use a program called AmiBroker (plus a few others)  which apparently runs under wine on Linux. I tried to install wine but ran into a minor problem when I found out gcc wasn't installed :( . [/QUOTE]
You have gcc. Check what version you are using.

```
$ gcc --version
gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
```

---

