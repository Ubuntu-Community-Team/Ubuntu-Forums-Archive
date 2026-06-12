---
title: "Messed up system by installing Kernel for Intrepid"
date: 2008-09-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lachild on 2008-09-20
Hello,

While tring to get my Card reader working I installed in the Linux Kernel for the up and comming Intrepid.  While this got my card reader working, it did unfortunatly mess up my Graphics card (Nvidia) and even after installing the driver for Nvidia was still unable to get Compitz working again.

What I need to know is two things,  One if I upgrade the system using Alpha 6 and keep my system updated, will I have a complete stable version of Intrepid by the time it launches?

Also, if I decide not to update the system, how can I now revert back to the older Hardy kernel.  Right now if I remove linux-headers it reinstalled the Intrepid Kernel even after telling Synaptic to only use updates for Hardy. :(

Thanks in advance for the help
LaChild

---

### Post by retrow on 2008-09-20
If you still have your older kernel image, you can specify your bootloader to use that one instead of the Ibex's kernel. If you had been keeping up with kernel upgrades for Hardy, you should have 2.6.24.19-generic kernel in /boot folder. Presently your default might be 2.6.27.3 (latest Ibex kernel). If so, just modify your /boot/grub/menu.lst such that the default booting is with the Hardy 2.6.24.19 kernel.

---

