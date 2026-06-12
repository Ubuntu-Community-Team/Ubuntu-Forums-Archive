---
title: "Windows Messed up my bootloader"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by jimmy20013 on 2006-10-03
I installed Windows XP after installing Ubuntu and now I cant see my grub bootloader. The PC just boots to windows. I am using the Ubuntu Live Cd to boot to Ubuntu and I have managed to mount my hard drive partition containing  Ubuntu. Now what should I do so as to I can see my grub bootloader.


Also Windows sucks.

---

### Post by jimmy20013 on 2006-10-03
I fixed it. I started terminal, sudo grub->root(hd0,0)->setup(hd0) and rebooted.

Ubuntu was on hda1 hence I had to use hd0,0.

---

