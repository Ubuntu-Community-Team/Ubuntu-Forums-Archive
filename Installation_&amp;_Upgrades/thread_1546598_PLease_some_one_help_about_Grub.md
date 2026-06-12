---
title: "PLease some one help about Grub"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by turkler on 2010-08-05
hello i have ubuntu 10.4 32 bit and windows 7 64 bit i am trying to install XPUD on my Hard disk but i cant understand ! i am still a basic user in linux so dont get me wrong 

please tell me step by step to install it in hard disk 

the only thing i know tell now to copy the xpud 0.9.2 image to boot / make folder name (Xpud) but after that nothing to understand 

and sorry for my bad english

thank you all

---

### Post by oldfred on 2010-08-05
the instructions on their site have you just booting the ISO directly. I fyou make a folder /boot/xpud and put ISO there this entry in grub2 will let you boot it. The hd0,0 is if your install is in sda1, you will have to adjust to your drive & partition.

[http://www.xpud.org/download.en.html](http://www.xpud.org/download.en.html)
USB install
[http://www.pendrivelinux.com/usb-xpud-persistent-install-windows/](http://www.pendrivelinux.com/usb-xpud-persistent-install-windows/)

Copy entry below to and edit drive & partition to suit :
gksudo gedit /etc/grub.d/40_custom


menuentry "xPUD 0.9.2" {
loopback loop (hd0,0)/xpud-0.9.2.iso
linux(loop)/boot/xpud isofrom=/xpud-0.9.2.iso noisapnp quiet 
initrd   (loop)/opt/media
}

---

