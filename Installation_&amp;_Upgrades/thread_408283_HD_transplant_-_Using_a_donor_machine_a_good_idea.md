---
title: "HD transplant - Using a donor machine a good idea?"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Wielenga on 2007-04-13
I have machine that does not support USB boot, nor does it have a CD-ROM

Tried a hard drive install but (alternative CD) but keeps asking for cd rom. Cannot do a ln for some obscure reason. So what I did, ripped out the disk and installed xubuntu on a different machine. It seems to work but I wonder whether the kernel reflects the correct hardware config and the receiving machine runs in the most optimum way... 

The machines are considerably different; PIII > PII, ATI > Neomagic etc.

Is there a way to automatically rebuild the kernel if required.

---

### Post by DerHesse on 2007-04-13
$ uname -a

should reflect the kernel you are using.   -x86 or -generic should be ok.

---

