---
title: "All kernels deleted."
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by yoda29 on 2007-09-06
Hello,

I've accidently deleted all kernels and now the GRUB don't show any entry for kubuntu (as expected).
How do I install a kernel? By the LiveCD? How can I do that?

Best regards

---

### Post by maybeway36 on 2007-09-06
Can you use the install CD to boot into your hard drive system with a root shell?

---

### Post by yoda29 on 2007-09-06
Yes, I can use the LiveCD, but i don't now what to do after...

---

### Post by merlinus on 2007-09-06
You might try manually mounting your partition, and then using Synaptic to search for -16.

Install linux-headers 2.6.20-16, linux-headers 2.6.20-16-generic, linux-image and linux-restricted-modules (same numbers).

-merlin

---

### Post by yoda29 on 2007-09-11
How do I do that. I have Kubuntu Gutsy and the Livecd of Feisty. How can I, from the Livecd install a kernel to boot into Kubuntu again. I've lost all the kernel entries, as I've deleted all the kernels.

Best regards

---

### Post by yoda29 on 2007-09-14
Anyone?????

---

### Post by dabl on 2007-09-14
> **yoda29 said:**
> How do I do that. I have Kubuntu Gutsy and the Livecd of Feisty. How can I, from the Livecd install a kernel to boot into Kubuntu again. I've lost all the kernel entries, as I've deleted all the kernels.


Mmmmmmmmmm .... that's a bit of mess!  :(

All I can think of, if you know which partition your Feisty was on, and if you know which /boot/grub/menu.lst was the operational boot menu, you could copy the linux kernel from the Feisty Live CD to the appropriate Feisty /boot folder, then make sure that the menu.lst file is pointing to it correctly (and the versions match), and then when you boot that will be the only menu selection that actually works.  Maybe.  [-o<

---

### Post by yoda29 on 2007-09-14
And update with Gutsy LiveCD???? Will it work?

---

