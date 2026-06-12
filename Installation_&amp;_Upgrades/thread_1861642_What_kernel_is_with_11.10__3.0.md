---
title: "What kernel is with 11.10?  3.0?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by KeithLM on 2011-10-15
I did the upgrade from 11.04 today and I see that I have 2.6.38-11-generic as my kernel.  Isn't it supposed to be a 3.0 kernel?  I'm confused, did something not go right?

---

### Post by pbpersson on 2011-10-15
According to [this website]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#Linux_3.0_Kernel") it is supposed to be 3.0

---

### Post by drs305 on 2011-10-15
The current kernel is 3.0.0. 

You can see what you are currently running with "uname -r".

Check the contents of /boot to see if vmlinuz-3.0.0-... exists.

If it is there, try updating grub:
```
sudo update-grub
```

---

### Post by mbott on 2011-10-15
Mine appears to have upgraded just fine:

-Version-
Kernel		        : Linux 3.0.0-12-generic (x86_64)
Compiled		: #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011
C Library		: Unknown
Default C Compiler	: GNU C Compiler version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 
Distribution		: Ubuntu 11.10

---

### Post by KeithLM on 2011-10-15
When I run update-grub all I see is 2.6.38-11 and 2.6.38-8.  apt-get update and apt-get upgrade do nothing.  And my X config is hosed so I can't get to any of the gui based update tools.

---

