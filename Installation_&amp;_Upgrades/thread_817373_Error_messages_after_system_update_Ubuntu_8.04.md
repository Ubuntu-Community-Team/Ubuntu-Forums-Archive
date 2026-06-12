---
title: "Error messages after system update Ubuntu 8.04"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by zuidema on 2008-06-03
After I do a system update the following errors appear in the message box of update manager.

E: linux-image-2.6.24-17-generic: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

I have looked in Synapic package manager and nothing is broken and no dependency problems are reported. Need help!

---

### Post by Partyboi2 on 2008-06-03
Open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --confiure -a
``` What is the output?

---

### Post by zuidema on 2008-06-04
This is the output  for sudo dpkg --configure -a




root@jgz-desktop:/home/jgz# sudo dpkg --configure -a
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /usr/sbin/update-grub.
grub-probe: error: Cannot get the real path of `/dev/hda'
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic

---

### Post by iaculallad on 2008-06-04
Fire up your terminal:

```
sudo apt-get install util-linux
```

Then redo your system update.

---

### Post by xfran on 2008-06-06
I had the same problem, I just found a solution.

It seems that my boot partition is too small. I gave it 50Mb, but when linux updates the kernel it leaves the old versions files in the boot folder, so there is no space to install the new one.

I just read in another post a guy with the same problem and he solved it moving to other folder the old version files and running then the :

sudo dpkg --configure -a

I tried and it worked for me.
A colleague tried uninstalling in synaptic the old kernel before but it gave him some trouble, as the grub menu was not updated correctly so be careful with this one.

---

