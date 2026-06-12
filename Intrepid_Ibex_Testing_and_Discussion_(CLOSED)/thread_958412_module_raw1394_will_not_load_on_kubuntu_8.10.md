---
title: "module raw1394 will not load on kubuntu 8.10"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by odror on 2008-10-25
I have kubuntu 8.10 with the latest updates, running kernel 2.6.27-7.

when I type 
#  modprobe raw1394
FATAL: Module raw1394 not found.


But this module is not missing. It is located in 
/lib/modules/2.6.27-7-generic/kernel/drivers/ieee1394/raw1394.ko

Is this a bug?
Is there a workaround

-Thanks
Oz

---

### Post by cantormath on 2008-10-25
you use sudo when you typed this command?

---

### Post by odror on 2008-10-25
I run the command in a root account. sudo is not needed.
I get the same error when I add the sudo.

-Oz

---

