---
title: "--configure -a dependency problems"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by blu-ray boyz on 2010-04-12
hi,

   im new to the forums, so if im in the wrong section just let me know. THANKS in advance.  I just finished installing 9.10 and did the updates that came up and now everytime i try to open SYNAPTIC PACKAGE MANAGER, or install more updates from UPDATE MANAGER i get the message telling me to run SUDO DPKG --CONFIGURE -A  When i do that i get the following results from the terminal window. before the updates everything worked fine. any help would be great. thanks again



jay@jay-laptop:~$ sudo dpkg --configure -a
[sudo] password for jay: 
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.31-20-generic (2.6.31-20.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-20-generic
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-20-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.31-20-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-20-generic; however:
  Package linux-image-2.6.31-20-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.20.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.31-14-generic
dpkg: subprocess installed post-installation script returned error exit status 1
jay@jay-laptop:~$

---

### Post by nothingspecial on 2010-04-12
Ouch, that looks nasty.

First, try 

```
sudo apt-get install -f
```

Which will try and correct any dependency issues.

If that doesn`t work, then you might have to try booting in to an earlier kernel, and removing the offending one.

If you have no idea what I`m talking about, I appologise, post back.

---

### Post by blu-ray boyz on 2010-04-12
I tried the 'sudo apt-get install -f' and it told me that it was interrupted and to run the configure -a again. how do I boot to the earlier kernel and remove the bad one? THANKS.

---

### Post by nothingspecial on 2010-04-13
Press shift while booting

---

