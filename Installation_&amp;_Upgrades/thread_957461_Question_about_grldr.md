---
title: "Question about grldr"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by gavntery on 2008-10-24
I copy the file "grldr" to "C:", and add a new entry to the Vista BCD to boot from grldr. Like this:
......              {7af0a663-a1ed-11dd-8af9-001d92db8114}
device                  partition=C:
path                    \grldr
description             Ubuntu 8.10
The question is when I reboot my computer, it didn't boot from Vista's bootmgr.It boot from grldr directly without my operation. I hope the computer boot from bootmgr to display the boot menu. In the boot menu, I can choose the "Ubuntu 8.10" boot entry. And it start the grldr to boot the Linux.
I have two harddisk:a 320GB SATA and a 80GB IDE. Vista installed to C: in the 320GB SATA one, and Ubuntu 8.10 installed in the 80GB IDE one. The "/boot" in 80GB IDE one is a single logical disk.

---

### Post by gavntery on 2008-10-24
PLease!!!

---

### Post by caljohnsmith on 2008-10-24
Have you tried [EasyBCD]("http://neosmart.net/dl.php?id=1")? I think that might help you.

---

### Post by gavntery on 2008-10-24
Yes! It worked perfectly on my old computer. My Old computer has two IDE hard disk. But now EasyBCD is no use.

---

