---
title: "linux-686-smp"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by IrIT on 2005-02-24
Hi :D
I'm about to upgrade my kernel. Right now i'm running with the standard 386. In synaptic i read, that 686 is for Pentium 4. Now, i've a P4 with Hyper Threading. Is the smp kernel then the correct kernel?
Also, i've asked around. And somebody said, that it proberly was the correct kernel. But that i have to add something to my grub. He said that i should add:
apic=ht no acpi

So, is this correct. And if it is, where in my grub should i then add it?

Thanks in advanve!  :D

---

### Post by tim1 on 2005-02-24
linux-686-smp is right for Pentium 4, at least I'm  running it on mine  :D 

I don't think you need to change anything else than the kernel, I didn't either. If you want to try it without risking anything, leave your old Kernel entry intact and just add the new one. If the new one doesn't work, just boot the old one and begin troubleshooting.

greets, tim

---

### Post by IrIT on 2005-02-25
Ok! :D

But is it also the correct one for Hyper Therading?

---

### Post by WW on 2005-02-25
Yes. See, for example, this article: [http://www-128.ibm.com/developerworks/linux/library/l-htl/](http://www-128.ibm.com/developerworks/linux/library/l-htl/)

---

### Post by IrIT on 2005-02-25
Thanks a lot guys! :D

I'll try it as soon as i come home.

apic=ht no acpi <-- Then i don't need to add this?

---

### Post by IrIT on 2005-02-25
IN the site WW linked to, they said that they used acpismp=force for HT. But they testet it on a Xeon processer. And i've a P4. So is the acpismp=force to correct option?

---

### Post by Leif on 2005-02-25
I have a p4 too, and linux-686-smp works fine without any extra options.

---

