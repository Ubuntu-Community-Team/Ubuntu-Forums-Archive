---
title: "How Can I Tell if I am running Ubuntu 32-bit or 64-bit?"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by NCMS on 2011-08-20
I am running **Windows 7 32-bit** on my laptop [COLOR=black]**HP ProBook 6550b**[/COLOR] and installed in dual boot mode **ubuntu 10.04.3** 


***cat /etc/issue***
ubuntu 10.04.3 LTS

***uname -a***
Linux ncms-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux

***uname -r***
2.6.32-33-generic

***uname -m***
i686

***sudo lscpu***
Architecture: 
i686
CPU op-mode(s): 32-bit, 64-bit


**[COLOR=red]How can I tell if Ubuntu is 32-bit or 64-bit  form the output listed above?[/COLOR]**

---

### Post by howefield on 2011-08-20
> **NCMS said:**
> 
***uname -a***
Linux ncms-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux


***uname -m***
i686




32 bit.

---

### Post by NCMS on 2011-08-20
[color=purple]***thank you***[/color]

---

