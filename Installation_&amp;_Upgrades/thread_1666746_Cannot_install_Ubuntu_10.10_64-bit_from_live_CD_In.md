---
title: "Cannot install Ubuntu 10.10 64-bit from live CD: Input/output error"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by etienne@Rofti on 2011-01-14
Hi there!

I have recently bought an HP Compaq 615 dual-core laptop. I bought it second-hand (although it is as good as new and was only used for a couple of months) and it came with Windows 7 Home Basic, which I promptly decided to replace with Ubuntu 10.10.

However, I cannot seem to install or run the 64-bit version of Ubuntu, while the 32-bit version works perfectly! I get the following error message if I click "Try Ubuntu" from the live CD screen, or if I click "Install Ubuntu":

> /etc/rc2.d/S99grub-common: 40: grub-editenv: Input/output error

I have no idea what this means or how to fix it. Google has not helped me yet. Please, if anyone knows what I'm doing wrong, please let me know!

Thanks so much.

Etienne

---

### Post by dino99 on 2011-01-14
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/439784)

workaround in post #2

often on ext4+64 bits, less on ext3, might check on your install

---

### Post by etienne@Rofti on 2011-01-14
Thanks, dino99 ...

After a suggestion by someone else, I installed using the "alternate" CD image instead of the live CD. It worked fine!

I couldn't test your solution, since I was busy installing by the time you replied. Thanks for your help anyway!

E

---

