---
title: "Software Updates + Linux img 2.6.32.27 + hesitation 2 update = require clarification"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by astrobob.tk on 2010-12-20
Hello fellow Ubuntuers,

Just today I was checking for software upgrades using the upgrade manager & I got the following updates:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7187[/IMG]

Upon checking the linux image description, here is what It read:

[IMG]http://ubuntuforums.org/picture.php?albumid=1552&pictureid=7186[/IMG]

It states: 

> Geared towards 32-bit desktop systems with over 4GB RAM
You likely do not want to install this package directly, instead, install the linux-generic-pae-meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.


Up to my knowledge, I installed a 64-bit Ubuntu on a core 2 duo dell studio xps with exactly 4GB RAM. this is the first time I check the description of a linux image & the first time that I face such description; so i hesitated to update the system.

Moreover, "uname -a" gives:

> Linux ********* 2.6.32-26-generic-pae #48-Ubuntu SMP Wed Nov 24 10:31:20 UTC 2010 i686 GNU/Linux


I hope for some clarification & explanation in regard of what going on here please.

thank you

---

### Post by bowens44 on 2010-12-20
It looks like you installed 32 bit not 64.

uname -a should give you something like this if you installed 64 bit:

Linux net23-admin 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

---

### Post by astrobob.tk on 2010-12-21
> **bowens44 said:**
> It looks like you installed 32 bit not 64.

uname -a should give you something like this if you installed 64 bit:

Linux net23-admin 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

How do I know if the hardware supports 64 bit ?

SO basically, I should do the update ?

---

### Post by dino99 on 2010-12-21
> **astrobob.tk said:**
> How do I know if the hardware supports 64 bit ?

SO basically, I should do the update ?

yes you should, your choice is the good one: pae kernel is a 32 bits that fully use ram like 64 bits does, but with less issues :)

---

