---
title: "No Kernels listed in grub"
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rv65 on 2010-02-09
I have a Dell D610 running Ubuntu 10.04 and there are no kernels listed in Grub other than memtest. I just can't boot into the system unless I use a SuperGrub2 boot disc. My 64 bit desktop has all the kernels listed but not this machine which runs 32 bit. 

I also have issues with hunspell-en-ca and language-writing-support-en dependency issues. Hunspell throws an error while language support has some dependency issue that prevents this from being updated. This only happens on the laptop.

---

### Post by dino99 on 2010-02-10
is this D610 only have 1 distro on it ?
if you miss kernel(s), i think you miss grub to. run grub-mkconfig then update-grub

if nothing happen, run grub-install

---

### Post by rv65 on 2010-02-11
I also have Windows XP. I reinstalled grub and memtest and all is well for now.

---

