---
title: "cx8 cmov required for install"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by lw.white on 2010-12-30
Hi, I am trying to install Ubuntu Netbook 10.10 on a Via EPIA 800 c3 Mini Itx computer, with 638mb RAM and a 40 GB HDD. I could not get it to boot from a LiveCD, it hung at loading Bootlogo, so I have used Unetbootin. It now comes up with an error stating that:

This kernel requires the following features not present on your CPU
cx8 cmov
Unable to boot - please use a kernel appropriate to your CPU.

Can anyone help me with how to get around this?

---

### Post by DiGiTGOD on 2011-01-27
I've got the same problem... does anyone know of an iso that will work???

How far back do I have to go? 9.04? 8.04?

I thought that an i386 disc would work on machines without cmov? is this a bug??

---

### Post by Rex75 on 2011-03-02
After kernel 2.6.35 you need a cpu which supports the command CMOV (Conditional Move).
 
It seems, that Ubuntu 10.04 LTS hast a older kernel 2.6.32. I will try this Ubuntu Version and let's see.

---

### Post by Rex75 on 2011-03-03
With the older version I can start ubuntu, but the poor graphic onboard can't handle the desktop.
 
Btw. It's an Samuel 2 Via C3 (Eden) Prozessor, which has this problems.

---

### Post by lobstar on 2011-08-28
Hi

Got the same chip/machine and trying to blow some life into it.

Did you get anything to work with it ?

---

