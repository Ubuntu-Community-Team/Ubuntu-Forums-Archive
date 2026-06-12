---
title: "nvidia driver fail"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by bugs6 on 2007-12-05
HI

I am trying to run alien arena and i found out that i need to install my graphic drivers so i get to the nvidia installer and it says that i dont have kernel sources or something and that it will make them for me.

It doesnt work and says i need to find the right kernel source or something then tells me to get the dorrect libc files for my kernel, im very confused.

any help would be appreciated!!

thnks

---

### Post by Pumalite on 2007-12-05
Run:
sudo apt-get install linux-headers-`uname -r`
(copy and paste in your Terminal)

---

### Post by bugs6 on 2007-12-09
tht didnt work it didnt find the package

---

### Post by Pumalite on 2007-12-09
It's nor supposed to find any package. It's supposed to let you compile your driver into the kernel.

---

