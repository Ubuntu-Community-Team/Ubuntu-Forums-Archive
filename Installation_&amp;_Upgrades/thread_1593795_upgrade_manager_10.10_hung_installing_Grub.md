---
title: "upgrade manager 10.10 hung installing Grub"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by bswanboat on 2010-10-11
I used the upgrade manager to update to Ubuntu 10.10. It hung on installing grub. After trying the repairs, the system says it can't find grub_xputs and gives the grub rescue> prompt. 

What is the solution?

---

### Post by JigglyWiggly_ on 2010-10-11
Same prob... so much fail.

---

### Post by wilee-nilee on 2010-10-11
Grub2 read carefully it defaults to the install from a live cd. 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by bswanboat on 2010-10-12
Thanks for the link. I have just finished following the steps in this link: [http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099"). I now have a menu to select from for the different kernels and my Windows installation. But when I boot into Ubuntu, all I get is the command prompt.

Getting there but not there yet.

---

### Post by bswanboat on 2010-10-12
It looks like the issue is with the driver for the Nvidia GeForce2 MX/MX 400 graphics card. The driver will not install.

---

### Post by wilee-nilee on 2010-10-12
> **bswanboat said:**
> It looks like the issue is with the driver for the Nvidia GeForce2 MX/MX 400 graphics card. The driver will not install.

Are you able to get into Ubuntu with edit of the kernel. Hold down the shift to get the grub menu if its not there automatically, hit e the use the arrows to set nomodeset in between the ro and no splash, boot from there with ctrl-x. This is a per-session option.

---

