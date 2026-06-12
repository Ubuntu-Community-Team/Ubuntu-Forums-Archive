---
title: "remove windows + leave ubuntu"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by robteh on 2010-08-22
Currently, both windows vista and Ubuntu 10.04lts are installed in my Dell studio 1737 laptop. On startup i'm prompted to choose one of the two OS(s). However, i now want to completely do away with vista. How do i do it with the least inconvenience?

---

### Post by Rubi1200 on 2010-08-22
Did you install Ubuntu to the hard-drive or via Wubi?

Do you have, or can you get, an Ubuntu CD?

---

### Post by 73ckn797 on 2010-08-22
As asked already, if you installed Ubuntu through Windows you will have to do a complete fresh install. If you do have a Ubuntu CD you can accomplish what you want without removing Ubuntu but only if Windows and Ubuntu are on separate partitions. You can delete the Windows partition using gparted which is on the Ubuntu disk. There will be more steps needed but we will need to know the current installation status.

---

### Post by cj.surrusco on 2010-08-22
> **73ckn797 said:**
> As asked already, if you installed Ubuntu through Windows you will have to do a complete fresh install.

Not necessarily.  You could use [LVPM]("http://lubi.sourceforge.net/lvpm.html") to export the Wubi install to a separate partition.

---

