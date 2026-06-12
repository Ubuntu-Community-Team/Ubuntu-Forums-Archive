---
title: "[SOLVED] No internet in custom compiled kernel"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by mthakur2006 on 2007-09-20
Hi,
I recently custom compiled a kernel, two kernels infact, one with thek ck1 patchset and another one with cfs. Both the cases, I had no internet (wireless) and dmesg showed that it was unable to load module ipw2200 because of error 2.
any help?
thanks.

---

### Post by ddrichardson on 2007-09-21
Did you make modules as well?

---

### Post by mthakur2006 on 2007-09-21
> **ddrichardson said:**
> Did you make modules as well?

how do you do that?
sorry...noob ere!

---

### Post by ddrichardson on 2007-09-21
Well when you compiled your kernel, anything you selected to be a module would not be built unless you do:```
make modules
```
If you prefer them to be in one large monolithic kernel then you need to select the drivers to be built in the kernel.

---

### Post by mthakur2006 on 2007-09-22
> **ddrichardson said:**
> Well when you compiled your kernel, anything you selected to be a module would not be built unless you do:```
make modules
```
If you prefer them to be in one large monolithic kernel then you need to select the drivers to be built in the kernel.

tried it...no joy!

---

### Post by ddrichardson on 2007-09-22
You can also do ```
make modules_install
```

---

### Post by mthakur2006 on 2007-09-22
hi, that didn't work, but i found something that does.
in /lib/firmware, i copied the firmware from my older kernel and renamed it to the result of uname -r and viola!
it works!
but i don't notice a speed difference with the cfs tho!

---

### Post by ddrichardson on 2007-09-22
Yeah that'll do it. Didn't know you had specific firmware. What is cfs?

---

### Post by mthakur2006 on 2007-09-22
cfs is completely fair scheduler. it is supposed to dramatically improve performance. here are the links:

[http://ubuntuforums.org/showthread.php?t=538068&highlight=cfs](http://ubuntuforums.org/showthread.php?t=538068&highlight=cfs)

:guitar:

---

