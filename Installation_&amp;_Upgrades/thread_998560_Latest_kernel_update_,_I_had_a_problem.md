---
title: "Latest kernel update , I had a problem"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by bowens44 on 2008-11-30
After updating to 2.6.24-22 I believe my nvidia drivers weren't being recognized. I assume that something went wrong with the update. When booting I was told that ubunutu was running in low resolution.

I booted to my previous kernel and all is well. 

What I would like to do is completely remove the latest kernel and try the upgrade again. If I attempt to remove it in synaptic, will linux-restricted-modules-generic and linux-image-generic be updated to show that I am back to the previous kernel?

What is the best way to get my system back to where it was before the upgrade attempt. I am back to my previous menu.lst file in /boot/grub.

When  try this again I want to be sure to get all needed files. 

thanks

---

### Post by lemming465 on 2008-12-02
Let me guess - older Nvidia video chip and Ubuntu 8.10?  If not, write back with the Ubuntu version (cat /etc/lsb-release), contents of /etc/X11/xorg.conf, results of *sudo lspci*, and contents of /var/log/Xorg.0.log.

Ubuntu 8.10 uses Xorg 1.5, and the binary Nvidia drivers hadn't been ported to that when it was released.  The latest 2.6.27-9 kernel, Xorg 1.5.2, and Nvidia binary drivers are doing OK together.  If you have an Nvidia chip and need an interim solution, switch to **driver "nv"** in /etc/X11/xorg.conf temporarily.

---

