---
title: "Kernel Panic after upgrade to 23.04 (kernel 6;2 and nvidia related?) - binary not fou"
date: 2023-05-02
forum: Installation &amp; Upgrades
---

### Post by alexcarlosantao on 2023-05-02
Hi, 

 I had a fully functional ubuntu 22.10 installation on my samsung notebook.
 Today I tried to upgrade to 23.04 and I got a Kernel panic after boot. 
  I can boot normally on older kernel selection it on advanced options grub menu (5.19.0-41). When I do that, I open root terminal and try to fix the upgrade process. It starts compiling and gives me an error saying:
    ERROR (dkms apport): binary package for nvidia: 525.60.11 not found

and all else fails to build. 

  I'm trying to disable nvidia module, but I cannot, everytime I try to do something it tries to finishes this process. The kernel it tries to build it is 6.2.0-20. 

Any help, please ?

---

### Post by alexcarlosantao on 2023-05-02
Got to make it work by :

> echo 'nouveau' | sudo tee -a /etc/modules

sudo rm /etc/X11/xorg.conf

reboot

sudo apt install nvidia-driver-530

reboot



---

