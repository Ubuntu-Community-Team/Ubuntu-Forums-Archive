---
title: "How to install and use an older GCC version for armhf?"
date: 2024-04-18
forum: Installation &amp; Upgrades
---

### Post by parduz on 2024-04-18
I'm running an Ubuntu 22.04.3 LTS image in WSL, as i need to cross-compile a program for an ARM linux pc.

I've been able to install the arm architecture, the arm gcc and compile. Problem is that GCC is version 11 and the glibc is too new for the ARM linux.
So i need to downgrade to GCC10.

I've tried to follow this guide: [https://tech.sadaalomma.com/ubuntu/how-to-downgrade-gcc-version-in-ubuntu/](https://tech.sadaalomma.com/ubuntu/how-to-downgrade-gcc-version-in-ubuntu/) so i've removed both **gcc **and **arm-linux-gnueabihf-gcc** and then I've [FONT=courier new]*sudo apt install **gcc-10-arm-linux-gnueabihf** *[/FONT]and it installed
Is it the right one? 
I'm unable to call it .. what's the command, or the path, to check its version like gcc -v?.
Should i install something like binutils-arm-linux-gnueabihf but for GCC10? how?

Could someone guide me?

---

