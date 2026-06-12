---
title: "Synaptic/Grub using incorrect default values"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by DerPflanz on 2007-04-29
Hi,

I have some small problems concerning upgrading kernels:

1. After installing the kernel and updating Grub (as Synaptic seems to do as well), my /boot/grub/menu.lst is incorrect. For some strange reason, the file says 'root   (hd1,0)' for every entry, while (hd0,0) is the correct value. My device.map shows the values correctly:

(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc

2. Also (although this is not a very big issue) I would like to have 'quiet nosplash' added by default to all my Linux boot options. 

How can I fix these issues?

TIA
Bart Friederichs

---

### Post by lw5 on 2007-04-29
Just backup and adjust you /boot/grub/menu.lst? Or am I misunderstanding your question?

---

### Post by DerPflanz on 2007-05-01
You understand the question correctly, and the proposed solution works, but I often forget it. And that causes my bootmenu to be incorrect, and I have to manually change that. It should just work.

---

### Post by lw5 on 2007-05-01
Ah, now I understand. In menu.lst there is a line like this:

# groot=(hd1,0)

I think changing that to the correct disk should get rid of your problems when updating to a new kernel.

---

