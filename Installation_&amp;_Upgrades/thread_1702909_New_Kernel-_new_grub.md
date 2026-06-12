---
title: "New Kernel- new grub?"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Jonker on 2011-03-08
Hi there,
I have Ubuntu 10.10 installed on a ext. HD. It works fine. Then I update yesterday to the Kernel 2.6.35.28. I had configured the Grub that it is on the ext. HD. But after updating, the Grub bootloader was on the MBR on the internal HD? Could this have been caused by the new kernel?

---

### Post by Jonker on 2011-03-10
is the question so difficult that nobody knows the answer, or is it so stupid that you don't want to give an answer?

---

### Post by Hedgehog1 on 2011-03-10
> **Jonker said:**
> Hi there,
I have Ubuntu 10.10 installed on a ext. HD. It works fine. Then I update yesterday to the Kernel 2.6.35.28. I had configured the Grub that it is on the ext. HD. But after updating, the Grub bootloader was on the MBR on the internal HD? Could this have been caused by the new kernel?

If you don't want the external HDD install to treat itself as the second drive of your PC, you have to do this on the external HDD (It is the same thing I do for **Ubuntu-On-A-Stick!** USB installs):

On the external HDD:
```
sudo rm /etc/grub.d/30_os-prober
```

This will make the next command you run from the external HDD booted OS:

```
sudo update-grub
``` only look for OS's on the external HDD drive.

***The Hedge***

:KS

---

### Post by Jonker on 2011-03-10
so it had something to do with the new kernel?

---

