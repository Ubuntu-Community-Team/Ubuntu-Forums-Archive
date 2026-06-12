---
title: "Lexmark X1240 Printer in Kubuntu"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-09-29
This printer has always worked fine for me in previous versions of Kubuntu when using the following walk through:
[http://ubuntuforums.org/showthread.php?t=49714](http://ubuntuforums.org/showthread.php?t=49714)

I recently reformatted and reinstalled my Kubuntu OS, and now this is no longer working for me. In the printer configuration section, I now get the following error message when trying to print a test page:

> Printer State: Idle - /usr/lib/cups/filter/rastertoz600 failed

Any idea what may have caused this? I went through those directions three times and still nothing has changed.

---

### Post by hansdown on 2008-09-29
Hi jlacroix.

I'm not an expert with these things, but I can give you some useful information...

Sorry, I got the wrong info.

---

### Post by jlacroix on 2008-09-29
Edit: Sorry for the misunderstanding.

Anyway, I just tested this printer out in Windows, and it works.

With Intrepid, I installed it the same way I always have, with the same instructions, that have always worked until now. I guess the problem has to be Intrepid.

---

### Post by henwyn on 2008-09-29
Lots of people having problems with printers stopping working on upgrades with an error about filters not being available.  One post I found elsewhere online blamed it on apparmor in the kernel locking them out for security reasons. Whatever the cause, what worked for me with my Samsung printer was deleting the printer and then reinstalling with the Samsung Linux installer. If Lexmark has no Linux installer, tryjust deleting it and reinstaling. HTH

---

### Post by jlacroix on 2008-09-29
> **henwyn said:**
> Lots of people having problems with printers stopping working on upgrades with an error about filters not being available.  One post I found elsewhere online blamed it on apparmor in the kernel locking them out for security reasons. Whatever the cause, what worked for me with my Samsung printer was deleting the printer and then reinstalling with the Samsung Linux installer. If Lexmark has no Linux installer, tryjust deleting it and reinstaling. HTH

Thanks. Lexmark is stupid and only includes a Linux driver for Red Hat which has to be converted using the instructions. I've deleted the printer and reinstalled it several times.

I also googled about the apparmor problem and followed the directions, but I still couldn't get it to go.

---

